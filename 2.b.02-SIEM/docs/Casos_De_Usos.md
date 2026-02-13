# Documentación de caso de uso
Detección de **fuerza bruta SSH** e **ICMP** (Snort → Filebeat → ELK)

> Plantilla basada en el ejemplo/plantillas del PDF "CasosDeUsos.pdf" (apartado de plantillas de caso de uso: objetivo, alcance, fuentes de eventos, tipo de datos, flujo lógico, notificación, severidad, recomendación).

---

## Control de cambios

| Fecha | Actualización | Realizado por | Autorizado por | Naturaleza del cambio |
|---|---|---|---|---|
| 13/02/2026 | Creación del caso de uso | David Jimenez Ruiz | Profesorado | Documento nuevo |

---

## Contenido
1. OBJETIVO  
2. ALCANCE  
3. FUENTES DE EVENTOS  
4. TIPO DE DATOS  
5. FLUJO LÓGICO  
6. NOTIFICACIÓN  
7. SEVERIDAD  
8. RECOMENDACIÓN  

---

## 1. OBJETIVO

Detectar actividad sospechosa relacionada con:

- **Fuerza bruta SSH** contra el servicio SSH (TCP/22), identificando intentos repetidos (múltiples eventos en una ventana temporal) para generar una alerta accionable.
- **ICMP** (ping/eco) como prueba rápida de visibilidad del IDS y como indicador de posibles escaneos/sondeo (según umbral).

---

## 2. ALCANCE

Este caso de uso aplica sobre el entorno de laboratorio desplegado con ELK + agente e IDS (Snort), con el siguiente alcance:

- **Servicios/Tráfico monitorizado:**
  - Tráfico TCP hacia puerto **22/SSH** del endpoint monitorizado.
  - Tráfico **ICMP** hacia el endpoint (para verificación y, opcionalmente, detección de escaneo/volumen).

- **Se considera detección** (genera alerta):
  - Múltiples intentos SSH desde una misma IP origen en un intervalo corto (indicador típico de fuerza bruta).
  - ICMP repetitivo por encima de un umbral (opcional; en el laboratorio también se usó como test de "Snort ve tráfico").

- **No se considera** (reduce falsos positivos):
  - Intentos SSH aislados (1–2 fallos puntuales).
  - Pings puntuales de comprobación (1–2 paquetes).

---

## 3. FUENTES DE EVENTOS

- **Snort 2.9.20 (IDS)** ejecutándose en el endpoint/agente, generando alertas en fichero `fast` hacia `/var/log/snort/alert`.  
- **Filebeat** como recolector, leyendo `/var/log/snort/alert` (y logs de Nginx si aplica) y enviando eventos a Logstash (Beats input 5044) para su indexación en Elasticsearch y visualización en Kibana.

---

## 4. TIPO DE DATOS

Para implementar el caso de uso se requiere analizar los siguientes datos:

| Plataforma | Tipo de log | Ruta / índice esperado | Contenido relevante |
|---|---|---|---|
| Snort | Alertas IDS (formato fast) | `/var/log/snort/alert` | Timestamp, firma/mensaje, IP origen/destino, proto, puertos. |
| ELK (Kibana/Elasticsearch) | Eventos indexados desde Filebeat | `filebeat-*` | `@timestamp`, `message` (alerta Snort), campos enriquecidos si se parsean. |

**Campos de interés (mínimos en PoC):**
- `@timestamp`
- `message` (incluye la alerta "fast" de Snort)
- `src_ip` / `dst_ip` (si se extraen; si no, se consulta por texto)
- `dest_port` (22 en caso SSH).

---

## 5. FLUJO LÓGICO

### 5.1 Flujo de generación y envío

1. Se genera tráfico (ICMP/SSH) desde un host atacante (p. ej. Kali).  
2. Snort inspecciona el tráfico y, si coincide con las reglas (`local.rules`), escribe alertas en `/var/log/snort/alert` (modo fast).  
3. Filebeat lee el fichero de alertas y envía eventos a Logstash (5044).  
4. Logstash reenvía a Elasticsearch, quedando disponible en Kibana (Discover/visualizaciones).

### 5.2 Condición de detección (PoC)

- **SSH fuerza bruta (correlación/umbral):**  
  - Se dispara alerta cuando, para una misma IP origen, se detectan múltiples eventos de "Acceso SSH / SSH attempt" en un intervalo corto (el umbral exacto se ajusta al laboratorio; típicamente ≥ 5 en 5 minutos).

- **ICMP (verificación + posible umbral):**  
  - Se dispara alerta cuando se detecta tráfico ICMP hacia el endpoint (para corroboración de captura); opcionalmente, se eleva a alerta "escaneo/volumen" si supera un umbral de paquetes/tiempo.

### 5.3 Problemas encontrados y ajuste aplicado (importante)

Durante las pruebas del ataque SSH (Hydra), se observó que la **regla inicial** solo detectaba si el tráfico cumplía `flow:established`.  

Para poder **corroborar intentos** y no depender únicamente de sesiones ya establecidas, se modificó la regla (relajando/eliminando la condición estricta) y se ajustó la ejecución de Snort para registrar correctamente en fichero.

**Ejecución final de Snort (definitiva en la PoC):**
```bash
snort -A fast -q -c /etc/snort/snort.conf -i eth0 -k none -l /var/log/snort
```

- Se adoptó salida `fast` a fichero para integrarlo con Filebeat.
- Se usó `-k none` como workaround de laboratorio para evitar problemas de checksum en entornos virtualizados y asegurar visibilidad del tráfico.

---

## 6. NOTIFICACIÓN

En el laboratorio, la notificación se gestionó mediante visualización en Kibana (Discover y paneles).

En un escenario real, este caso de uso debería notificar al equipo SOC vía correo, ticketing o webhook, siguiendo un formato estándar (fecha/hora, IP origen, IP destino, tipo de alerta, umbral, enlace a Kibana).

---

## 7. SEVERIDAD

Propuesta de severidad (adaptable al entorno y a si el origen es interno/externo):

| Alerta / Reporte | Severidad |
|---|---|
| Fuerza bruta SSH (múltiples intentos desde misma IP) | Alta |
| ICMP repetitivo por encima de umbral (posible escaneo) | Media |
| ICMP puntual (solo verificación) | Baja |

Ajustar severidad según contexto (red interna, host crítico, horario, reincidencia).

---

## 8. RECOMENDACIÓN

Medidas de mitigación y hardening asociadas al caso de uso:

- **Endurecimiento de SSH:** deshabilitar login por contraseña si es posible, forzar claves, restringir por IP/VPN, y aplicar políticas de contraseñas robustas.

- **Bloqueo automático:** implementar controles tipo rate-limit / firewall (iptables/nftables) o herramientas como fail2ban para bloquear IPs tras superar umbrales.

- **Afinamiento continuo:** revisar falsos positivos, ajustar umbrales y mantener un histórico de alertas para mejorar la correlación y el contexto.

- **Operación del IDS:** mantener reglas y Snort actualizados; documentar claramente parámetros de ejecución en producción (evitar `-k none` salvo necesidad justificada).


# Caso 2: Verificación tuit Khyber - Write-up OSINT

## Introducción y descripción del caso

El 19 de enero de 2023, un periodista con casi 140.000 seguidores en Twitter publicó una foto de un vehículo destruido en llamas con el texto:

**"ÚLTIMA HORA: TTP llevó a cabo un ataque suicida en un puesto policial en la ciudad de Khyber, en Pakistán, en el que murieron tres agentes de policía paquistaníes".**

La tarea era **verificar si la foto corresponde realmente al ataque citado** o si está reutilizada de otro incidente. Este es un ejercicio de detección de desinformación visual.

---

## Metodología empleada

**Proceso OSINT aplicado**:
1. Captura de la foto del tuit
2. Búsqueda inversa (TinEye) → rastrear origen
3. Análisis contexto Wikipedia → identificar incidente real
4. Verificación Google → confirmar ataque Khyber existe
5. Comparación: foto ≠ ataque citado

**Herramientas principales**: TinEye (búsqueda inversa), Wikipedia (contexto histórico), Google Search (confirmación).

---

## Resultados obtenidos

### Búsqueda inversa (TinEye)
Subimos la foto a TinEye. El resultado apuntaba a un artículo de Wikipedia sobre **"Al-Qaeda in Iraq"** en una sección de **"Atentados con coches bomba"** durante la ocupación de Irak (2003-2008).

**Hallazgo**: La foto es de un ataque antiguo en Irak, no de Pakistán 2023.

### Verificación ataque Khyber
Confirmamos con Google que el ataque de Khyber del 19/01/2023 **sí ocurrió**:
- Lugar: Sarband police station, Khyber, Pakistán
- Muertos: 3 policías
- Responsables: TTP (Tehrik-i-Taliban Pakistan)

### Conclusión verificación
**Desinformación confirmada**: El ataque fue real, pero la foto es falsa (reutilizada de Irak).

---

## Tabla con respuestas

| Pregunta | Respuesta |
|----------|-----------|
| **a) Verifica la declaración** | **FALSA**: La foto NO corresponde a Khyber 19/01/2023. Es de ataques históricos en Irak (2005-2008). El ataque de Khyber sí ocurrió, pero con foto incorrecta. |

---

## Conclusiones y recomendaciones

**Conclusión**: Caso de desinformación visual. El evento es real pero la foto es de otro lugar/fecha. Es una táctica común en redes sociales.

**Recomendación principal**: TinEye es crítica para verificar origen de imágenes. Nunca confiar solo en apariencia visual de foto.

**Por qué es peligroso**: 
- La gente asume foto = prueba del evento
- Se propaga rápido en redes sin verificación
- Alimenta narrativas falsas

---

## Reflexión sobre limitaciones y mejoras

**Limitaciones encontradas**:
- Una foto que parece "real" (vehículo destruido, fuego) puede provenir de cualquier lugar
- Necesidad de herramientas especializadas (TinEye) para rastrear origen
- Requiere verificación cruzada (Wikipedia + Google) para estar seguro

**Mejoras para futuras investigaciones**:
- Usar TinEye como PRIMERA herramienta en verificación de fotos (antes que análisis visual)
- Consultar fact-checkers especializados (SOCH, Reuters Fact Check) para casos de desinformación
- Mantener base datos de fotos reutilizadas frecuentes
- Crear alertas automáticas para detectar imágenes reutilizadas en contextos falsos

**Lección clave**: En verificación de desinformación, las imágenes son el arma más poderosa pero también la más falsifiable.
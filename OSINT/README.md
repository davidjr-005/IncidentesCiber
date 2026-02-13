# IncidentesCiber
Repositorio Individual para la asignatura Incidentes en Ciberseguridad
# Actividad 2.d.01 – Prueba de OSINT (Toma de contacto)

## Descripción general

Esta actividad consiste en aplicar técnicas de **Open Source Intelligence (OSINT)** para investigar y resolver **cuatro casos prácticos** proporcionados en un archivo adjunto.  
El objetivo es seguir todo el **ciclo OSINT** (planificación → recolección → procesamiento → análisis → difusión) y dejar constancia del proceso y de los resultados en un informe final (write‑up) y en este repositorio.

---

## Objetivos de la actividad

- Aplicar el **proceso teórico de OSINT** en situaciones reales.
- Utilizar de forma eficaz diferentes **herramientas OSINT** para recopilar y analizar información.
- Desarrollar **habilidades de documentación y presentación** de investigaciones OSINT.

---

## Trabajo a realizar

### 1. Análisis de los casos

Para cada uno de los cuatro supuestos del PDF:

- Leer con detalle el enunciado.
- Identificar claramente **qué se está preguntando** (preguntas a, b, c…).
- Acotar el **alcance de la investigación** (tipo de dato: imagen, vídeo, geolocalización, verificación de noticia, etc.).

### 2. Planificación del proceso OSINT

Para cada caso, definir una mini‑estrategia que incluya:

- **Fuentes de información relevantes**  
  - Buscadores generales (Google, Bing).  
  - Plataformas específicas (Twitter, Instagram, Wikipedia, medios locales, etc.).  
  - Mapas/Street View, archivos web (Wayback), bases de datos especializadas.

- **Herramientas OSINT adecuadas**  
  - Búsqueda inversa de imágenes (Google Images, TinEye, Yandex).  
  - Google Dorks (operadores `site:`, `filetype:`, `after:`/`before:`…).  
  - Herramientas avanzadas (Maltego, Shodan, SpiderFoot, theHarvester, FOCA) si aportan valor en el caso.

- **Ejecución de la investigación**  
  - Qué pasos se van a seguir primero, qué se hará si un camino no da resultados, y cómo se va a validar la información encontrada (cruce de fuentes).

### 3. Documentación del proceso

En cada carpeta de caso (`/Caso1`, `/Caso2`…) se documentará:

- **Herramientas y fuentes utilizadas**  
  - Qué herramientas se usaron y para qué (ej. TinEye para localizar origen de la foto, Google Maps para Street View, etc.).  

- **Datos recopilados**  
  - URLs relevantes, fechas, nombres, coordenadas, capturas de pantalla, etc.  

- **Análisis realizado**  
  - Cómo se interpretan esos datos, cómo se descartan pistas falsas, cómo se llega a la respuesta final.  

- **Dificultades encontradas y cómo se superaron**  
  - Ejemplos: una herramienta no devuelve resultados, una imagen engaña por la perspectiva, fechas contradictorias, etc., y qué se hizo para resolverlo.

---

## Informe final (write‑up)

Además de la documentación técnica por caso, se entregará un **write‑up resumido** (por ejemplo en `IS-2.d.01-[INICIALES].md` o PDF) que incluya para cada caso:

- **Introducción y descripción del caso**  
  - Resumen breve del enunciado y objetivo (una o dos frases).

- **Metodología empleada**  
  - Qué enfoque OSINT se ha seguido (búsqueda inversa, geoloc, verificación de noticia…).

- **Resultados obtenidos**  
  - Respuestas claras a las preguntas del caso (lugar/fecha, nombre edificio, coordenadas, etc.).

- **Conclusiones y recomendaciones**  
  - Qué se ha aprendido en ese caso y qué recomendarías hacer en investigaciones similares.

- **Reflexión sobre limitaciones y posibles mejoras**  
  - Limitaciones de las herramientas/fuentes, falta de metadatos, cambios con el tiempo (Street View antiguo, webs borradas), etc.  
  - Propuestas de mejora: otras herramientas, automatización, más fuentes, etc.

- **Tabla con respuestas** (obligatoria por enunciado)  
  - Para cada ejercicio:  
    - Columna izquierda: **Pregunta**  
    - Columna derecha: **Respuesta final**  
  - Ejemplo:

    | Pregunta | Respuesta |
    |----------|-----------|
    | a) Lugar y fecha de nacimiento | Virginia Zoo, Norfolk (EE.UU.), 21/10/2009 21:15 |
    | b) Residencia actual | Disney’s Animal Kingdom, Florida, llegada 12/10/2010 |

---

## Recursos recomendados

### Material teórico OSINT
- Apuntes y lecturas de clase sobre fases OSINT: **planificación, recolección, procesamiento, análisis y difusión**.

### Herramientas OSINT (mencionadas en la actividad)

- **Maltego**: análisis de enlaces y minería de datos (personas, dominios, IPs, etc.).  
- **Shodan**: buscador de dispositivos y servicios expuestos en Internet.  
- **Google Dorks**: búsquedas avanzadas con operadores (`site:`, `filetype:`, `inurl:`, etc.).  
- **SpiderFoot**: reconocimiento automatizado (IPs, dominios, correos, dark web…).  
- **theHarvester**: recolección de correos, nombres, subdominios, IPs de fuentes públicas.  
- **FOCA**: análisis de metadatos en documentos (PDF, DOCX, etc.).

### Formación adicional (vídeos)

- OpenWebinars – **Herramientas avanzadas OSINT**  
- OpenWebinars – **OSINT y fuga de datos empresariales**  

---

## Estructura sugerida del repositorio

```text
2d.OSINT/
├── README.md                # Este archivo: descripción global actividad
├── IS-2.d.01-[INICIALES].pdf  # Write-up final en PDF
├── Caso1/
│   ├── Documentacion_caso1.md
│   ├── Writeup_caso1.md
│   └── img/
├── Caso2/
│   ├── Documentacion_caso2.md
│   ├── Writeup_caso2.md
│   └── img/
├── Caso3/
│   ├── Documentacion_caso3.md
│   ├── Writeup_caso3.md
│   └── img/
└── Caso4/
    ├── Documentacion_caso4.md
    ├── Writeup_caso4.md
    └── img/
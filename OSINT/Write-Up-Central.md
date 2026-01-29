# Caso 1: Jirafa recién nacida - Write-up OSINT

## Introducción y descripción del caso
Foto de cría jirafa reticulada (especie en peligro) participando en programa conservación.  
**Objetivos**: 
- a) Lugar y fecha de nacimiento
- b) Residencia actual y fecha de llegada  
- c) Fotografía en hábitat actual

## Metodología empleada
**Ciclo OSINT**: Planificación → Recolección (TinEye/Dorks) → Procesamiento → Análisis → Tabla.  
**Herramientas principales**: TinEye, Google Dorks fecha/site, ZooBorns, ZooChat.

## Resultados obtenidos
1. **TinEye**: Imagen indexada 2009 → Virginia Zoo pista
2. **ZooBorns**: Confirmado nacimiento **21/10/2009 21:15**, Norfolk VA
3. **ZooChat**: Identificada **Willow** (naming poll), traslado Disney AK **12/10/2010**
4. **Verificación**: Fotos actuales savana Disney's Animal Kingdom

## Tabla con respuestas
| Pregunta | Respuesta |
|----------|-----------|
| **a)** Lugar y fecha de nacimiento | **Virginia Zoo, Norfolk VA, 21/10/2009 21:15** |
| **b)** Residencia actual y fecha de llegada | **Disney's Animal Kingdom (Florida), 12/10/2010** |
| **c)** Fotografía hábitat actual | ![Willow](img/jirafa6.png) |

## Conclusiones y recomendaciones
**Conclusión**: Caso resuelto completamente. Willow participa en programa SSP reticuladas.  
**Recomendación**: Siempre TinEye primero + Dorks fecha para imágenes antiguas.  
**Limitaciones**: Dependencia archivos web 2009 → usar Wayback Machine preventivo.  
**Mejora futura**: SpiderFoot automatizar recolección foros+blogs zoos.

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

# Caso 3: Estación Flinders Street Melbourne - Write-up OSINT

## Introducción y descripción del caso

La tarea fue identificar una estación de tren compartida en redes sociales. Necesitábamos responder dos preguntas:
- a) ¿Cómo se llama la estación?
- b) ¿Cuál es el nombre y altura de la estructura más alta visible?

Se trata de un ejercicio típico de geolocalización OSINT donde la foto proporciona pistas visuales clave (letrero visible, arquitectura, contexto).

---

## Metodología empleada

**Proceso OSINT aplicado**:
1. Análisis visual → búsqueda texto visible
2. Identificación ubicación → verificación Street View
3. Geolocalización edificios → identificación por carteles
4. Confirmación datos → fuentes especializadas

**Herramientas**: Google Maps (satelital + Street View), Google Search, Brave Search, The Skyscraper Center.

---

## Resultados obtenidos

### Identificación de la estación
El letrero visible "FLINDERS STREET" fue inmediatamente buscable en Google. Resultado: **Flinders Street Railway Station, Melbourne, Victoria, Australia** (estación más concurrida de Australia, inaugurada 1854).

Street View confirmó 100% de coincidencia visual con la foto original.

### Identificación del edificio más alto
**Error inicial**: Pensamos que era IBM Building (~75m) porque se veía más grande. Error de perspectiva.

**Corrección**: Navegamos Street View a nivel calle, encontramos cartel "FOCUS APARTMENTS - BRAND NEW FOR SALE". Ese era el edificio.

**Altura confirmada**: 167 metros (50 pisos), ubicado en 81 City Road, Southbank.

---

## Tabla con respuestas

| Pregunta | Respuesta |
|----------|-----------|
| **a) Nombre estación** | Flinders Street Station (Melbourne, Victoria, Australia) |
| **b) Nombre + altura edificio** | FOCUS Apartments by Central Equity, 167 metros (50 pisos) |

---

## Conclusiones y recomendaciones

**Conclusión**: Caso resuelto exitosamente con 2 fuentes cruzadas (Google Search + The Skyscraper Center).

**Recomendación principal**: Nunca confiar solo en perspectiva visual. Street View a nivel calle es más fiable que satelital para leer nombres y confirmar edificios.

---

## Reflexión sobre limitaciones y mejoras

**Limitaciones encontradas**:
- TinEye no funciona si la foto no está indexada (requiere cambio rápido de herramienta)
- Perspectiva fotográfica distorsiona percepción de altura
- Vista satelital muestra forma pero no nombres

**Mejoras para futuras investigaciones**:
- Usar siempre múltiples ángulos Street View antes de confirmar edificio
- Consultar herramientas 3D (Google Earth 3D) para validar perspectiva
- Crear checklist: letrero → ubicación → altura → fuente oficial

# Caso 4: Vídeo Visit Tirana - Write-up OSINT

## Introducción y descripción del caso

El 16 de febrero de 2023, la cuenta de Twitter **@VisitTirana** publicó un vídeo de una persona caminando por una calle de Tirana con el caption **"Sunset in Tirana"**.

La tarea era:
- a) ¿A qué hora se grabó el vídeo?
- b) ¿Cuáles son las coordenadas exactas de dónde caminaba la persona?

Este es un ejercicio avanzado de **geolocalización + cronolocalización** (ubicación + tiempo).

---

## Metodología empleada

**Proceso OSINT aplicado**:
1. Análisis del tuit original (fecha, hora publicación, caption)
2. Rastreo del fotógrafo original → Instagram
3. Extracción hora exacta de publicación Instagram
4. Análisis visual del vídeo (características únicas de calle)
5. Identificación calle en Google Earth
6. Localización edificios distintivos
7. Validación con Street View
8. Determinación coordenadas exactas

**Herramientas principales**: Twitter, Instagram, Google Earth Pro (3D buildings), Google Street View, SunCalc (validación hora).

---

## Resultados obtenidos

### Hora de grabación

El tuit de @VisitTirana fue publicado a las **23:07 (11:07 PM)**, pero eso es horas después de grabar.

El descubrimiento clave fue encontrar al **fotógrafo original (Eriseld Myrto)** en Instagram. Su perfil mostró que publicó el mismo vídeo a las **4:48 PM (16:48)** del 16 de febrero de 2023.

**Conclusión**: El vídeo se grabó aproximadamente a las **4:45 PM**, pocos minutos antes de publicar en Instagram.

### Geolocalización exacta

Analizando características visuales del vídeo (carril bici en el medio, arbustos verdes, árboles sin hojas, edificios), identificamos la calle como **Kavaja Street** en Tirana.

Localizamos el **edificio distintivo** visible en el vídeo usando Google Earth 3D Buildings. Confirmamos con Street View frame por frame.

**Coordenadas identificadas**:
- **Inicio del vídeo**: 41°19'37.24"N, 19°48'27.01"E
- **Fin del vídeo**: 41°19'36.29"N, 19°48'23.89"E

---

## Tabla con respuestas

| Pregunta | Respuesta |
|----------|-----------|
| **a) ¿A qué hora se grabó?** | **Aproximadamente 4:45 PM (14:45), 16 de febrero de 2023** |
| **b) Coordenadas inicio vídeo** | **41°19'37.24"N, 19°48'27.01"E** |
| **c) Coordenadas fin vídeo** | **41°19'36.29"N, 19°48'23.89"E** |

---

## Conclusiones y recomendaciones

**Conclusión**: Caso resuelto completamente. Vídeo grabado en Kavaja Street, Tirana, a las 4:45 PM, con coordenadas precisas confirmadas por Street View.

**Recomendación principal**: Rastrear al creador original (fotógrafo) en redes sociales. Frecuentemente proporcionan metadatos de hora exacta que no están disponibles en retweets.

**Por qué funciona**:
- Instagram preserva hora exacta de publicación
- Google Earth Pro permite identificar edificios únicos
- Street View valida frame por frame
- Combinación = coordenadas altamente precisas

---

## Reflexión sobre limitaciones y mejoras

**Limitaciones encontradas**:
- Street View de 2016 vs vídeo de 2023 (7 años de diferencia): cambios visuales menores
- Necesidad de localizar fotógrafo original (requiere búsqueda adicional)
- Precisión GPS limitada a ±5 metros sin acceso a metadatos EXIF

**Mejoras para futuras investigaciones**:
- Usar **EXIF metadata** si el vídeo está disponible en formato original (proporciona coordenadas exactas)
- Crear base datos de características visuales únicas por calle (carril bici, arbustos, diseño)
- Usar **SunCalc** simultáneamente para validar hora por posición de sombras
- Consultar **Google Earth Pro** con vista 3D Buildings antes de Street View
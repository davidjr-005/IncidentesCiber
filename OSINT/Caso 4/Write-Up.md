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
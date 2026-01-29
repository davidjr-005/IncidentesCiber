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

**Lección clave**: En OSINT geolocalización, los datos duros (números, fuentes oficiales) siempre ganan a la intuición visual.
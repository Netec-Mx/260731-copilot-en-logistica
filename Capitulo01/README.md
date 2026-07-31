---LAB_START---
LAB_ID: 01-00-01
---MARKDOWN---
# Práctica 1 — Diagnóstico de Datos Operativos y Validación de Información

## 1. Metadatos

| Campo | Detalle |
|---|---|
| **Duración estimada** | 60 minutos |
| **Complejidad** | Fácil |
| **Nivel Bloom** | Aplicar (*Apply*) |
| **Módulo** | Módulo 1 — Diagnóstico Operativo con Copilot |
| **Lección base** | 1.1 — Validación de Resultados y Prompts para Análisis Operativo |
| **Herramientas principales** | Microsoft Excel con Copilot, Microsoft OneDrive |

---

## 2. Descripción General

En esta práctica aplicarás directamente los principios de prompt engineering y validación de resultados aprendidos en la Lección 1.1 sobre un dataset logístico simulado. Trabajarás con Microsoft Copilot integrado en Excel para ejecutar un diagnóstico de tres fases: exploración inicial del dataset, detección de inconsistencias de calidad de datos y construcción de una lista priorizada de acciones operativas del día. Al finalizar, habrás construido una metodología personal de análisis asistido por IA que podrás replicar en tu operación real, aplicando el ciclo **prompt → resultado → validación → refinamiento** como práctica central de trabajo.

---

## 3. Objetivos de Aprendizaje

Al completar esta práctica, serás capaz de:

- [ ] Aplicar la estructura de cuatro elementos (Rol + Tarea + Datos + Formato) para formular prompts efectivos en Copilot para Excel sobre un dataset logístico real.
- [ ] Validar los resultados generados por Copilot utilizando los cinco criterios técnicos de verificación: exactitud numérica, coherencia lógica, completitud, relevancia contextual y trazabilidad.
- [ ] Identificar al menos tres tipos de inconsistencias en un dataset logístico (valores nulos críticos, fechas inválidas, registros duplicados) mediante prompts iterativos.
- [ ] Construir una lista priorizada de acciones operativas del día basada en los hallazgos del diagnóstico, asistida por Copilot.
- [ ] Diseñar una secuencia de cinco prompts iterativos que mejoren progresivamente la precisión del análisis operativo.

---

## 4. Prerrequisitos

### Conocimientos previos

| Área | Nivel requerido |
|---|---|
| Navegación en Microsoft Excel | Básico (filtros, ordenamiento, fórmulas simples como `COUNTIF`, `AVERAGE`) |
| Terminología logística | Básico (pedidos, SKU, tiempo de entrega, inventario, SLA, incumplimiento) |
| Uso general de Microsoft 365 | Básico (abrir archivos desde OneDrive, guardar, compartir) |
| Interacción con asistentes de IA | No requerido (se introduce en esta práctica) |

### Acceso y licencias requeridas

| Recurso | Estado requerido |
|---|---|
| Cuenta corporativa Microsoft 365 | ✅ Activa y con sesión iniciada |
| Licencia Microsoft 365 Copilot | ✅ Asignada y activa (no Copilot Free) |
| Microsoft Excel con Copilot habilitado | ✅ Visible en la cinta de opciones (*ribbon*) |
| Microsoft OneDrive para la Empresa | ✅ Sincronizado y accesible |
| Archivo `Dataset_Logistico_Practica1.xlsx` | ✅ Descargado y guardado en OneDrive (provisto por el instructor) |

> ⚠️ **IMPORTANTE:** Si el ícono de Copilot no aparece en la cinta de Excel, consulta la sección de **Solución de Problemas** antes de continuar. Sin licencia activa de Microsoft 365 Copilot, ningún paso de esta práctica puede ejecutarse.

---

## 5. Entorno de Laboratorio

### Hardware recomendado

| Componente | Mínimo | Recomendado |
|---|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| Memoria RAM | 8 GB | 16 GB |
| Almacenamiento libre | 10 GB | 20 GB |
| Resolución de pantalla | 1366 × 768 | 1920 × 1080 |
| Conexión a Internet | 10 Mbps bajada | 25 Mbps bajada |

### Software requerido

| Aplicación | Versión mínima | Verificación |
|---|---|---|
| Microsoft Excel | 365 Apps, versión 2308 o posterior | `Archivo > Cuenta > Acerca de Excel` |
| Microsoft OneDrive | Versión actual (canal mensual) | Ícono en bandeja del sistema |
| Microsoft Edge | Versión 115 o posterior | `edge://settings/help` |
| Copilot en Excel | Habilitado con licencia M365 Copilot | Botón Copilot visible en cinta `Inicio` |

### Configuración inicial del entorno

Antes de comenzar los pasos del laboratorio, ejecuta la siguiente verificación rápida:

**Paso A — Verificar la versión de Excel:**
```
Archivo → Cuenta → Acerca de Excel
Confirmar que la versión sea 2308 o posterior.
```

**Paso B — Verificar que Copilot está habilitado en Excel:**
```
1. Abre Excel.
2. En la cinta de opciones (ribbon), pestaña "Inicio", busca el botón "Copilot" 
   con el ícono de IA (círculo con colores).
3. Si no aparece: Archivo → Opciones → General → 
   verificar que "Mostrar características de Copilot" esté habilitado.
```

**Paso C — Cargar el archivo de práctica desde OneDrive:**
```
1. Abre el navegador Microsoft Edge.
2. Navega a: https://onedrive.live.com (o portal corporativo de OneDrive).
3. Localiza el archivo: Dataset_Logistico_Practica1.xlsx
   (proporcionado por el instructor en la carpeta compartida del curso).
4. Haz clic en "Abrir en la aplicación de escritorio" para abrirlo en Excel.
5. Confirma que el archivo se abre en modo "Edición" (no en modo protegido).
```

> 📝 **Nota:** Copilot en Excel funciona **únicamente** cuando el archivo está guardado en OneDrive o SharePoint. Un archivo guardado solo en disco local no activará las funciones de Copilot. Si ves el mensaje *"Guarda en OneDrive para usar Copilot"*, sigue las instrucciones del Paso C.

**Paso D — Convertir los datos en Tabla de Excel (requisito para Copilot):**
```
1. Con el archivo abierto, haz clic en cualquier celda dentro del rango de datos.
2. Presiona Ctrl + T (o ve a Insertar → Tabla).
3. Confirma que "La tabla tiene encabezados" esté marcado.
4. Haz clic en Aceptar.
5. Verifica que aparezca la pestaña "Diseño de tabla" en la cinta.
```

> ⚠️ **Crítico:** Copilot en Excel requiere que los datos estén en formato de **Tabla** (no solo un rango). Este paso es obligatorio para que todos los prompts funcionen correctamente.

---

## 6. Pasos del Laboratorio

### Fase 1 — Exploración Inicial del Dataset (15 minutos)

---

#### Paso 1.1 — Familiarización con la estructura del dataset

**Objetivo:** Comprender la estructura y contenido del dataset antes de formular prompts, estableciendo el contexto operativo necesario para análisis precisos.

**Instrucciones:**

1. Con el archivo `Dataset_Logistico_Practica1.xlsx` abierto en Excel y los datos convertidos en Tabla (Paso D de configuración), examina visualmente las columnas disponibles. El dataset contiene las siguientes columnas principales:

   | Columna | Descripción |
   |---|---|
   | `ID_Pedido` | Identificador único del pedido |
   | `Fecha_Pedido` | Fecha en que se registró el pedido |
   | `Fecha_Entrega_Comprometida` | Fecha SLA prometida al cliente |
   | `Fecha_Entrega_Real` | Fecha en que se entregó efectivamente |
   | `SKU` | Código del producto |
   | `Transportista` | Empresa de transporte asignada |
   | `Estado_Pedido` | Estado actual (Entregado, Pendiente, En tránsito, Cancelado) |
   | `Cantidad_Unidades` | Unidades del pedido |
   | `Stock_Disponible` | Unidades en inventario al momento del pedido |
   | `Dias_Retraso` | Días de diferencia entre entrega real y comprometida |
   | `Alerta_SLA` | Indicador de incumplimiento (Sí/No) |

2. Anota el número total de filas (registros) y columnas que observas.

3. Identifica visualmente si hay celdas en blanco visibles o valores que parecen incorrectos.

**Resultado esperado:** Familiaridad con las 11 columnas del dataset y una estimación visual de posibles problemas de calidad de datos.

**Verificación:** Puedes contar las columnas en la fila de encabezados. Deberías ver exactamente 11 columnas (A hasta K). El dataset simulado contiene aproximadamente 200–500 registros.

---

#### Paso 1.2 — Primer prompt de exploración: Resumen general del dataset

**Objetivo:** Formular el primer prompt estructurado para obtener un resumen ejecutivo del dataset logístico, aplicando la estructura Rol + Tarea + Datos + Formato.

**Instrucciones:**

1. En la cinta de opciones de Excel, haz clic en el botón **Copilot** (pestaña `Inicio`). Se abrirá el panel de Copilot en el lado derecho de la pantalla.

2. En el cuadro de texto del panel de Copilot, escribe el siguiente prompt. Cópialo exactamente tal como aparece:

```
Actúa como analista de operaciones logísticas. 
Con base en la tabla activa de este archivo Excel, 
proporciona un resumen ejecutivo que incluya: 
(1) número total de pedidos, 
(2) distribución por Estado_Pedido (cuántos hay de cada tipo), 
(3) porcentaje de pedidos con Alerta_SLA = "Sí", 
(4) transportistas únicos presentes en el dataset. 
Presenta el resultado en formato de lista numerada, 
con valores numéricos concretos.
```

3. Presiona **Enter** o haz clic en el botón de enviar (ícono de flecha).

4. Espera la respuesta de Copilot (puede tardar entre 5 y 20 segundos dependiendo de la conexión).

5. Lee la respuesta completa antes de continuar.

**Resultado esperado:** Copilot debe generar una lista numerada con los cuatro puntos solicitados, incluyendo valores numéricos específicos como *"Total de pedidos: 347"* o *"Pedidos con alerta SLA: 23% (80 registros)"*.

**Verificación — Aplicar criterio de Exactitud Numérica:**

Verifica manualmente el punto más fácil de comprobar: el total de pedidos.

```excel
// En una celda vacía del archivo, escribe esta fórmula:
=COUNTA(A2:A1000)
// Ajusta el rango según el tamaño real de tu dataset.
// El resultado debe coincidir con el número reportado por Copilot.
```

Si hay discrepancia entre el número de Copilot y tu fórmula, anótalo. Lo abordarás en el refinamiento del Paso 1.3.

> 📝 **Recuerda:** La variabilidad es normal en Copilot. Si la respuesta tiene un formato diferente al esperado (por ejemplo, párrafo en lugar de lista), eso es una señal para refinar el prompt, no un error del sistema.

---

#### Paso 1.3 — Iteración del prompt: Refinamiento para mayor precisión

**Objetivo:** Practicar el ciclo de refinamiento de prompts cuando la primera respuesta no es suficientemente específica o tiene un formato inadecuado.

**Instrucciones:**

1. Evalúa la respuesta del Paso 1.2 usando los cinco criterios de validación. Completa mentalmente esta lista de verificación:

   | Criterio | ¿Se cumple? | Observación |
   |---|---|---|
   | Exactitud numérica | Sí / No | ¿Coincide con tu fórmula `COUNTA`? |
   | Coherencia lógica | Sí / No | ¿Los porcentajes suman 100%? |
   | Completitud | Sí / No | ¿Respondió los 4 puntos solicitados? |
   | Relevancia contextual | Sí / No | ¿Habla de logística o es genérico? |
   | Trazabilidad | Sí / No | ¿Puedes identificar de dónde viene cada dato? |

2. Si algún criterio **no se cumple**, escribe el siguiente prompt de refinamiento en el panel de Copilot (adapta según el problema identificado):

```
Tu respuesta anterior no incluyó [elemento faltante / tuvo un error en X]. 
Por favor, corrige y regenera el resumen. 
Asegúrate de que los porcentajes estén calculados sobre el total de pedidos 
y que cada punto incluya el valor numérico absoluto entre paréntesis.
```

3. Si **todos los criterios se cumplen**, escribe el siguiente prompt de profundización:

```
Actúa como analista de operaciones logísticas. 
Complementa el resumen anterior con: 
(1) el SKU con mayor frecuencia en el dataset, 
(2) el rango de fechas cubierto por el campo Fecha_Pedido 
(fecha más antigua y más reciente), 
(3) el transportista con más pedidos asignados. 
Formato: tabla de tres filas con columnas "Métrica" y "Valor".
```

4. Registra ambas respuestas (la inicial y la refinada) para comparación posterior.

**Resultado esperado:** Una tabla de tres filas con el SKU más frecuente, el rango de fechas del dataset y el transportista con más pedidos.

**Verificación — Aplicar criterio de Trazabilidad:**

```excel
// Verifica el transportista con más pedidos:
// En una celda vacía, usa:
=COUNTIF(F2:F500,"NombreTransportista")
// Reemplaza "NombreTransportista" con el valor reportado por Copilot.
// Compara con el valor que Copilot indicó.
```

---

### Fase 2 — Validación Cruzada y Detección de Inconsistencias (25 minutos)

---

#### Paso 2.1 — Diagnóstico de valores nulos y celdas vacías críticas

**Objetivo:** Usar Copilot para identificar campos críticos con valores nulos o vacíos que puedan comprometer la integridad del análisis operativo.

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt:

```
Actúa como auditor de calidad de datos logísticos. 
Analiza la tabla activa e identifica qué columnas contienen 
celdas vacías o valores nulos. 
Para cada columna con datos faltantes, indica: 
(a) nombre de la columna, 
(b) número aproximado de celdas vacías, 
(c) impacto operativo si ese campo está vacío 
    (por ejemplo: "sin Fecha_Entrega_Real no se puede calcular retraso"). 
Presenta el resultado en una tabla con columnas: 
Columna | Celdas vacías | Impacto operativo.
```

2. Lee la respuesta de Copilot y anota las columnas problemáticas identificadas.

3. Verifica manualmente la columna más crítica identificada (generalmente `Fecha_Entrega_Real` o `Dias_Retraso`):

```excel
// Contar celdas vacías en la columna Fecha_Entrega_Real (columna D):
=COUNTBLANK(D2:D500)

// Contar celdas vacías en Dias_Retraso (columna J):
=COUNTBLANK(J2:J500)
```

4. Compara los valores de tu fórmula con los reportados por Copilot. Anota cualquier discrepancia en tu cuaderno o en una hoja nueva del archivo llamada `Notas_Validacion`.

**Resultado esperado:** Una tabla que liste entre 2 y 5 columnas con datos faltantes, con el número aproximado de registros afectados y el impacto operativo de cada uno.

**Verificación:** El número de celdas vacías reportado por Copilot debe estar dentro de un margen razonable (±5%) del valor calculado por tu fórmula `COUNTBLANK`. Si la diferencia es mayor, aplica el criterio de **Exactitud numérica** y refina el prompt.

---

#### Paso 2.2 — Detección de fechas inválidas o incoherentes

**Objetivo:** Identificar registros donde las fechas lógicamente no tienen sentido (por ejemplo, fecha de entrega real anterior a la fecha del pedido), aplicando el criterio de **Coherencia lógica** de validación.

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt:

```
Actúa como analista de calidad de datos logísticos. 
Revisa las columnas Fecha_Pedido, Fecha_Entrega_Comprometida 
y Fecha_Entrega_Real en la tabla activa. 
Identifica registros que presenten cualquiera de estas anomalías: 
(1) Fecha_Entrega_Real anterior a Fecha_Pedido, 
(2) Fecha_Entrega_Comprometida anterior a Fecha_Pedido, 
(3) Fecha_Entrega_Real con valores que parezcan fechas de años futuros 
    (posterior a 2025). 
Reporta: número de registros con cada tipo de anomalía 
y los IDs de pedido de los primeros 3 casos de cada tipo. 
Formato: tabla con columnas Tipo_Anomalía | Cantidad | Ejemplos_ID_Pedido.
```

2. Revisa la respuesta de Copilot.

3. Verifica manualmente el primer tipo de anomalía usando la siguiente fórmula en una columna auxiliar temporal (por ejemplo, columna L):

```excel
// En la celda L2, escribe:
=IF(C2<B2, "ANOMALÍA: Entrega antes de pedido", "OK")
// Copia la fórmula hacia abajo para todos los registros.
// Luego filtra la columna L para ver solo las "ANOMALÍA".
// Cuenta cuántas hay y compara con el número reportado por Copilot.
```

4. Después de verificar, elimina la columna auxiliar L para mantener el dataset limpio.

**Resultado esperado:** Una tabla con los tres tipos de anomalías de fecha, indicando cuántos registros afecta cada una y ejemplos de IDs de pedido. En el dataset simulado, se han introducido deliberadamente entre 5 y 15 anomalías de este tipo.

**Verificación:** Aplica el criterio de **Coherencia lógica**: ¿tiene sentido que existan fechas de entrega anteriores a la fecha del pedido? Sí, son errores de captura de datos. ¿El número reportado por Copilot coincide con el conteo de tu fórmula auxiliar? Eso determina si el criterio de **Exactitud numérica** se cumple.

---

#### Paso 2.3 — Identificación de registros duplicados

**Objetivo:** Detectar pedidos con ID duplicado que puedan estar inflando métricas operativas como el total de órdenes o el volumen de unidades.

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt:

```
Actúa como auditor de integridad de datos. 
En la tabla activa, verifica si existen valores duplicados 
en la columna ID_Pedido. 
Reporta: 
(1) número total de IDs duplicados encontrados, 
(2) lista de los primeros 5 IDs que aparecen más de una vez, 
(3) impacto estimado en métricas si no se eliminan los duplicados 
    (por ejemplo: inflación del total de pedidos). 
Formato: lista numerada con los tres puntos solicitados.
```

2. Verifica manualmente la existencia de duplicados:

```excel
// Método 1: Formato condicional para resaltar duplicados
// Selecciona toda la columna A (ID_Pedido).
// Ve a: Inicio → Formato condicional → Resaltar reglas de celdas 
//        → Valores duplicados.
// Los duplicados quedarán resaltados en rojo.

// Método 2: Fórmula para contar duplicados
// En una celda vacía:
=SUMPRODUCT((COUNTIF(A2:A500,A2:A500)>1)*1)
// Esto cuenta cuántos registros tienen un ID que aparece más de una vez.
```

3. Compara el resultado de tu verificación manual con lo reportado por Copilot.

**Resultado esperado:** Copilot debe reportar entre 3 y 10 IDs duplicados en el dataset simulado (introducidos intencionalmente). La lista de los primeros 5 IDs duplicados debe ser verificable con el formato condicional.

**Verificación — Criterio de Trazabilidad:** ¿Puedes encontrar manualmente en el dataset los IDs que Copilot reportó como duplicados? Usa `Ctrl + F` para buscar uno de los IDs mencionados y confirma que aparece más de una vez.

---

#### Paso 2.4 — Síntesis del diagnóstico de calidad de datos

**Objetivo:** Consolidar todos los hallazgos de la Fase 2 en un resumen ejecutivo de calidad de datos usando Copilot.

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt de síntesis:

```
Actúa como consultor de calidad de datos logísticos. 
Con base en el análisis que hemos realizado en esta sesión 
sobre la tabla activa, genera un resumen ejecutivo de calidad de datos 
que incluya: 
(1) puntuación estimada de calidad del dataset del 1 al 10 
    (donde 10 es perfecto), justificando el puntaje, 
(2) los tres problemas de calidad más críticos encontrados, 
    ordenados por impacto operativo, 
(3) recomendaciones concretas para corregir cada problema. 
Formato: tabla con columnas Problema | Impacto | Recomendación.
```

2. Lee la respuesta y evalúa si la puntuación de calidad es coherente con los hallazgos de los pasos anteriores (criterio de **Coherencia lógica**).

3. Guarda la respuesta copiándola a la hoja `Notas_Validacion` de tu archivo Excel para referencia futura.

**Resultado esperado:** Una tabla de tres filas con los problemas críticos, su impacto operativo y recomendaciones de corrección, más una puntuación de calidad justificada (típicamente entre 5 y 7 para el dataset simulado).

**Verificación:** Aplica el criterio de **Relevancia contextual**: ¿las recomendaciones son específicas para logística o son genéricas? Una recomendación como *"Implementar validación de fechas en el sistema de captura de pedidos"* es contextualmente relevante. Una como *"Mejorar los datos"* no lo es.

---

### Fase 3 — Construcción de la Lista Priorizada de Acciones Operativas (15 minutos)

---

#### Paso 3.1 — Identificación de pedidos críticos del día

**Objetivo:** Usar Copilot para identificar los pedidos que requieren atención inmediata basándose en los criterios de urgencia operativa (SLA en riesgo, retrasos acumulados, stock insuficiente).

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt:

```
Actúa como coordinador de operaciones logísticas. 
Con base en la tabla activa, identifica los 10 pedidos 
que requieren atención más urgente hoy. 
Usa los siguientes criterios de priorización, en orden de importancia: 
(1) Estado_Pedido = "Pendiente" con Alerta_SLA = "Sí" (máxima prioridad), 
(2) Dias_Retraso > 2 y Estado_Pedido = "En tránsito", 
(3) Stock_Disponible < Cantidad_Unidades (riesgo de desabasto). 
Para cada pedido, muestra: ID_Pedido, Transportista, 
Dias_Retraso, motivo de priorización. 
Ordena de mayor a menor urgencia. 
Formato: tabla con las columnas indicadas.
```

2. Revisa la tabla generada por Copilot.

3. Verifica los primeros 3 pedidos de la lista manualmente:

```excel
// Para verificar el primer pedido de la lista:
// 1. Usa Ctrl + F para buscar el ID_Pedido reportado por Copilot.
// 2. Confirma que su Estado_Pedido = "Pendiente".
// 3. Confirma que su Alerta_SLA = "Sí".
// 4. Confirma el valor de Dias_Retraso.
```

**Resultado esperado:** Una tabla de 10 pedidos ordenados por urgencia, con el motivo de priorización claramente indicado para cada uno.

**Verificación:** Aplica el criterio de **Completitud**: ¿la tabla tiene exactamente 10 filas? ¿Todas las columnas solicitadas están presentes? Si falta alguna columna o hay menos de 10 pedidos (porque el dataset no tiene suficientes casos que cumplan los criterios), Copilot debe indicarlo explícitamente.

---

#### Paso 3.2 — Construcción del plan de acción diario priorizado

**Objetivo:** Transformar la lista de pedidos críticos en un plan de acción operativo estructurado que pueda comunicarse al equipo de trabajo.

**Instrucciones:**

1. En el panel de Copilot, escribe el siguiente prompt de acción:

```
Actúa como jefe de operaciones logísticas. 
Con base en los 10 pedidos críticos identificados en el análisis anterior, 
construye un plan de acción para el día de hoy con las siguientes secciones: 
SECCIÓN 1 - Acciones inmediatas (primeras 2 horas): 
  lista los 3 pedidos más urgentes con la acción específica recomendada 
  para cada uno (contactar transportista, liberar stock, escalar a gerencia). 
SECCIÓN 2 - Acciones de seguimiento (antes del mediodía): 
  lista los siguientes 4 pedidos con su acción recomendada. 
SECCIÓN 3 - Monitoreo continuo (resto del día): 
  los 3 pedidos restantes con indicadores de alerta a vigilar. 
Formato: tres secciones claramente separadas con subtítulos, 
acciones en viñetas, tono ejecutivo y directo.
```

2. Lee el plan generado por Copilot.

3. Evalúa el plan usando el criterio de **Relevancia contextual**: ¿las acciones recomendadas son realizables en un entorno logístico real? ¿Son específicas o genéricas?

4. Si alguna acción te parece genérica o poco práctica, escribe un prompt de refinamiento:

```
La acción para el pedido [ID] es demasiado genérica. 
Considerando que el transportista asignado es [nombre] 
y el retraso es de [X] días, 
¿qué acción específica recomiendas: 
reasignar transportista, aplicar penalización contractual 
o activar protocolo de entrega urgente? 
Justifica tu recomendación en máximo 2 oraciones.
```

**Resultado esperado:** Un plan de acción diario en tres secciones, con acciones específicas y asignables a miembros del equipo.

**Verificación:** El plan debe ser coherente con los datos del dataset. Por ejemplo, si un pedido tiene `Transportista = "LogiRápido"` y `Dias_Retraso = 5`, la acción recomendada debe mencionar a ese transportista específicamente, no ser genérica.

---

#### Paso 3.3 — Diseño de la secuencia de cinco prompts iterativos (actividad de síntesis)

**Objetivo:** Consolidar el aprendizaje de la práctica diseñando una secuencia personal de cinco prompts reutilizables para el diagnóstico operativo diario.

**Instrucciones:**

1. En una hoja nueva del archivo Excel llamada `Mis_Prompts`, crea una tabla con las siguientes columnas:

   | Columna | Descripción |
   |---|---|
   | `N°` | Número del prompt en la secuencia (1 al 5) |
   | `Fase` | Exploración / Validación / Priorización |
   | `Prompt` | Texto completo del prompt |
   | `Objetivo` | Qué información busca obtener |
   | `Criterio_Validacion` | Cómo verificarás que la respuesta es correcta |

2. Completa la tabla con los cinco prompts que usaste o refinaste durante esta práctica. Puedes usar los prompts de los pasos anteriores como base, adaptándolos con mejoras basadas en tu experiencia durante el laboratorio.

3. Para el Prompt 5, diseña uno **nuevo** que no hayas usado aún, orientado a un escenario logístico específico de tu operación real (o del dataset simulado). Aplica obligatoriamente la estructura de cuatro elementos:

```
Estructura obligatoria del Prompt 5:
ROL: "Actúa como [rol específico]..."
TAREA: "[Verbo de acción] [qué específicamente]..."
DATOS: "Con base en [fuente de datos / columna / período]..."
FORMATO: "Presenta el resultado en [tipo de formato]..."
```

4. Prueba el Prompt 5 en el panel de Copilot y documenta el resultado en la columna `Objetivo` de tu tabla.

**Resultado esperado:** Una hoja `Mis_Prompts` con cinco prompts documentados, reutilizables y con su criterio de validación definido. Esta hoja se convierte en tu biblioteca personal de prompts logísticos.

**Verificación:** Cada prompt debe tener los cuatro elementos de estructura (Rol, Tarea, Datos, Formato) identificables en el texto. Si alguno le falta un elemento, refínalo antes de guardar.

---

## 7. Validación y Pruebas Finales

Al completar las tres fases del laboratorio, ejecuta la siguiente lista de verificación integral:

### Lista de verificación de completitud

| # | Criterio de completitud | Estado |
|---|---|---|
| 1 | El archivo `Dataset_Logistico_Practica1.xlsx` está guardado en OneDrive con los datos en formato Tabla | ☐ |
| 2 | Completé al menos 6 prompts en el panel de Copilot durante la sesión | ☐ |
| 3 | Verifiqué manualmente al menos 3 resultados de Copilot usando fórmulas de Excel | ☐ |
| 4 | Identifiqué al menos 3 tipos de inconsistencias en el dataset (nulos, fechas inválidas, duplicados) | ☐ |
| 5 | Generé un plan de acción diario con 10 pedidos priorizados | ☐ |
| 6 | Creé la hoja `Mis_Prompts` con 5 prompts documentados | ☐ |
| 7 | Apliqué al menos una iteración de refinamiento de prompt durante la práctica | ☐ |
| 8 | Documenté los hallazgos de calidad de datos en la hoja `Notas_Validacion` | ☐ |

### Prueba de validación final

Ejecuta este prompt de cierre en el panel de Copilot para generar un resumen de todo el trabajo realizado en la sesión:

```
Actúa como asistente de documentación operativa. 
Resume en formato ejecutivo todo el análisis realizado 
en esta sesión de trabajo sobre el dataset logístico. 
Incluye: 
(1) hallazgos clave de calidad de datos (máximo 3 puntos), 
(2) los 3 pedidos más urgentes identificados con su motivo, 
(3) una recomendación de acción inmediata para el equipo operativo. 
Extensión máxima: 150 palabras. Tono: ejecutivo y directo.
```

Guarda esta respuesta en la hoja `Notas_Validacion` como *Resumen Ejecutivo de Sesión*.

---

## 8. Solución de Problemas

### Problema 1 — El botón de Copilot no aparece en la cinta de Excel

**Síntoma:** La pestaña `Inicio` de Excel no muestra el botón de Copilot (ícono de círculo de colores), o el botón aparece en gris y no es interactivo.

**Causa probable:** Una de las siguientes condiciones:
- La licencia de Microsoft 365 Copilot no está asignada a la cuenta del usuario (causa más frecuente).
- El archivo de Excel está guardado localmente (no en OneDrive/SharePoint).
- La versión de Excel es anterior a la 2308 o el canal de actualización no es el mensual.
- El administrador del tenant ha deshabilitado Copilot para el grupo de usuarios.

**Solución paso a paso:**

```
VERIFICACIÓN 1 — Confirmar licencia:
1. Abre un navegador y ve a: https://portal.office.com
2. Haz clic en tu foto de perfil (esquina superior derecha).
3. Selecciona "Ver cuenta" → "Suscripciones".
4. Verifica que aparezca "Microsoft 365 Copilot" en la lista de licencias.
   - Si NO aparece: contacta a tu administrador de TI. 
     Sin esta licencia, no es posible continuar.
   - Si SÍ aparece: continúa con la Verificación 2.

VERIFICACIÓN 2 — Confirmar ubicación del archivo:
1. En Excel, ve a Archivo → Información.
2. La ruta del archivo debe mostrar "OneDrive" o "SharePoint".
3. Si muestra una ruta local (C:\ o D:\), guarda el archivo en OneDrive:
   Archivo → Guardar como → OneDrive - [nombre de tu organización].
4. Cierra y vuelve a abrir el archivo desde OneDrive.

VERIFICACIÓN 3 — Actualizar Excel:
1. Ve a Archivo → Cuenta → Opciones de actualización → Actualizar ahora.
2. Espera que se complete la actualización.
3. Reinicia Excel y verifica si aparece el botón de Copilot.
```

---

### Problema 2 — Copilot genera respuestas genéricas o no hace referencia a los datos del archivo

**Síntoma:** El panel de Copilot responde con información general sobre logística o análisis de datos, pero no menciona valores específicos del dataset (por ejemplo, responde *"Los pedidos pendientes son aquellos que aún no han sido entregados"* en lugar de *"Hay 87 pedidos en estado Pendiente"*).

**Causa probable:** Una de las siguientes condiciones:
- Los datos no están en formato de **Tabla** de Excel (el requisito más común omitido).
- El cursor no está posicionado dentro del rango de datos al abrir el panel de Copilot.
- El prompt no hace referencia explícita a la tabla o al archivo activo.
- El archivo tiene múltiples hojas y Copilot no sabe cuál analizar.

**Solución paso a paso:**

```
SOLUCIÓN 1 — Confirmar formato de Tabla:
1. Haz clic en cualquier celda dentro de tus datos.
2. Ve a Insertar → Tabla (o presiona Ctrl + T).
3. Si ya es una Tabla, verás la pestaña "Diseño de tabla" en la cinta.
4. Si no es una Tabla, conviértela ahora y cierra/reabre el panel de Copilot.

SOLUCIÓN 2 — Posicionar el cursor dentro de la Tabla:
1. Cierra el panel de Copilot (X en la esquina superior del panel).
2. Haz clic en cualquier celda DENTRO del rango de datos 
   (no en una celda vacía fuera de la tabla).
3. Vuelve a abrir Copilot desde la cinta: Inicio → Copilot.
4. El panel debe mostrar el nombre de la tabla en la parte superior 
   (por ejemplo: "Tabla1" o "Dataset_Logistico").

SOLUCIÓN 3 — Hacer referencia explícita en el prompt:
En lugar de escribir "analiza los datos", especifica:
"Con base en la Tabla1 de la hoja activa de este archivo Excel..."
Esto fuerza a Copilot a anclar su análisis a los datos específicos.

SOLUCIÓN 4 — Verificar que la hoja activa es la correcta:
Si el archivo tiene múltiples hojas (Dataset, Notas_Validacion, Mis_Prompts),
asegúrate de que la pestaña activa sea "Dataset" antes de abrir Copilot.
```

---

## 9. Limpieza del Entorno

Al finalizar la práctica, realiza las siguientes acciones para mantener el entorno ordenado:

1. **Eliminar columnas auxiliares temporales:**
   ```
   Si creaste columnas auxiliares durante la Fase 2 (por ejemplo, columna L 
   para verificación de fechas), selecciónalas y elimínalas:
   Clic derecho en el encabezado de columna → Eliminar.
   ```

2. **Guardar el archivo con las hojas de documentación:**
   ```
   Asegúrate de que el archivo tenga tres hojas:
   - Hoja principal: Dataset_Logistico (con los datos originales + Tabla)
   - Hoja de notas: Notas_Validacion (con hallazgos y resumen ejecutivo)
   - Hoja de prompts: Mis_Prompts (con tus 5 prompts documentados)
   
   Guarda con: Ctrl + S
   Confirma que se guarda en OneDrive (no localmente).
   ```

3. **Eliminar formato condicional de duplicados (si fue aplicado):**
   ```
   Selecciona la columna A (ID_Pedido).
   Ve a: Inicio → Formato condicional → Borrar reglas → 
         Borrar reglas de las celdas seleccionadas.
   ```

4. **Cerrar el panel de Copilot:**
   ```
   Haz clic en la X del panel de Copilot para cerrarlo.
   Esto libera recursos de memoria, especialmente útil 
   si continuarás con la Práctica 2 en la misma sesión.
   ```

5. **Compartir el archivo con el instructor (si se solicita):**
   ```
   Archivo → Compartir → Copiar vínculo → 
   Seleccionar "Personas con el vínculo de [organización] pueden editar".
   Envía el vínculo al instructor según las instrucciones del curso.
   ```

---

## 10. Resumen

### Logros de esta práctica

En esta práctica ejecutaste un diagnóstico operativo completo de un dataset logístico utilizando Microsoft Copilot integrado en Excel. Aplicaste el ciclo **prompt → resultado → validación → refinamiento** en tres fases progresivas:

- **Fase 1 (Exploración):** Formulaste prompts estructurados con los cuatro elementos (Rol + Tarea + Datos + Formato) para obtener un resumen ejecutivo del dataset, y practicaste la iteración cuando la primera respuesta no era suficientemente precisa.

- **Fase 2 (Validación):** Detectaste tres tipos de inconsistencias críticas —valores nulos, fechas inválidas y registros duplicados— y aplicaste los cinco criterios de validación (exactitud numérica, coherencia lógica, completitud, relevancia contextual y trazabilidad) para verificar cada resultado de Copilot antes de confiar en él.

- **Fase 3 (Priorización):** Transformaste los hallazgos en un plan de acción operativo concreto con 10 pedidos priorizados y acciones asignables, y construiste tu biblioteca personal de cinco prompts reutilizables.

### Conceptos clave reforzados

| Concepto | Aplicación en esta práctica |
|---|---|
| Estructura de 4 elementos del prompt | Usada en todos los prompts de las tres fases |
| Ciclo iterativo de refinamiento | Aplicado en los Pasos 1.3, 3.2 y 3.3 |
| 5 criterios de validación | Verificados manualmente con fórmulas de Excel en cada fase |
| Alucinación de IA | Detectada y corregida mediante verificación cruzada con `COUNTIF`, `COUNTBLANK` y `COUNTA` |
| Prompt de síntesis | Usado en el Paso 2.4 y en la validación final |

### Preparación para la Práctica 2

La **Práctica 2** utilizará directamente los hallazgos de calidad de datos documentados en tu hoja `Notas_Validacion` para construir dashboards ejecutivos y visualizaciones de KPIs logísticos. Antes de la siguiente sesión:

- Asegúrate de que tu archivo esté guardado en OneDrive con las tres hojas completas.
- Revisa los 5 prompts de tu hoja `Mis_Prompts` y piensa cómo podrían adaptarse para análisis visual.
- Practica la reformulación de al menos 2 prompts propios de tu operación real, aplicando la estructura de cuatro elementos.

### Recursos adicionales

| Recurso | URL |
|---|---|
| Documentación oficial de Copilot para Microsoft 365 | [learn.microsoft.com/es-es/copilot/microsoft-365/](https://learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-overview) |
| Guía de ingeniería de prompts de Microsoft | [learn.microsoft.com/es-es/azure/ai-services/openai/concepts/prompt-engineering](https://learn.microsoft.com/es-es/azure/ai-services/openai/concepts/prompt-engineering) |
| Uso de Copilot en Excel para análisis de datos | [learn.microsoft.com/es-es/copilot/microsoft-365/use-cases/excel](https://learn.microsoft.com/es-es/copilot/microsoft-365/use-cases/excel) |
| Galería de prompts de Microsoft Copilot | [adoption.microsoft.com/es-es/copilot-scenario-library/](https://adoption.microsoft.com/es-es/copilot-scenario-library/) |

---

> 💡 **Recordatorio final:** Los resultados de Copilot son **no determinísticos**. El mismo prompt puede producir respuestas ligeramente diferentes en cada ejecución. Esto es normal y esperado. La habilidad que has desarrollado hoy —validar críticamente cada resultado antes de actuar sobre él— es precisamente lo que convierte a Copilot en un aliado confiable en tu operación logística, en lugar de una fuente de errores no detectados.

---
LAB_END---

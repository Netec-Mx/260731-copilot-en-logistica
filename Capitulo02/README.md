---LAB_START---
LAB_ID: 02-00-01
---MARKDOWN---
# Práctica 2 — Generación Automatizada de Dashboards y Resúmenes Operativos

## 1. Metadatos

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Aplicar (Apply) |
| **Módulo** | 2 — Dashboards Ejecutivos y Reportes de Cumplimiento Logístico |
| **Herramientas principales** | Microsoft Excel con Copilot, Microsoft OneDrive |
| **Licencia requerida** | Microsoft 365 Copilot (activa) |

---

## 2. Descripción General

En esta práctica construirás un dashboard operativo logístico completo a partir de un dataset de entregas simulado. Utilizarás Copilot en Excel para calcular KPIs clave como OTIF, Fill Rate, Tasa de Devoluciones y Tiempo de Ciclo de Orden, generarás visualizaciones comparativas asistidas por Copilot y redactarás un resumen ejecutivo de una página listo para presentar a una audiencia gerencial. La práctica refuerza la metodología de tres pasos aprendida en la Lección 2.1 —calcular, visualizar, segmentar— y añade una etapa de revisión crítica donde evaluarás si las visualizaciones comunican correctamente la realidad operativa.

---

## 3. Objetivos de Aprendizaje

Al completar este laboratorio serás capaz de:

- [ ] Utilizar Copilot en Excel para calcular e interpretar KPIs logísticos clave (OTIF, Fill Rate, Tasa de Devoluciones, Tiempo de Ciclo de Orden) a partir de un dataset estructurado.
- [ ] Generar automáticamente visualizaciones (gráficas de barras, líneas de tendencia, tablas de ranking) asistidas por Copilot que representen el desempeño operativo de forma ejecutiva.
- [ ] Aplicar prompts de análisis comparativo para identificar períodos de alto y bajo desempeño y formular hipótesis sobre sus causas.
- [ ] Redactar un resumen ejecutivo logístico de una página usando Copilot, con hallazgos clave, tendencias preocupantes y recomendaciones de acción.
- [ ] Evaluar críticamente las visualizaciones generadas por Copilot y realizar ajustes iterativos mediante prompts refinados.

---

## 4. Prerrequisitos

### Conocimiento previo

| Área | Nivel requerido |
|---|---|
| Práctica 1 del curso (diagnóstico de datos con Copilot) | Completada o experiencia equivalente |
| KPIs logísticos: OTIF, Fill Rate, Lead Time, Tasa de Devoluciones | Comprensión básica |
| Tablas de Excel y tipos de gráficas | Conocimiento básico |
| Uso del panel de Copilot en Excel | Familiaridad básica |

### Acceso y recursos necesarios

| Recurso | Estado requerido |
|---|---|
| Licencia activa de Microsoft 365 Copilot | ✅ Verificada antes de iniciar |
| Archivo `Dataset_Logistico_P2.xlsx` | Descargado en OneDrive (proporcionado por el instructor) |
| Plantilla `Reporte_Ejecutivo_Logistico.xlsx` | Descargada en OneDrive (proporcionada por el instructor) |
| Microsoft Excel (versión 2308 o posterior) | Instalado y actualizado |
| Conexión a Internet estable (≥ 10 Mbps) | Activa durante toda la práctica |
| Microsoft OneDrive para la Empresa | Sesión iniciada |

> ⚠️ **Nota crítica:** Copilot en Excel **solo funciona cuando el archivo está guardado en OneDrive o SharePoint**. Si el archivo está en el escritorio local, Copilot no estará disponible. Verifica esto antes de comenzar.

---

## 5. Entorno del Laboratorio

### Hardware recomendado

| Componente | Mínimo | Recomendado |
|---|---|---|
| RAM | 8 GB | 16 GB |
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| Almacenamiento libre | 10 GB | 20 GB |
| Resolución de pantalla | 1366 × 768 | 1920 × 1080 |
| Conexión a Internet | 10 Mbps bajada | 25 Mbps bajada |

### Software requerido

| Aplicación | Versión mínima | Verificación |
|---|---|---|
| Microsoft Excel | 2308 (Microsoft 365) | `Archivo → Cuenta → Acerca de Excel` |
| Microsoft Copilot en Excel | Activo con licencia M365 Copilot | Panel Copilot visible en pestaña Inicio |
| Microsoft OneDrive para la Empresa | Versión actual | Icono en bandeja del sistema, sesión activa |
| Microsoft Edge | Versión 115 o posterior | `edge://settings/help` |

### Configuración inicial del entorno

Sigue estos pasos **antes** de comenzar las actividades del laboratorio:

**Paso A — Verificar que Copilot está activo en Excel:**

1. Abre Microsoft Excel.
2. En la pestaña **Inicio**, busca el ícono **Copilot** (estrella de colores) en el extremo derecho de la cinta.
3. Si el ícono no aparece, ve a `Archivo → Opciones → General` y verifica que la cuenta de Microsoft 365 con licencia Copilot esté activa.

**Paso B — Subir los archivos a OneDrive:**

1. Abre el Explorador de archivos y localiza los archivos proporcionados por el instructor:
   - `Dataset_Logistico_P2.xlsx`
   - `Reporte_Ejecutivo_Logistico.xlsx`
2. Copia ambos archivos a tu carpeta de OneDrive para la Empresa (por ejemplo: `OneDrive - [Nombre Empresa] / Curso_M365_Copilot / Practica2 /`).
3. Espera a que los archivos muestren el ícono de sincronización ✅ (nube verde).

**Paso C — Abrir el dataset desde OneDrive:**

1. En Excel, ve a `Archivo → Abrir → OneDrive - [Nombre Empresa]`.
2. Navega a la carpeta `Practica2` y abre `Dataset_Logistico_P2.xlsx`.
3. Confirma que en la barra de título aparece el nombre del archivo **sin** el prefijo `[Solo lectura]`.

> 💡 **Descripción del dataset:** El archivo `Dataset_Logistico_P2.xlsx` contiene una tabla llamada `TBL_Entregas` con aproximadamente 1,500 registros de entregas simuladas correspondientes a un trimestre (enero–marzo). Las columnas incluyen: `ID_Pedido`, `Fecha_Pedido`, `Fecha_Entrega_Programada`, `Fecha_Entrega_Real`, `Estado_Entrega` (A tiempo / Tardío / Devuelto), `Region` (Norte / Sur / Centro / Occidente), `Transportista`, `Categoria_Producto`, `Unidades_Solicitadas`, `Unidades_Entregadas`, `Costo_Envio_MXN`, `Dias_Ciclo`.

---

## 6. Instrucciones Paso a Paso

### Etapa 1: Verificación de la Estructura del Dataset y Activación de Copilot

**Objetivo:** Confirmar que el dataset cumple los requisitos técnicos para que Copilot opere correctamente y familiarizarse con la estructura de los datos.

**Tiempo estimado:** 10 minutos

---

#### Instrucciones

**1.** Con el archivo `Dataset_Logistico_P2.xlsx` abierto, haz clic en cualquier celda dentro del rango de datos.

**2.** Verifica que los datos están en formato de **Tabla de Excel** estructurada:
   - En la pestaña **Diseño de tabla** (o **Table Design**), confirma que el nombre de la tabla es `TBL_Entregas`.
   - Si el rango no está como tabla, selecciona todo el rango y presiona `Ctrl + T`, marca "La tabla tiene encabezados" y acepta.

**3.** Revisa los tipos de dato de las columnas críticas:
   - Selecciona la columna `Fecha_Pedido` → confirma que el formato de celda es **Fecha**.
   - Selecciona la columna `Costo_Envio_MXN` → confirma que el formato es **Número** o **Moneda**.
   - Selecciona la columna `Estado_Entrega` → confirma que el formato es **Texto**.

**4.** Abre el panel de Copilot haciendo clic en **Inicio → Copilot** en la cinta de opciones.

**5.** En el campo de texto del panel Copilot, escribe el siguiente prompt de verificación:

```
Describe brevemente el contenido de esta tabla. ¿Cuántos registros tiene? ¿Cuáles son las columnas principales?
```

**6.** Presiona `Enter` o el botón de enviar y espera la respuesta de Copilot (generalmente 5–15 segundos).

---

**Resultado esperado:**

Copilot debe responder con una descripción similar a:

> *"Esta tabla contiene 1,500 registros de entregas logísticas con 12 columnas. Las columnas incluyen identificadores de pedido, fechas de pedido y entrega, estado de entrega, región, transportista, categoría de producto, unidades solicitadas y entregadas, costo de envío y días de ciclo."*

La respuesta puede variar en redacción, pero debe identificar correctamente el número aproximado de registros y las columnas principales.

---

**Verificación:**

- [ ] El nombre de la tabla en la cinta es `TBL_Entregas`.
- [ ] Las columnas de fecha tienen formato `Fecha` y las numéricas tienen formato `Número`.
- [ ] El panel de Copilot está abierto y ha respondido al prompt de verificación.
- [ ] No hay mensajes de error en el panel de Copilot (como "No se puede analizar esta tabla").

---

### Etapa 2: Cálculo de KPIs Logísticos con Copilot

**Objetivo:** Usar Copilot para calcular los cuatro KPIs principales —OTIF, Fill Rate, Tasa de Devoluciones y Tiempo de Ciclo promedio— y crear una hoja de resumen de métricas.

**Tiempo estimado:** 20 minutos

---

#### Instrucciones

**1.** Asegúrate de que el cursor está dentro de la tabla `TBL_Entregas` y el panel de Copilot está abierto.

**2.** Calcula el **OTIF mensual**. En el panel de Copilot escribe:

```
Calcula el porcentaje de entregas con Estado_Entrega igual a 'A tiempo' agrupado por mes (basado en Fecha_Entrega_Real). Muéstrame los resultados en una tabla de resumen y llama a la métrica OTIF_Pct.
```

**3.** Cuando Copilot genere la respuesta, haz clic en el botón **"Insertar hoja"** o **"Agregar a hoja"** si aparece disponible. Si Copilot sugiere insertar una tabla dinámica, acepta la sugerencia. Renombra la hoja resultante como `KPI_OTIF`.

**4.** Regresa a la hoja principal (`TBL_Entregas`) y calcula el **Fill Rate mensual**. En el panel de Copilot escribe:

```
Calcula el Fill Rate mensual como (suma de Unidades_Entregadas / suma de Unidades_Solicitadas) × 100, agrupado por mes. Llama a la métrica FillRate_Pct.
```

**5.** Inserta los resultados en una nueva hoja llamada `KPI_FillRate`.

**6.** Calcula la **Tasa de Devoluciones**. En el panel de Copilot escribe:

```
Calcula la tasa de devoluciones como el porcentaje de registros donde Estado_Entrega es 'Devuelto' sobre el total de pedidos, agrupado por mes y por Region. Muéstrame los resultados ordenados de mayor a menor tasa.
```

**7.** Inserta los resultados en una nueva hoja llamada `KPI_Devoluciones`.

**8.** Calcula el **Tiempo de Ciclo promedio**. En el panel de Copilot escribe:

```
Calcula el promedio de Dias_Ciclo agrupado por mes y por Transportista. ¿Cuál es el transportista con el mayor tiempo de ciclo promedio en cada mes?
```

**9.** Inserta los resultados en una nueva hoja llamada `KPI_CicloOrden`.

**10.** En la hoja `KPI_OTIF`, revisa los valores calculados. Si el OTIF de algún mes está por debajo del 95%, anota ese mes como "alerta" en una celda adyacente con el texto `⚠️ Incumplimiento SLA`.

---

**Resultado esperado:**

Deberás tener cuatro hojas nuevas en el libro de Excel:
- `KPI_OTIF` con tabla de OTIF mensual (3 meses: enero, febrero, marzo).
- `KPI_FillRate` con tabla de Fill Rate mensual.
- `KPI_Devoluciones` con tabla de devoluciones por mes y región.
- `KPI_CicloOrden` con tabla de días de ciclo por mes y transportista.

Los valores de OTIF deben estar en el rango de 80%–98% (valores simulados). Si algún mes muestra 0% o 100% exacto, probablemente hay un error en el filtro del prompt; consulta la sección de Resolución de Problemas.

---

**Verificación:**

- [ ] Existen cuatro hojas de KPIs en el libro.
- [ ] Los porcentajes de OTIF y Fill Rate están expresados entre 0 y 100 (no en decimales como 0.92).
- [ ] La tabla de devoluciones muestra al menos dos regiones con valores distintos.
- [ ] La tabla de ciclo de orden identifica al menos un transportista con tiempo promedio superior a los demás.

---

### Etapa 3: Generación de Visualizaciones Asistidas por Copilot

**Objetivo:** Crear un conjunto de visualizaciones ejecutivas —gráfica de líneas de tendencia, gráfica de barras comparativa y tabla de ranking— que formen la base visual del dashboard.

**Tiempo estimado:** 25 minutos

---

#### Instrucciones

**1.** Crea una nueva hoja en el libro y nómbrala `Dashboard_Visual`. Esta será la hoja principal del dashboard.

**2.** Regresa a la hoja `TBL_Entregas` y asegúrate de que el panel de Copilot está activo.

**3.** Genera la **gráfica de tendencia de OTIF**. En el panel de Copilot escribe:

```
Crea un gráfico de líneas que muestre la evolución mensual del porcentaje de entregas a tiempo (OTIF) durante los tres meses. Añade una línea de referencia horizontal en el 95% como umbral objetivo. Titula el gráfico 'Tendencia OTIF Mensual - Q1'.
```

**4.** Cuando Copilot genere el gráfico, selecciónalo y cópialo (`Ctrl + C`). Ve a la hoja `Dashboard_Visual` y pégalo (`Ctrl + V`) en la esquina superior izquierda (aproximadamente celda B2).

**5.** Regresa a `TBL_Entregas`. Genera la **gráfica comparativa por región**. En el panel de Copilot escribe:

```
Crea un gráfico de barras agrupadas que compare el OTIF promedio por Region (Norte, Sur, Centro, Occidente) para el trimestre completo. Ordena las barras de mayor a menor OTIF. Titula el gráfico 'OTIF por Región - Q1'.
```

**6.** Copia el gráfico generado a la hoja `Dashboard_Visual` (posición aproximada: celda H2).

**7.** Genera la **gráfica de Fill Rate y Devoluciones combinada**. En el panel de Copilot escribe:

```
Crea un gráfico de barras que muestre el Fill Rate mensual y superpón una línea secundaria con la tasa de devoluciones mensual. Usa el eje izquierdo para Fill Rate y el eje derecho para devoluciones. Titula el gráfico 'Fill Rate vs. Tasa de Devoluciones - Q1'.
```

**8.** Copia este gráfico a la hoja `Dashboard_Visual` (posición aproximada: celda B20).

**9.** Genera el **ranking de transportistas por tiempo de ciclo**. En el panel de Copilot escribe:

```
Crea una tabla de ranking que muestre los 5 transportistas con mayor tiempo de ciclo promedio en el trimestre. Incluye columnas: Transportista, Dias_Ciclo_Promedio, Num_Pedidos, Porcentaje_Tardios. Ordena de mayor a menor tiempo de ciclo.
```

**10.** Inserta la tabla de ranking en la hoja `Dashboard_Visual` (posición aproximada: celda H20).

**11.** En la hoja `Dashboard_Visual`, agrega un título principal en la celda B1:

```
DASHBOARD OPERATIVO LOGÍSTICO — Q1 [AÑO ACTUAL]
```

Aplica formato: fuente **Calibri 16pt, negrita**, color de fondo azul oscuro (#1F3864), color de texto blanco.

---

**Resultado esperado:**

La hoja `Dashboard_Visual` debe contener:
- Título principal del dashboard en la parte superior.
- Gráfica de líneas de tendencia OTIF con línea de referencia al 95%.
- Gráfica de barras comparativa de OTIF por región.
- Gráfica combinada de Fill Rate vs. Tasa de Devoluciones.
- Tabla de ranking de los 5 transportistas con mayor tiempo de ciclo.

> ⚠️ **Nota sobre variabilidad de Copilot:** Copilot puede no generar exactamente el tipo de gráfica solicitado en el primer intento. Si el gráfico generado no corresponde al tipo pedido (por ejemplo, genera un gráfico de pastel en lugar de barras), usa el siguiente prompt de corrección:
> ```
> El gráfico anterior no es correcto. Necesito específicamente un gráfico de barras agrupadas, no un gráfico de pastel. Por favor, genera nuevamente el gráfico con el tipo correcto.
> ```

---

**Verificación:**

- [ ] La hoja `Dashboard_Visual` contiene al menos 3 gráficos y 1 tabla de ranking.
- [ ] El gráfico de tendencia OTIF muestra los tres meses en el eje X y tiene una línea de referencia visible al 95%.
- [ ] El gráfico de barras por región muestra las 4 regiones con valores distintos.
- [ ] La tabla de ranking contiene exactamente 5 transportistas con sus métricas.

---

### Etapa 4: Análisis Comparativo e Identificación de Anomalías

**Objetivo:** Aplicar prompts de análisis comparativo para identificar períodos de alto y bajo desempeño, detectar anomalías y formular hipótesis sobre sus causas.

**Tiempo estimado:** 15 minutos

---

#### Instrucciones

**1.** Con el panel de Copilot abierto y el cursor en la tabla `TBL_Entregas`, realiza un análisis de períodos críticos. Escribe en Copilot:

```
Identifica las 3 semanas con el OTIF más bajo durante el trimestre. Para cada semana, muéstrame: número de semana, fecha de inicio, OTIF de esa semana, región con más tardanzas y transportista con más tardanzas. Presenta los resultados en una tabla.
```

**2.** Analiza la correlación entre costo y desempeño. En Copilot escribe:

```
¿Existe alguna relación entre el Costo_Envio_MXN promedio y el Estado_Entrega? Compara el costo promedio de envíos 'A tiempo' versus 'Tardío' versus 'Devuelto'. ¿Qué observas?
```

**3.** Detecta anomalías en el tiempo de ciclo. En Copilot escribe:

```
Identifica pedidos donde Dias_Ciclo sea mayor a 2 desviaciones estándar por encima del promedio general. ¿Cuántos pedidos son? ¿Qué región y transportista concentran más de estos casos atípicos?
```

**4.** Realiza un análisis de categoría de producto. En Copilot escribe:

```
¿Qué categorías de producto tienen la tasa de devoluciones más alta? Muéstrame las 3 primeras categorías con mayor tasa de devoluciones y el Fill Rate promedio de cada una.
```

**5.** Crea una nueva hoja llamada `Analisis_Anomalias` e inserta los resultados de los cuatro análisis anteriores. Organízalos con títulos claros para cada sección.

**6.** En la hoja `Analisis_Anomalias`, agrega una celda de texto con el título "Hipótesis sobre causas de bajo desempeño:" y debajo escribe manualmente (no con Copilot) al menos **2 hipótesis** basadas en los hallazgos. Por ejemplo:

> *"Las semanas 3 y 7 coinciden con el transportista X como el de mayor tardanza; hipótesis: capacidad de flota insuficiente en esas semanas."*

> *"La región Sur tiene el OTIF más bajo y la mayor tasa de devoluciones; hipótesis: posibles problemas de infraestructura vial o cobertura de última milla."*

---

**Resultado esperado:**

La hoja `Analisis_Anomalias` debe contener:
- Tabla con las 3 semanas de menor OTIF y sus características.
- Comparación de costos de envío por estado de entrega.
- Lista de pedidos atípicos por tiempo de ciclo con región y transportista.
- Ranking de 3 categorías de producto con mayor tasa de devoluciones.
- Al menos 2 hipótesis escritas por el participante.

---

**Verificación:**

- [ ] La hoja `Analisis_Anomalias` contiene los cuatro análisis solicitados.
- [ ] Las hipótesis están escritas en lenguaje operativo claro y hacen referencia a datos específicos del análisis.
- [ ] Los pedidos atípicos identificados representan menos del 10% del total (si el porcentaje es mayor, revisar el cálculo de desviación estándar con Copilot).

---

### Etapa 5: Redacción del Resumen Ejecutivo con Copilot

**Objetivo:** Usar Copilot para generar un resumen ejecutivo logístico de una página, con hallazgos clave, tendencias preocupantes y recomendaciones de acción, listo para presentar a una audiencia gerencial.

**Tiempo estimado:** 15 minutos

---

#### Instrucciones

**1.** Abre el archivo `Reporte_Ejecutivo_Logistico.xlsx` desde OneDrive. Este archivo contiene una hoja llamada `Resumen_Ejecutivo` con una plantilla de formato preconfigurada (encabezado corporativo, secciones etiquetadas, pie de página).

**2.** Regresa al archivo `Dataset_Logistico_P2.xlsx` y asegúrate de que el panel de Copilot está activo.

**3.** Genera el texto del resumen ejecutivo. En el panel de Copilot escribe el siguiente prompt estructurado:

```
Basándote en los datos de esta tabla, redacta un resumen ejecutivo de operaciones logísticas para el Q1. El resumen debe tener las siguientes secciones:
1. Desempeño General: incluye los valores de OTIF, Fill Rate y Tasa de Devoluciones promedio del trimestre.
2. Hallazgos Clave: menciona las 2 regiones con menor OTIF y el transportista con mayor tiempo de ciclo.
3. Alertas Operativas: identifica métricas que estén por debajo del umbral objetivo (OTIF < 95%, Fill Rate < 92%).
4. Recomendaciones: propón 3 acciones concretas basadas en los hallazgos.
El tono debe ser formal y ejecutivo. Longitud máxima: 300 palabras.
```

**4.** Copia el texto generado por Copilot (`Ctrl + C`).

**5.** Ve al archivo `Reporte_Ejecutivo_Logistico.xlsx`, hoja `Resumen_Ejecutivo`, y pega el texto en la celda designada para el contenido del resumen (indicada en la plantilla con el marcador `[INSERTAR RESUMEN AQUÍ]`).

**6.** Revisa el texto generado críticamente. Verifica que:
   - Los valores numéricos mencionados coincidan con los KPIs calculados en la Etapa 2.
   - Las regiones y transportistas mencionados correspondan a los hallazgos de la Etapa 4.
   - El tono sea apropiado para una audiencia directiva.

**7.** Si necesitas ajustar el texto, usa Copilot con un prompt de refinamiento. Por ejemplo:

```
El resumen anterior es bueno pero las recomendaciones son muy genéricas. Por favor, reformula la sección de Recomendaciones con acciones más específicas y medibles, como 'reducir el tiempo de ciclo del transportista X en un 15% para el Q2 mediante renegociación de SLA'.
```

**8.** Actualiza el encabezado de la plantilla con los datos del participante:
   - Celda `Preparado por:` → Tu nombre completo.
   - Celda `Fecha:` → Fecha de hoy.
   - Celda `Período analizado:` → Q1 (Enero–Marzo [Año]).

---

**Resultado esperado:**

El archivo `Reporte_Ejecutivo_Logistico.xlsx` debe contener un resumen ejecutivo completo con:
- Valores numéricos de KPIs del trimestre.
- Identificación de al menos 2 áreas de bajo desempeño.
- Al menos 1 alerta de incumplimiento de SLA.
- 3 recomendaciones de acción específicas y medibles.
- Datos del preparador y período en el encabezado.

---

**Verificación:**

- [ ] El resumen ejecutivo tiene las 4 secciones solicitadas (Desempeño General, Hallazgos Clave, Alertas Operativas, Recomendaciones).
- [ ] Los valores numéricos del resumen son consistentes con los KPIs calculados en la Etapa 2.
- [ ] El texto no excede las 300 palabras.
- [ ] El encabezado de la plantilla está completo con nombre, fecha y período.

---

### Etapa 6: Revisión Crítica del Dashboard y Ajustes Iterativos

**Objetivo:** Evaluar si las visualizaciones del dashboard comunican correctamente la realidad operativa e implementar mejoras mediante prompts iterativos.

**Tiempo estimado:** 5 minutos

---

#### Instrucciones

**1.** Abre la hoja `Dashboard_Visual` del archivo `Dataset_Logistico_P2.xlsx` y observa el conjunto completo de visualizaciones.

**2.** Aplica los siguientes criterios de evaluación crítica para cada gráfico (marca mentalmente o en papel):

   | Criterio | ¿Cumple? |
   |---|---|
   | El título del gráfico es descriptivo y menciona el período | Sí / No |
   | Los ejes tienen etiquetas con unidades claras (%, días, MXN) | Sí / No |
   | La escala del eje Y es apropiada (no distorsiona la percepción) | Sí / No |
   | Los colores distinguen claramente las categorías | Sí / No |
   | La línea de referencia al 95% es visible en el gráfico de OTIF | Sí / No |

**3.** Para cualquier criterio que no se cumpla, usa Copilot para corregirlo. Ejemplo de prompt de ajuste:

```
En el gráfico de tendencia OTIF, el eje Y comienza en 0% en lugar de comenzar en 70%. Esto hace que las diferencias entre meses parezcan muy pequeñas. Ajusta el eje Y para que comience en 70% y termine en 100%.
```

**4.** Si algún gráfico no comunica claramente la información, solicita a Copilot una alternativa:

```
El gráfico de Fill Rate vs. Devoluciones es difícil de leer con dos ejes. ¿Podrías generar en su lugar dos gráficos separados de barras simples, uno para Fill Rate y otro para Tasa de Devoluciones, para facilitar la lectura?
```

**5.** Una vez satisfecho con el dashboard, guarda el archivo en OneDrive presionando `Ctrl + S`.

---

**Resultado esperado:**

El dashboard final debe cumplir al menos 4 de los 5 criterios de evaluación para cada gráfico. Los ajustes realizados deben estar documentados (el participante puede anotar en la hoja `Analisis_Anomalias` qué ajustes hizo y por qué).

---

**Verificación:**

- [ ] Al menos 4 de 5 criterios de evaluación se cumplen para cada gráfico del dashboard.
- [ ] El archivo está guardado en OneDrive (ícono de sincronización ✅ visible).
- [ ] Los ajustes realizados mediante prompts iterativos mejoraron la legibilidad del dashboard.

---

## 7. Validación y Pruebas del Laboratorio

Una vez completadas todas las etapas, realiza las siguientes verificaciones finales para confirmar que el laboratorio fue completado exitosamente:

### Lista de verificación final

| # | Elemento a verificar | Criterio de éxito |
|---|---|---|
| 1 | Hoja `KPI_OTIF` | Contiene tabla con OTIF mensual para 3 meses; al menos 1 mes marcado con alerta si OTIF < 95% |
| 2 | Hoja `KPI_FillRate` | Contiene tabla con Fill Rate mensual expresado como porcentaje |
| 3 | Hoja `KPI_Devoluciones` | Contiene tabla con tasa de devoluciones por mes y región |
| 4 | Hoja `KPI_CicloOrden` | Contiene tabla con días de ciclo promedio por mes y transportista |
| 5 | Hoja `Dashboard_Visual` | Contiene mínimo 3 gráficos y 1 tabla de ranking; título visible |
| 6 | Hoja `Analisis_Anomalias` | Contiene 4 análisis comparativos y 2 hipótesis escritas por el participante |
| 7 | Archivo `Reporte_Ejecutivo_Logistico.xlsx` | Resumen ejecutivo completo con 4 secciones; valores numéricos consistentes con KPIs |
| 8 | Consistencia de datos | Los valores del resumen ejecutivo coinciden con los KPIs calculados (tolerancia ±2%) |
| 9 | Guardado en OneDrive | Ambos archivos tienen ícono de sincronización ✅ |
| 10 | Criterios de dashboard | Al menos 4 de 5 criterios de calidad visual se cumplen en cada gráfico |

### Prueba de coherencia de datos

Realiza esta verificación manual para confirmar que los KPIs son coherentes entre sí:

**Prueba 1 — Coherencia OTIF vs. Tardíos:**
En la hoja `TBL_Entregas`, usa la función `COUNTIF` manualmente para contar los registros con `Estado_Entrega = "A tiempo"` y divide entre el total. El resultado debe estar dentro de ±2% del OTIF promedio calculado por Copilot.

```excel
=COUNTIF(TBL_Entregas[Estado_Entrega],"A tiempo")/COUNTA(TBL_Entregas[Estado_Entrega])
```

**Prueba 2 — Coherencia Fill Rate:**
Verifica que la suma de `Unidades_Entregadas` dividida entre la suma de `Unidades_Solicitadas` coincida con el Fill Rate promedio del trimestre calculado por Copilot.

```excel
=SUM(TBL_Entregas[Unidades_Entregadas])/SUM(TBL_Entregas[Unidades_Solicitadas])
```

Si los valores difieren en más del 2%, revisa los prompts utilizados con Copilot y verifica que no haya filtros accidentales aplicados a la tabla.

---

## 8. Resolución de Problemas

### Problema 1: Copilot no genera el tipo de gráfico solicitado o produce un gráfico incorrecto

**Síntomas:**
- Copilot genera un gráfico de pastel cuando se solicitó un gráfico de barras.
- El gráfico generado no tiene línea de referencia al 95%.
- El gráfico muestra datos de solo un mes en lugar de los tres meses del trimestre.
- El botón "Insertar gráfico" no aparece en la respuesta de Copilot.

**Causa probable:**
Copilot interpreta el prompt de forma ambigua cuando no se especifica suficientemente el tipo de visualización, el rango de datos o las columnas a utilizar. Esto es especialmente común cuando la tabla tiene muchas columnas y Copilot no sabe cuáles priorizar. Adicionalmente, Copilot en Excel tiene limitaciones con ciertos tipos de gráficos combinados (doble eje) que pueden no estar disponibles en todas las versiones.

**Solución paso a paso:**

1. **Sé más específico en el prompt.** En lugar de pedir "un gráfico de tendencia", especifica exactamente qué columnas usar:
   ```
   Crea un gráfico de líneas usando la columna 'Mes' en el eje X y el porcentaje de registros con Estado_Entrega = 'A tiempo' en el eje Y. El gráfico debe mostrar los meses enero, febrero y marzo.
   ```

2. **Descompón los gráficos complejos.** Si el gráfico de doble eje no funciona, solicita dos gráficos separados:
   ```
   Crea dos gráficos de barras independientes: el primero con Fill Rate mensual y el segundo con Tasa de Devoluciones mensual. Los usaré lado a lado en el dashboard.
   ```

3. **Verifica que no hay filtros activos** en la tabla `TBL_Entregas`. Ve a **Datos → Borrar** para eliminar cualquier filtro activo que pueda estar limitando los datos que Copilot analiza.

4. **Cierra y reabre el panel de Copilot** si los prompts no producen resultados. A veces el contexto de la conversación se corrompe y reiniciar el panel resuelve el problema.

5. **Alternativa manual:** Si Copilot no puede generar el gráfico correcto después de 3 intentos, crea el gráfico manualmente usando los datos de resumen calculados por Copilot en las hojas de KPIs. Selecciona los datos de la hoja `KPI_OTIF` e inserta el gráfico desde **Insertar → Gráficos recomendados**.

---

### Problema 2: Los valores de KPIs calculados por Copilot son inconsistentes o claramente incorrectos

**Síntomas:**
- El OTIF calculado por Copilot muestra 100% para todos los meses (claramente incorrecto).
- La tasa de devoluciones muestra 0% cuando visualmente se puede ver que hay registros con `Estado_Entrega = "Devuelto"`.
- Los valores de Fill Rate son mayores al 100% (imposible en este contexto).
- Copilot muestra valores diferentes cada vez que se ejecuta el mismo prompt.

**Causa probable:**
Este problema tiene tres causas frecuentes: (1) **Sensibilidad a mayúsculas/minúsculas** en los valores de texto — si los datos tienen `"a tiempo"` (minúsculas) pero el prompt especifica `"A tiempo"` (mayúscula), la condición puede no coincidir. (2) **Tipos de dato inconsistentes** — si la columna `Unidades_Entregadas` tiene algunas celdas con texto (`"N/A"`) mezcladas con números, Copilot puede calcular incorrectamente las sumas. (3) **Filtros o segmentadores activos** que limitan el rango de datos analizado por Copilot.

**Solución paso a paso:**

1. **Verifica los valores exactos en la columna `Estado_Entrega`:**
   ```excel
   =UNIQUE(TBL_Entregas[Estado_Entrega])
   ```
   Esta fórmula muestra todos los valores únicos. Confirma si son exactamente `"A tiempo"`, `"Tardío"` y `"Devuelto"` (con las mayúsculas y tildes exactas).

2. **Ajusta el prompt para usar los valores exactos encontrados:**
   ```
   Calcula el porcentaje de registros donde Estado_Entrega es exactamente igual a 'A tiempo' (con mayúscula en A y minúscula en tiempo). Agrupa por mes usando la columna Fecha_Entrega_Real.
   ```

3. **Limpia los tipos de dato inconsistentes:**
   - Selecciona la columna `Unidades_Entregadas`.
   - Ve a **Datos → Texto en columnas → Finalizar** para forzar la conversión a número.
   - Repite para `Unidades_Solicitadas`.

4. **Elimina todos los filtros activos** con `Datos → Borrar` antes de ejecutar cualquier prompt de cálculo.

5. **Valida con fórmulas manuales** usando las Pruebas de Coherencia descritas en la Sección 7. Si las fórmulas manuales dan resultados correctos pero Copilot no, el problema es del prompt, no de los datos.

6. **Sobre la variabilidad de respuestas:** Es normal que Copilot produzca respuestas ligeramente diferentes en cada ejecución. Si los valores varían en más del 5% entre ejecuciones del mismo prompt, es señal de que el prompt es ambiguo. Agrega más contexto y restricciones al prompt para reducir la variabilidad.

---

## 9. Limpieza del Entorno

Al finalizar el laboratorio, realiza los siguientes pasos de limpieza para mantener el entorno ordenado:

**1. Guarda todos los archivos en OneDrive:**
   - En `Dataset_Logistico_P2.xlsx`: `Ctrl + S` → confirma que el ícono de OneDrive muestra ✅.
   - En `Reporte_Ejecutivo_Logistico.xlsx`: `Ctrl + S` → confirma sincronización.

**2. Organiza los archivos en OneDrive:**
   - Asegúrate de que ambos archivos están en la carpeta `OneDrive - [Nombre Empresa] / Curso_M365_Copilot / Practica2 /`.
   - No muevas ni elimines los archivos; serán referenciados en prácticas posteriores.

**3. Cierra los archivos de Excel** si no vas a continuar inmediatamente con la siguiente práctica.

**4. Opcional — Exportar el dashboard como PDF:**
   Si deseas tener una copia del dashboard para compartir sin necesidad de Excel:
   - En la hoja `Dashboard_Visual`, ve a `Archivo → Exportar → Crear documento PDF/XPS`.
   - Guarda el PDF en la misma carpeta de OneDrive con el nombre `Dashboard_Logistico_Q1_[TuNombre].pdf`.

**5. Cierra el panel de Copilot** haciendo clic en la X del panel lateral para liberar recursos del sistema.

> 📝 **Nota:** No elimines las hojas de KPIs (`KPI_OTIF`, `KPI_FillRate`, `KPI_Devoluciones`, `KPI_CicloOrden`) ni la hoja `Analisis_Anomalias`. Estos datos serán utilizados como referencia en la Práctica 3 cuando se presenten resultados en Teams.

---

## 10. Resumen

### Lo que aprendiste en esta práctica

En este laboratorio aplicaste la metodología de análisis logístico de tres pasos —calcular, visualizar, segmentar— para construir un dashboard operativo completo. Los logros clave de esta práctica incluyen:

| Competencia desarrollada | Herramienta utilizada |
|---|---|
| Cálculo de KPIs logísticos (OTIF, Fill Rate, Devoluciones, Ciclo) | Copilot en Excel con prompts estructurados |
| Generación de visualizaciones ejecutivas (barras, líneas, ranking) | Copilot en Excel + ajustes iterativos |
| Análisis comparativo e identificación de anomalías | Prompts de análisis con Copilot |
| Redacción de resumen ejecutivo orientado a audiencias directivas | Copilot con prompt de formato estructurado |
| Evaluación crítica de visualizaciones y refinamiento iterativo | Criterios de calidad visual + prompts de ajuste |

### Puntos clave para recordar

- **La calidad del prompt determina la calidad del resultado.** Prompts específicos con nombres de columnas exactos, valores de texto precisos y tipos de visualización explícitos producen resultados más confiables.
- **Copilot es no determinístico.** El mismo prompt puede producir resultados ligeramente diferentes en cada ejecución. Siempre valida los resultados con fórmulas manuales antes de incluirlos en reportes ejecutivos.
- **La revisión crítica es obligatoria.** Copilot puede generar visualizaciones técnicamente correctas pero comunicativamente deficientes (escalas distorsionadas, colores confusos, títulos genéricos). La etapa de revisión crítica no es opcional.
- **Los prompts iterativos son la norma, no la excepción.** Raramente el primer prompt produce el resultado perfecto. El flujo de trabajo efectivo con Copilot es: prompt inicial → evaluación → refinamiento → evaluación → resultado final.

### Conexión con la siguiente práctica

En la **Práctica 3**, llevarás los hallazgos de este dashboard a Microsoft Teams y Outlook. Aprenderás a usar Copilot en Teams para preparar presentaciones de resultados, generar resúmenes de reuniones y comunicar alertas operativas a equipos distribuidos. El resumen ejecutivo que generaste en esta práctica será el punto de partida para esas comunicaciones.

---

### Recursos adicionales

| Recurso | Descripción | URL |
|---|---|---|
| Documentación oficial de Copilot en Excel | Guía completa de capacidades y limitaciones | [Microsoft Learn — Copilot en Excel](https://learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-excel) |
| Creación y uso de tablas en Excel | Referencia técnica para tablas estructuradas | [Soporte Microsoft — Tablas en Excel](https://support.microsoft.com/es-es/office/crear-y-dar-formato-a-tablas-e81aa349-b006-4f8a-9806-5af9df0ac664) |
| KPIs logísticos — CSCMP | Definiciones estándar de la industria | [CSCMP Glossary](https://cscmp.org/CSCMP/Educate/SCM_Definitions_and_Glossary_of_Terms.aspx) |
| Métricas de cadena de suministro | Guía práctica de indicadores logísticos | [Inbound Logistics — Supply Chain Metrics](https://www.inboundlogistics.com/articles/supply-chain-metrics-that-matter/) |
| Mejores prácticas de visualización de datos | Principios de diseño para dashboards ejecutivos | [Microsoft Power BI — Guías de visualización](https://learn.microsoft.com/es-es/power-bi/visuals/power-bi-visualization-best-practices) |

---

*Fin del Laboratorio 02-00-01 — Práctica 2: Generación Automatizada de Dashboards y Resúmenes Operativos*

---
LAB_END---

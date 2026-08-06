# Práctica 2 — Generación Automatizada de Dashboards y Resúmenes Operativos

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Gerentes de operaciones, coordinadores de tráfico, líderes de almacén y analistas de cadena de suministro. |
| **Tecnologías** | Microsoft Copilot Chat (M365 / Web), Microsoft Word y Microsoft Excel. |
| **Enfoque** | Análisis de tendencias de transporte/inventario, síntesis ejecutiva en Word y generación de prototipos visuales de dashboards. |

---

## 2. Descripción Corta

En este laboratorio de 90 minutos, los participantes utilizarán Microsoft Copilot Chat para transformar volúmenes de datos históricos de despacho y recepción en dashboards ejecutivos e informes gerenciales de alto impacto. Mediante un flujo avanzado estructurado en 6 fases (Generación, Agregación de KPIs, Análisis de Tendencias, Generación Gráfica, Redacción del Informe Ejecutivo en Word y Reto Autónomo Guíado), el estudiante construirá un tablero de control visual en Excel y redactará un reporte profesional para la toma de decisiones.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Consolidar e interpretar KPIs clave de rendimiento** (On-Time In-Full, tiempos de ciclo, ocupación de flota y costos por tonelada) mediante Copilot Chat.
* **Detectar patrones y tendencias operativas** en series de datos de transporte e inventario.
* **Generar maquetas y prototipos visuales de Dashboards** ejecutivos solicitando imágenes directamente en Copilot Chat.
* **Redactar informes ejecutivos formalizados en Microsoft Word** estructurando hallazgos analíticos, justificantes operativos y recomendaciones estratégicas para la gerencia.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot Chat** (con capacidad de generación de imágenes integrada).
* Aplicación de **Microsoft Excel** abierta.
* Aplicación de **Microsoft Word** abierta.

---

## 5. Procedimiento Paso a Paso

### Fase 1: Generación del Histórico Operativo Multivariable

Para simular una operación realista, generaremos un dataset sintético que represente un mes de movimientos de distribución, incluyendo volúmenes, entregas a tiempo y costos.

1. Abra la interfaz de **Microsoft Copilot Chat**.
2. Copie y ejecute el siguiente prompt:

```
Actúa como un Analista Senior de Cadena de Suministro. Genera un dataset simulado en una tabla Markdown con 12 filas que represente el comportamiento de 4 zonas de distribución (Norte, Sur, Centro, Occidente) durante los últimos 3 meses.

Las columnas deben ser:
- Mes
- Zona_Distribucion
- Envíos_Totales
- Entregas_A_Tiempo (OTIF %)
- Costo_Flete_USD
- Tiempo_Promedio_Descarga_Min

Asegúrate de incluir tendencias visibles: por ejemplo, que la zona Norte tenga mayor volumen pero tiempos de descarga altos, y que la zona Sur muestre una caída en el % de entregas a tiempo en el último mes.
```

3. Copie la tabla generada para utilizarla en los siguientes pasos.

---

### Fase 2: Agregación de Datos y Cálculo de KPIs Clave

Transformaremos las filas operativas en indicadores consolidados (KPIs) de nivel gerencial en Excel.

1. En la misma ventana de Copilot Chat, ejecute el siguiente prompt:

```
Actúa como un Especialista en Business Intelligence para Logística. Toma la tabla de datos de la Fase 1 y calcula los siguientes indicadores consolidados por Zona_Distribucion:

1. Promedio general de Entregas a Tiempo (% OTIF) por zona.
2. Costo Total de Flete (USD) acumulado por zona.
3. Costo promedio por envío (Costo_Flete_USD / Envíos_Totales).
4. Zona con el peor tiempo de descarga promedio.

Presenta estos KPIs en una tabla resumida y clara de nivel ejecutivo.
```

2. Traslade estos datos consolidados a un libro de Excel y guarde el archivo como `Dashboard_Operativo_Logistica.xlsx`.

---

### Fase 3: Análisis de Tendencias y Detección de Ineficiencias

Identificaremos cuellos de botella y desviaciones operativas analizando las variaciones mensuales.

1. Ejecute el siguiente prompt en Copilot Chat:

```
Actúa como un Consultor en Optimización de Operaciones. Revisa los datos de las Fases 1 y 2 y redacta un diagnóstico analítico que responda:

1. ¿Qué zona presentó el deterioro más crítico en servicio (% OTIF) y en qué mes ocurrió?
2. ¿Existe alguna correlación entre el Tiempo_Promedio_Descarga_Min y la caída en el % OTIF?
3. ¿Cuál es la zona más eficiente en relación Costo por Envío vs Entregas a Tiempo?

Sintetiza la respuesta en 3 hallazgos clave estructurados con viñetas claras e hipótesis de causas raíz.
```

---

### Fase 4: Generación Visual de la Maqueta del Dashboard (Imagen)

Aprovecharemos las capacidades de generación gráfica directa en Copilot Chat para crear la imagen del prototipo visual del Dashboard ejecutivo que ilustrará nuestro informe formal.

1. Introduzca el siguiente prompt directamente en el chat de Copilot:

```
Crea una imagen de un Dashboard de Control Logístico y Flota con diseño UI/UX moderno, limpio y profesional.

Estilo visual: Tema oscuro (Dark Mode) corporativo con detalles en azul cian y verde lima.
Contenido visual que debe incluir la imagen:
1. Zona superior: 3 tarjetas de KPI destacadas (OTIF 92%, Costo Flete $145K, Tiempo Descarga 45 min) con indicadores de tendencia verde y rojo.
2. Zona central izquierda: Un gráfico de barras verticales con los volúmenes de las zonas Norte, Sur, Centro y Occidente.
3. Zona central derecha: Un gráfico de líneas mostrando la evolución mensual del % OTIF.
4. Zona inferior: Una pequeña tabla de alertas operativas.

Asegúrate de que parezca una pantalla real de un software de inteligencia de negocios logístico.
```

2. Guarde la imagen generada directamente desde el chat de Copilot.

---

### Fase 5: Redacción del Informe Gerencial y Resumen Ejecutivo en Word

Estructuraremos la documentación formal en Microsoft Word, combinando la redacción analítica de la IA con la maqueta gráfica para presentar la propuesta de mejoras a la dirección general.

1. Abra **Microsoft Word** con un documento en blanco.
2. Solicite a Copilot Chat la redacción del reporte ejecutivo formal mediante el siguiente prompt:

```
Actúa como un Director de Operaciones y Cadena de Suministro. Necesito redactar un "Informe Ejecutivo de Desempeño Operativo y Logístico" formal para la Gerencia General en Microsoft Word.

Utilizando los hallazgos y KPIs analizados en las fases anteriores, redacta el documento con la siguiente estructura:
1. **Título del Reporte y Encabezado:** Documento formal con fecha, autor y destinatario.
2. **Resumen Ejecutivo (Executive Summary):** Un párrafo conciso de alto nivel sintetizando el estado de la red logística y las principales desviaciones financieras/operativas.
3. **Análisis por Zona Operativa:** Un desglose narrativo evaluando los KPIs clave de cada región (OTIF %, Costos y Tiempos de Descarga).
4. **Plan de Acción y Recomendaciones:** 3 iniciativas estratégicas directas para solucionar los cuellos de botella detectados en la zona crítica (mencionando tiempos de ejecución y responsables).

Mantén un tono ejecutivo, profesional, persuasivo y libre de rodeos técnicos innecesarios.
```

3. Copie el texto generado por Copilot Chat en su archivo de Word.
4. Inserte la imagen de la maqueta del Dashboard (generada en la Fase 4) justo debajo del Resumen Ejecutivo como soporte gráfico del informe.
5. Guarde el documento como `Informe_Ejecutivo_Logistica.docx`.

---

### Fase 6: Reto de Aplicación Autónoma – Reporte Ejecutivo de Almacén y Retornos

**Escenario del Reto:** La gerencia solicita un reporte de auditoría sobre la recepción en almacén y la tasa de devoluciones (mermas/retornos) del último trimestre.

#### Pistas y Guía para Resolver el Reto:

* **Pista 1 (Construcción del Dataset y Cálculos en Excel):**
  * *Estructura sugerida para el Prompt en Copilot Chat:* Pídele a la IA que cree una tabla sintética con las columnas: `Centro_Distribucion`, `Unidades_Recibidas`, `Unidades_Devueltas` y `Costo_Merca_Dañada`.
  * *Fórmula clave:* Indícale a Copilot que calcule el porcentaje de devolución dividiendo `(Unidades_Devueltas / Unidades_Recibidas) * 100` e identifica cuál almacén representa la mayor pérdida financiera.
  * Guarda estos datos en una nueva pestaña llamada `Reto_Almacen` dentro de tu archivo `Dashboard_Operativo_Logistica.xlsx`.

* **Pista 2 (Generación de la Imagen del Dashboard en Copilot Chat):**
  * *Estructura sugerida para el Prompt:* En el mismo chat, solicita directamente: *"Genera una imagen con el mockup de un dashboard de control de mermas y devoluciones de almacén..."*.
  * *Detalles del prompt:* Pide que el diseño sea en formato "Light Mode" (fondo claro corporativo), con un gráfico circular (pie chart) que muestre los motivos de devolución (daño en transporte, empaque roto, producto equivocado) y tarjetas de KPI con el total de mermas en USD.

* **Pista 3 (Redacción del Informe Final en Word):**
  * Solicita a Copilot Chat que redacte un informe ejecutivo de máximo 1 página para Word titulado *"Auditoría de Devoluciones y Pérdidas en Almacén"*.
  * Abre Microsoft Word, pega el informe redactado por Copilot Chat, inserta la imagen del dashboard de devoluciones que generaste en la Pista 2 y guarda el archivo como `Informe_Mermas_Almacen.docx`.

---

## 6. Conceptos Clave para Recordar

* **OTIF (On-Time In-Full):** Indicador crítico de nivel de servicio que mide el porcentaje de pedidos entregados a tiempo y con la cantidad completa solicitada.
* **Informe Ejecutivo Gerencial:** Documento redactado en Word que sintetiza métricas operativas complejas en narrativa de negocio accesible para directores y toma de decisiones.
* **Generación Nativa de Imágen:** Capacidad de solicitar mockups, diagramas e interfaces visuales directamente en la conversación de Copilot Chat sin cambiar de herramienta.

---

## 7. Resultado Esperado del Estudiante

El portafolio de evidencias de esta práctica debe incluir:

1. **Archivo de Excel (`Dashboard_Operativo_Logistica.xlsx`):**
   * **Pestaña `Datos_KPIs`:** Datos crudos y consolidado de métricas (Pasos 1 y 2).
   * **Pestaña `Reto_Almacen`:** Tabla del reto autónomo con los KPIs de devolución y costo de mercancía dañada (Paso 6).
2. **Archivo de Word (`Informe_Ejecutivo_Logistica.docx`):**
   * Reporte estructurado formalmente con Resumen Ejecutivo, Análisis por Zona y Plan de Acción (Paso 5).
   * Imagen incrustada de la maqueta visual del Dashboard de Control generada en el chat (Paso 4).
3. **Archivo de Word (`Informe_Mermas_Almacen.docx`):**
   * Reporte final del reto autónomo con la imagen del dashboard de mermas incrustada (Paso 6).

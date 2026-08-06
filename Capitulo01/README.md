# Práctica 1 — Diagnóstico de Datos Operativos y Validación de Información

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 60 minutos |
| **Complejidad** | Básica |
| **Audiencia** | Gerentes de operaciones, coordinadores de tráfico, especialistas de almacén y analistas de cadena de suministro. |
| **Tecnologías** | Microsoft Copilot (Chat M365 / Web) y Microsoft Excel. |
| **Enfoque** | Detección de inconsistencias, estandarización de inventarios/embarques y evaluación de calidad de datos operativos. |

---

## 2. Descripción Corta

En este laboratorio de 60 minutos, los participantes utilizarán Microsoft Copilot para transformar datos logísticos desestructurados y con errores en información limpia, confiable y lista para la toma de decisiones. A través de un flujo por fases (Generación, Diagnóstico, Validación y Visualización), el estudiante identificará anomalías en inventarios y rutas de despacho, establecerá reglas de saneamiento y generará un entregable funcional en Excel.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Identificar inconsistencias y errores comunes** en registros de inventario y transporte mediante IA generativa.
* **Aplicar reglas de validación y limpieza** de datos operativos usando prompts analíticos en Copilot.
* **Estandarizar formatos heterogéneos** de unidades de medida, códigos SKUs y tiempos de entrega.
* **Sintetizar diagnósticos de calidad de datos** en un archivo de Excel para su distribución ejecutiva.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot Chat**.
* Aplicación de **Microsoft Excel** abierta.

---

## 5. Procedimiento Paso a Paso

### Fase 1: Generación del Conjunto de Datos Operativos Simulados

Para evaluar la capacidad de diagnóstico de la IA, simularemos un extracto de datos operativos desordenados que contenga inconsistencias típicas de los sistemas WMS/TMS (registros duplicados, formatos heterogéneos y faltantes).

1. Abra la interfaz de **Microsoft Copilot Chat**.
2. Copie y ejecute el siguiente prompt para solicitar la generación de la tabla de prueba:

```
Actúa como un Administrador de Sistemas Logísticos. Genera una tabla de datos simulada en formato de texto plano con 10 filas de registros de inventario y envíos de un almacén central.

La tabla debe incluir las siguientes columnas:
- ID_Envio
- Codigo_SKU
- Descripcion_Producto
- Cantidad_Tarimas
- Peso_Total_KG
- Estado_Entrega
- Fecha_Despacho

Asegúrate de incluir deliberadamente las siguientes inconsistencias para un ejercicio de calidad de datos:
1. Un SKU con formato inconsistente o caracteres extraños.
2. Un registro con peso o cantidad en valores negativos o inverosímiles.
3. Un estado de entrega con error tipográfico (ej. "Entregadooo" o "En Tráncito").
4. Una fecha con formato distinto al resto (ej. AAAA/MM/DD vs DD-MM-AAAA).
5. Un campo obligatorio completamente vacío.

Muestra la tabla en formato Markdown para poder copiarla fácilmente.
```

3. Copie la tabla generada por Copilot y manténgala lista en su portapapeles.

---

### Fase 2: Diagnóstico Operativo e Identificación de Anomalías

En esta fase, utilizará Copilot como un auditor de datos para auditar la tabla simulada y detectar los puntos críticos que ponen en riesgo la operación.

1. En la misma ventana de chat de Copilot, ejecute el siguiente prompt pegando la tabla obtenida en el Paso 1:

```
Actúa como un Auditor de Calidad de Datos Logísticos. Analiza la siguiente tabla de registros de almacén y transporte:

[Pegar aquí la tabla generada en la Fase 1]

Realiza un diagnóstico detallado identificando:
1. Lista de todos los errores, valores atípicos (outliers) e inconsistencias encontradas por columna.
2. El impacto operativo real que generaría cada error si estos datos alimentaran directamente al sistema de gestión de transporte (TMS) o de almacén (WMS).
3. Una clasificación de la severidad del error (Alta, Media, Baja) según el riesgo de retraso o sobrecosto.

Presenta el diagnóstico en una tabla organizada con las columnas: Registro/Fila, Columna Afectada, Error Detectado, Impacto Operativo y Severidad.
```

---

### Fase 3: Validación, Estandarización y Limpieza de Información

Una vez diagnosticadas las fallas, aplicaremos las reglas de negocio para corregir los registros y estandarizar la información a un formato limpio y operable.

1. Ingrese el siguiente prompt en Copilot para ejecutar la transformación de los datos:

```
Actúa como un Especialista en Gobierno de Datos Logísticos. Toma la tabla analizada anteriormente y aplícale las siguientes reglas de negocio y limpieza:

1. Estandariza todos los Códigos_SKU al formato estándar "SKU-XXXX-MX".
2. Corrige los errores tipográficos en la columna Estado_Entrega utilizando solo tres valores válidos: "En Tránsito", "Entregado" o "Pendiente".
3. Corrige o marca para revisión los valores de peso/cantidad negativos o atípicos, reemplazándolos por un valor lógico estimado o la etiqueta "REVISAR".
4. Homogeniza todas las fechas al formato único "DD/MM/AAAA".
5. Completa los campos vacíos con la etiqueta "NO ESPECIFICADO".

Muestra el resultado final en dos partes:
- La tabla de datos 100% corregida y estandarizada.
- Un resumen con los criterios exactos aplicados para la corrección de cada fila.
```

---

### Fase 4: Estructuración y Exportación a Excel para Distribución

Para consolidar el trabajo y poder compartirlo con el equipo de operaciones o la gerencia, trasladaremos la información corregida a un libro de trabajo estructurado.

1. Abra **Microsoft Excel** con un libro en blanco.
2. Solicite a Copilot la estructura de reporte y fórmulas de validación mediante este prompt:

```
Actúa como un Analista de Inteligencia de Negocios en Logística. Necesito pasar la información corregida a un reporte ejecutable en Excel.

Por favor provéeme:
1. Las instrucciones paso a paso para organizar esta información en una hoja llamada "Inventario_Limpio".
2. Las reglas de "Validación de Datos" en Excel que debería configurar en la columna Estado_Entrega para evitar que los operadores vuelvan a ingresar datos erróneos en el futuro.
3. Una fórmula de Excel para alertar automáticamente en color rojo si el Peso_Total_KG supera el límite permitido de 15,000 KG por embarque.
```

3. Copie la tabla limpia de Copilot, péguela en Excel y aplique las recomendaciones de formato y validación indicadas.
4. Guarde el archivo como `Diagnostico_Datos_Logistica.xlsx`.

---

### Fase 5: Reto de Aplicación Autónoma – Auditoría de Rutas y Capacidad

**Escenario del Reto:** La coordinación de tráfico recibió el reporte de ruta de la flota interna del día, pero se sospecha que hay errores en los kilometrajes reportados, unidades duplicadas y estados de ruta inconsistentes.

#### Instrucciones para el Estudiante:
1. **Paso 1 (Generación de Prompt):** Diseñe un prompt en Copilot pidiendo la auditoría de un reporte sintético de 5 rutas de entrega que incluya: ID_Unidad, Ruta, KM_Recorridos, Tiempo_Estimado_Hrs y Estatus.
2. **Paso 2 (Análisis y Corrección):** Solicite a Copilot que identifique si hay un kilometraje imposible para el tiempo asignado (ej. 800 km en 2 horas) y estandarice el estatus a: "En Ruta", "Detenido" o "Completado".
3. **Entregable Final del Reto:** Genere la tabla final corregida en Excel, cree una segunda pestaña llamada `Reto_Rutas` en su archivo `Diagnostico_Datos_Logistica.xlsx` y guarde los cambios finales.

---

## 6. Conceptos Clave para Recordar

* **Calidad de Datos (Data Quality):** Grado en que un conjunto de datos satisface los requisitos de exactitud, completitud, consistencia y oportunidad para los procesos logísticos.
* **Estandarización de Registros:** Proceso de homologar formatos heterogéneos (fechas, SKUs, pesos) a una estructura de datos única compartida por el WMS/TMS.
* **Validación en Origen:** Configuración de controles en las herramientas de captura (como Excel o apps de almacén) para impedir el ingreso de datos erróneos desde la entrada.

---

## 7. Resultado Esperado del Estudiante

El portafolio de evidencias de esta práctica debe incluir:

1. **Archivo de Excel (`Diagnostico_Datos_Logistica.xlsx`)** que contenga:
   * **Pestaña `Inventario_Limpio`:** Tabla procesada, validada y corregida durante los Pasos 1 al 4, con las reglas de formato condicional de Excel aplicadas.
   * **Pestaña `Reto_Rutas`:** Resolución del reto autónomo de la Fase 5 con los datos de transporte auditados y estandarizados para su entrega.

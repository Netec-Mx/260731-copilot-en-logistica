# Práctica 3 — Resolución de Casos Prácticos de Operaciones y Manejo de Crisis

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 60 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Gerentes de operaciones, coordinadores de logística, analistas de riesgo y encargados de servicio al cliente. |
| **Tecnologías** | Microsoft Copilot Chat (M365 / Web), Microsoft Word y Microsoft Excel. |
| **Enfoque** | Evaluación de impacto por cuellos de botella/interrupciones, mitigación de riesgos logísticos y comunicación en crisis. |

---

## 2. Descripción Corta

En este laboratorio de 60 minutos, los participantes utilizarán Microsoft Copilot Chat para gestionar una contingencia crítica en la cadena de suministro. A través de un flujo por fases (Simulación del Incidente, Cuantificación de Impacto, Matriz de Riesgos, Generación Gráfica del Protocolo, Plan de Comunicación en Word y Reto Autónomo Guíado), el estudiante analizará un cuello de botella grave, estructurará un plan de contingencia financiero/operativo y redactará comunicados oficiales para stakeholders internos y externos.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Evaluar el impacto financiero y operativo** de un cuello de botella o interrupción en la cadena de suministro utilizando Copilot Chat.
* **Diseñar matrices de riesgo y planes de contingencia** para mitigar pérdidas por retrasos en entregas.
* **Generar diagramas visuales de protocolos de emergencia** solicitando imágenes directamente en la interfaz de chat.
* **Redactar comunicaciones de crisis formalizadas en Microsoft Word** adaptadas a diferentes audiencias (clientes clave, gerencia general y transportistas).

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot Chat** (con capacidad de generación de imágenes integrada).
* Aplicación de **Microsoft Excel** abierta.
* Aplicación de **Microsoft Word** abierta.

---

## 5. Procedimiento Paso a Paso

### Fase 1: Simulación del Incidente y Detalle de la Contingencia

Simularemos un escenario de crisis real en la red de distribución donde un imprevisto detiene el flujo operativo.

1. Abra la interfaz de **Microsoft Copilot Chat**.
2. Copie y ejecute el siguiente prompt:

```
Actúa como un Gerente de Riesgos Operativos en Logística. Genera la descripción de un caso de crisis hipotético pero realista para una empresa de distribución nacional.

El escenario debe incluir:
1. El incidente central: Un bloqueo carretero prolongado y una falla en el sistema del nodo principal (Hub Central) que afecta a 5 clientes corporativos críticos.
2. Una tabla sintética en Markdown con 5 registros de envíos varados, incluyendo las columnas: `ID_Envio`, `Cliente`, `Valor_Carga_USD`, `Horas_Retraso` y `Penalizacion_Por_Hora_USD`.

Asegúrate de que la suma de las penalizaciones y el valor de la carga representen un riesgo financiero alto.
```

3. Copie la tabla e información generada para trabajar en las siguientes fases.

---

### Fase 2: Cuantificación del Impacto Financiero en Excel

Calculararemos el costo total del retraso y clasificaremos a los clientes prioritarios según el nivel de penalización.

1. En la misma ventana de Copilot Chat, ejecute el siguiente prompt:

```
Actúa como un Analista de Costos Logísticos. Toma la tabla de la Fase 1 y realiza los siguientes cálculos:

1. El monto total de penalización acumulada por cada envío (`Horas_Retraso` * `Penalizacion_Por_Hora_USD`).
2. El porcentaje que representa el riesgo financiero de cada cliente respecto al costo total de la crisis.
3. El orden de prioridad de atención (del 1 al 5) para aplicar rutas alternas o envíos dedicados exprés.

Presenta los resultados en una tabla clara para copiar a Excel.
```

2. Traslade estos cálculos a una hoja en Excel y guarde el archivo como `Gestion_Crisis_Operativa.xlsx`.

---

### Fase 3: Matriz de Mitigación y Protocolo de Contingencia

Diseñaremos un plan de acción preventivo y correctivo para contener el impacto operacional.

1. Ejecute el siguiente prompt en Copilot Chat:

```
Actúa como un Consultor en Manejo de Crisis y Resiliencia Logística. Con base en el incidente analizado, genera una Matriz de Contingencia y Mitigación de Riesgos.

Incluye en una tabla:
1. Tres alternativas tácticas inmediatas (ej. transbordo a unidades menores, uso de rutas de cuota alternas, envíos aéreos parciales).
2. Para cada alternativa: Costo Estimado de Implementación, Tiempo de Respuesta (horas) y % de Reducción del Riesgo.
3. Una recomendación directa sobre cuál opción balancea mejor el costo vs la satisfacción del cliente.
```

---

### Fase 4: Generación Visual del Diagrama de Flujo de Contingencia (Imagen)

Generaremos una representación visual del mapa del protocolo de respuesta rápida que formará parte de nuestro informe oficial.

1. Introduzca el siguiente prompt directamente en el chat de Copilot:

```
Genera una imagen conceptual de una infografía visual que muestre un "Protocolo de Respuesta Rápida ante Crisis Logísticas".

Estilo visual: Diseño visual limpio, moderno y corporativo en esquema de color azul oscuro, naranja de alerta y blanco.
La imagen debe mostrar:
1. Un flujo de 4 pasos representados con íconos claros: Detección del Bloqueo (ícono de alerta), Evaluación Financiera (ícono de calculadora/dólar), Desvío de Ruta (ícono de mapa/camión) y Notificación al Cliente (ícono de mensaje).
2. Flechas conectando cada fase y tarjetas estilizadas para cada paso.
3. Apariencia de un gráfico de procesos profesional de gestión de operaciones.
```

2. Guarde la imagen generada directamente desde la conversación.

---

### Fase 5: Redacción del Kit de Comunicación en Word

Estructuraremos el plan de comunicación oficial para la gerencia y las partes interesadas (stakeholders).

1. Abra **Microsoft Word** con un documento en blanco.
2. Solicite a Copilot Chat la redacción del manual de respuesta ejecutiva con el siguiente prompt:

```
Actúa como un Director de Comunicaciones Corporativas y Operaciones. Redacta un "Kit de Comunicación y Manejo de Crisis Operativa" formal para Microsoft Word.

El documento debe contener:
1. **Comunicado Interno para la Gerencia General:** Resumen ejecutivo breve del estado de la red, impacto económico controlado y plan de contingencia elegido.
2. **Carta Modelo para Clientes Afectados:** Redacción empática, altamente profesional y transparente, explicando la causa de fuerza mayor, las acciones tomadas para mitigar el retraso y la nueva hora estimada de entrega (ETA).
3. **Instrucción Operativa para Transportistas y Almacén:** Lista de 3 directrices claras de actuación inmediata para los conductores y personal de patio.

Mantén un tono de control, liderazgo, firmeza y profesionalismo.
```

3. Copie el texto en su archivo de Word, inserte la imagen del protocolo de respuesta (generada en la Fase 4) debajo del comunicado gerencial y guarde el archivo como `Plan_Comunicacion_Crisis.docx`.

---

### Fase 6: Reto de Aplicación Autónoma – Manejo de Crisis por Cierre Sanitario / Aduanal

**Escenario del Reto:** Un cargamento crítico de insumos importados quedó retenido inesperadamente en la aduana de entrada por una inspección extraordinaria, poniendo en riesgo la línea de producción de un cliente clave que opera bajo el esquema Just-in-Time (JIT).

#### Pistas y Guía para Resolver el Reto:

* **Pista 1 (Cálculo de Impacto y Alternativas en Excel):**
  * *Estructura sugerida para el Prompt:* Solicita a Copilot Chat una tabla simulada que muestre: `Lote_Retenido`, `Insumo`, `Horas_Para_Paro_Planta` y `Costo_Paro_Por_Hora_USD`. Pídele que calcule las pérdidas tras 12 horas de paro.
  * *Ubicación:* Guarda la tabla de análisis en una nueva pestaña llamada `Reto_Aduana` dentro de tu archivo `Gestion_Crisis_Operativa.xlsx`.

* **Pista 2 (Visual del Plan de Evacuación/Contingencia en Chat):**
  * *Estructura sugerida para el Prompt:* En Copilot Chat, solicita directamente: *"Genera una imagen estilizada tipo infografía corporativa que muestre un 'Plan de Rescate Aduanal y Despacho Exprés'..."*.
  * *Detalles:* Pide un estilo claro (Light Mode) con 3 pasos (Liberación Parcial, Flete Aéreo Dedicado y Entrega Preferencial).

* **Pista 3 (Comunicado Urgente en Word):**
  * Pide a Copilot Chat que redacte una *"Notificación de Alerta Temprana de Suministro"* dirigida al Director de Operaciones del cliente afectado, garantizando el suministro mediante una fuente alternativa.
  * Abre Word, pega la notificación, inserta la imagen del plan de rescate que generaste en la Pista 2 y guarda el documento como `Notificacion_Crisis_Aduana.docx`.

---

## 6. Conceptos Clave para Recordar

* **Matriz de Contingencia:** Herramienta de planificación estratégica que define acciones preconcebidas para neutralizar los efectos de un evento imprevisto en la cadena de suministro.
* **Comunicación de Crisis (Stakeholder Management):** Estrategia de información oportuna y transparente para mitigar el daño reputacional y preservar la confianza comercial durante una falla operativa.
* **Cuantificación del Riesgo (Cost of Delay):** Cálculo del impacto monetario real generado por cada unidad de tiempo perdida en una interrupción logística.

---

## 7. Resultado Esperado del Estudiante

El portafolio de evidencias de esta práctica debe incluir:

1. **Archivo de Excel (`Gestion_Crisis_Operativa.xlsx`):**
   * **Pestaña `Analisis_Penalizaciones`:** Datos del incidente y cálculo del impacto económico por retrasos (Fase 2).
   * **Pestaña `Reto_Aduana`:** Tabla del reto autónomo con los costos de paro de planta y evaluación del insumo retenido (Fase 6).
2. **Archivo de Word (`Plan_Comunicacion_Crisis.docx`):**
   * Reporte estructurado con Comunicado Interno, Carta Modelo para Clientes e Instrucción Operativa (Fase 5).
   * Imagen incrustada del diagrama del protocolo de respuesta generado en el chat (Fase 4).
3. **Archivo de Word (`Notificacion_Crisis_Aduana.docx`):**
   * Documento de alerta temprana del reto autónomo con la imagen de rescate aduanal incrustada (Fase 6).

# Práctica 3 — Resolución de Casos Prácticos de Operaciones y Manejo de Crisis

## 1. Metadatos

| Campo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Aplicar (*Apply*) |
| **Módulo** | 3 — Operaciones y Manejo de Crisis con Microsoft 365 Copilot |
| **Práctica número** | 3 de 4 |
| **Herramientas principales** | Microsoft Teams + Copilot · Microsoft Outlook + Copilot · Microsoft 365 Copilot Chat |

---

## 2. Descripción General

Esta práctica sitúa al participante en el rol de **coordinador logístico de guardia** durante tres escenarios simultáneos de crisis operativa: un cuello de botella en almacén, una falla masiva de entregas a un cliente corporativo y un riesgo inminente de quiebre de stock. Aplicando los conceptos de detección de cuellos de botella y áreas de riesgo crítico estudiados en la Lección 3.1, los participantes utilizarán Microsoft Copilot en Teams y Outlook para diagnosticar, comunicar y escalar cada situación con evidencia estructurada. El énfasis está en la **calidad de la redacción técnica logística**: precisión, tono profesional, estructura clara y accionabilidad de cada comunicación generada.

---

## 3. Objetivos de Aprendizaje

Al completar esta práctica, el participante será capaz de:

- [ ] **Aplicar** Copilot en Teams para resumir hilos de conversación de crisis, identificar el punto crítico de falla y generar un plan de acción de 5 pasos con evidencia operativa.
- [ ] **Redactar** comunicaciones profesionales de alto impacto (disculpa formal a cliente, escalación interna, alerta a proveedor) utilizando Copilot en Outlook con ajuste de tono y estructura.
- [ ] **Diagnosticar** riesgos de quiebre de stock a partir de datos tabulares usando Copilot y traducir el hallazgo en un memo ejecutivo accionable.
- [ ] **Construir** un protocolo personal de respuesta a crisis logística que integre Copilot como herramienta de apoyo en la toma de decisiones bajo presión.

---

## 4. Prerrequisitos

### 4.1 Conocimiento Previo

| Área | Nivel requerido |
|---|---|
| Prácticas 1 y 2 del curso completadas (o experiencia equivalente con Copilot en Excel) | Obligatorio |
| Conceptos de cuello de botella y KPIs logísticos (Lección 3.1) | Obligatorio |
| Protocolos básicos de comunicación en crisis: escalación, notificación a cliente, coordinación interna | Recomendado |
| Uso básico de Microsoft Teams y Outlook (envío de mensajes, búsqueda en hilos) | Obligatorio |

### 4.2 Acceso y Licencias

| Recurso | Estado requerido |
|---|---|
| Licencia activa de **Microsoft 365 Copilot** (no Copilot Free) | ✅ Verificado antes de iniciar |
| Microsoft Teams (nueva versión ≥ 2.1) con Copilot habilitado en chats y canales | ✅ Instalado y con sesión activa |
| Microsoft Outlook para Microsoft 365 (escritorio) con Copilot visible en la interfaz de redacción | ✅ Configurado con cuenta corporativa |
| Archivos de escenarios de crisis proporcionados por el instructor | ✅ Descargados y disponibles localmente |
| Acceso a **Microsoft 365 Copilot Chat** (https://m365.cloud.microsoft/chat) | ✅ Accesible desde el navegador |

> **⚠️ Nota crítica:** Sin licencia activa de Microsoft 365 Copilot, ninguno de los pasos de esta práctica puede ejecutarse. Si al abrir Teams u Outlook no aparece el botón o panel de Copilot, detente y contacta al instructor antes de continuar.

---

## 5. Entorno de Laboratorio

### 5.1 Requisitos de Hardware

| Componente | Mínimo | Recomendado |
|---|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| RAM | 8 GB | 16 GB |
| Almacenamiento libre | 2 GB (archivos de escenarios + exportaciones) | 5 GB |
| Pantalla | 1366 × 768 | 1920 × 1080 |
| Conectividad | 10 Mbps bajada, latencia < 100 ms | 25 Mbps, latencia < 50 ms |
| Audio | Micrófono + altavoces/auriculares funcionales | Auriculares con cancelación de ruido |

### 5.2 Software y Versiones

| Aplicación | Versión mínima | Verificación rápida |
|---|---|---|
| Microsoft Teams | 2.1 (nueva versión) | `Ayuda > Acerca de Teams` |
| Microsoft Outlook | Microsoft 365, canal mensual 2308+ | `Archivo > Cuenta de Office` |
| Microsoft Edge | 115+ | `edge://version` |
| Microsoft 365 Copilot Chat | Versión web actual | https://m365.cloud.microsoft/chat |

### 5.3 Archivos de Escenarios Requeridos

El instructor debe haber distribuido los siguientes archivos antes de iniciar la práctica. Guárdalos en una carpeta local denominada `Lab03_Crisis`:

```
Lab03_Crisis/
├── Escenario_A_Hilo_Teams_Almacen.txt        ← Hilo simulado de conversación de Teams
├── Escenario_B_Pedidos_No_Entregados.xlsx    ← Tabla de 15 pedidos fallidos
├── Escenario_C_Inventario_SKU_Riesgo.xlsx    ← Dataset de inventario con 40 SKUs
└── Plantilla_Protocolo_Crisis.docx           ← Plantilla para el entregable final
```

### 5.4 Configuración Inicial (5 minutos)

Antes de iniciar los escenarios, completa estos pasos de verificación:

```
1. Abre Microsoft Teams → verifica que el ícono de Copilot (✨) aparece
   en la barra lateral izquierda y dentro del chat de práctica del curso.

2. Abre Microsoft Outlook → crea un nuevo correo borrador → verifica que
   aparece el botón "Borrador con Copilot" o el panel de Copilot en la
   cinta de opciones de redacción.

3. Abre el navegador Edge → navega a:
   https://m365.cloud.microsoft/chat
   → confirma que puedes escribir prompts y recibir respuestas.

4. Abre la carpeta Lab03_Crisis y confirma que los cuatro archivos
   están presentes y no están bloqueados por el sistema de archivos
   (clic derecho → Propiedades → desbloquear si aplica).

5. Abre Escenario_B_Pedidos_No_Entregados.xlsx y
   Escenario_C_Inventario_SKU_Riesgo.xlsx en Excel para verificar
   que los datos son legibles y no requieren habilitación de macros.
```

> **Tiempo de configuración estimado:** 5 minutos. Si alguna verificación falla, notifica al instructor antes de avanzar.

---

## 6. Procedimiento Paso a Paso

La práctica está dividida en **tres escenarios secuenciales** más un **entregable integrador**. Trabaja cada escenario en orden; no avances al siguiente sin completar el anterior.

---

### Escenario A: Cuello de Botella en Almacén — Diagnóstico con Copilot en Teams

**Tiempo estimado:** 25 minutos

**Contexto operativo:** Son las 14:30 del martes. El canal `#operaciones-almacen-norte` de Teams lleva 3 horas activo con mensajes de 7 operadores reportando retrasos en el área de *picking*. Tu gerente te pide un diagnóstico en 15 minutos para decidir si activa el protocolo de hora extra.

---

#### Paso A-1: Acceder al Hilo Simulado de Teams

**Objetivo:** Cargar el contexto del escenario en Copilot para que pueda procesarlo.

**Instrucciones:**

1. Abre el archivo `Escenario_A_Hilo_Teams_Almacen.txt` desde la carpeta `Lab03_Crisis`.
2. Lee el hilo completo (aproximadamente 18 mensajes) para familiarizarte con los actores y los eventos reportados.
3. En Microsoft Teams, navega al canal o chat designado por el instructor para esta práctica (por ejemplo, `Lab03 - Escenario A`).
4. Si el instructor ha cargado el hilo simulado directamente en Teams como mensajes, ubícate en ese canal. Si no, utiliza **Microsoft 365 Copilot Chat** (https://m365.cloud.microsoft/chat) para el análisis, pegando el contenido del `.txt` como contexto.
5. Abre el panel de Copilot en Teams haciendo clic en el ícono **✨ Copilot** en la esquina superior derecha del canal o chat.

**Resultado esperado:** El panel de Copilot se abre en el lateral derecho de la pantalla, mostrando el campo de entrada de prompts y, si hay mensajes en el canal, la opción de resumir la conversación.

**Verificación:** El panel de Copilot muestra el texto *"¿En qué puedo ayudarte?"* o similar, y está vinculado al contexto del canal correcto.

---

#### Paso A-2: Resumir la Conversación de Crisis

**Objetivo:** Usar Copilot para sintetizar 18 mensajes dispersos en un resumen ejecutivo estructurado.

**Instrucciones:**

1. En el panel de Copilot de Teams (o en Copilot Chat si usas la alternativa web), ingresa el siguiente prompt. Si usas Copilot Chat, primero pega el contenido completo del hilo como contexto y luego el prompt:

```
Prompt A-2:

Eres un analista de operaciones logísticas. A continuación tienes
un hilo de conversación del equipo de almacén durante una situación
de retraso operativo.

[PEGAR AQUÍ EL CONTENIDO DEL ARCHIVO Escenario_A_Hilo_Teams_Almacen.txt]

Por favor:
1. Resume la conversación en no más de 150 palabras, indicando
   qué está ocurriendo, desde qué hora y quiénes están involucrados.
2. Identifica el punto crítico de falla: ¿en qué etapa del proceso
   se origina el retraso y cuál es la causa más probable?
3. Lista los acuerdos o compromisos que los operadores ya tomaron
   en el hilo, si los hay.
```

2. Envía el prompt y espera la respuesta (típicamente 10–20 segundos).
3. Lee la respuesta completa. Si alguna sección está incompleta o ambigua, usa este prompt de seguimiento:

```
Prompt de seguimiento A-2b:

La causa raíz que identificaste, ¿está respaldada por datos
concretos del hilo (horas, volúmenes, nombres de operadores)?
Por favor, cita las evidencias específicas del texto.
```

**Resultado esperado:** Copilot genera:
- Un resumen ejecutivo de 100–150 palabras que menciona el área afectada, el horario de inicio y los actores clave.
- Una identificación del punto crítico de falla (por ejemplo: escasez de montacargas en el pasillo 4, acumulación de WIP en zona de consolidación, etc.).
- Una lista de 2–4 acuerdos previos mencionados en el hilo.

**Verificación:** El resumen menciona al menos 3 datos verificables presentes en el hilo original (hora, operador, área). Si la respuesta es genérica y no cita el hilo, reformula el prompt con más contexto explícito.

---

#### Paso A-3: Generar el Plan de Acción de 5 Pasos

**Objetivo:** Traducir el diagnóstico en un plan de acción inmediata que el gerente pueda aprobar en minutos.

**Instrucciones:**

1. Basándote en la respuesta del Paso A-2, ingresa el siguiente prompt:

```
Prompt A-3:

Con base en el diagnóstico anterior, genera un plan de acción
inmediata de exactamente 5 pasos para resolver el cuello de botella
identificado en el área de almacén.

Cada paso debe incluir:
- Acción específica (qué hacer)
- Responsable sugerido (rol, no nombre personal)
- Tiempo de ejecución estimado
- Indicador de éxito (cómo saber que el paso funcionó)

El tono debe ser operativo y directo. El plan será presentado al
Gerente de Operaciones en los próximos 10 minutos.
```

2. Revisa el plan generado. Evalúa cada paso con los siguientes criterios:
   - ¿Es la acción específica y ejecutable, o es vaga?
   - ¿El responsable es un rol realista dentro de un almacén?
   - ¿El tiempo de ejecución es razonable para una crisis activa?
3. Si algún paso no cumple los criterios, usa este prompt de refinamiento:

```
Prompt de refinamiento A-3b:

El paso [número] no es suficientemente específico. Por favor,
reescríbelo con una acción más concreta y un indicador de éxito
medible, considerando que el almacén maneja 1,200 pedidos diarios
y opera con 3 turnos de 8 horas.
```

4. Copia el plan de acción final en un documento de texto o en la sección correspondiente de `Plantilla_Protocolo_Crisis.docx`.

**Resultado esperado:** Un plan de 5 pasos estructurado con acción, responsable, tiempo e indicador de éxito para cada uno. El plan debe ser coherente con el diagnóstico del Paso A-2 y no contradecir la información del hilo.

**Verificación:** Comparte el plan con un compañero de práctica o con el instructor. ¿Podría un gerente aprobarlo y ejecutarlo sin pedir aclaraciones? Si la respuesta es no, identifica qué paso necesita más especificidad.

---

### Escenario B: Crisis de Entrega — Redacción Profesional con Copilot en Outlook

**Tiempo estimado:** 30 minutos

**Contexto operativo:** Un cliente corporativo (Distribuidora Andina S.A.) reporta que 15 pedidos programados para entrega ayer no llegaron. El cliente amenaza con activar penalizaciones contractuales. Necesitas redactar tres comunicaciones en los próximos 20 minutos: (1) una disculpa formal al cliente con plan de recuperación, (2) una escalación interna al equipo de operaciones y (3) una alerta al proveedor de transporte responsable.

---

#### Paso B-1: Analizar los Datos de Pedidos Fallidos

**Objetivo:** Obtener un diagnóstico rápido de los 15 pedidos antes de redactar las comunicaciones.

**Instrucciones:**

1. Abre `Escenario_B_Pedidos_No_Entregados.xlsx` en Excel.
2. Navega a **Microsoft 365 Copilot Chat** (https://m365.cloud.microsoft/chat) en Edge.
3. Haz clic en el ícono de adjuntar archivo (📎) o usa la opción de cargar archivo, y sube `Escenario_B_Pedidos_No_Entregados.xlsx`.

> **Nota:** Si la carga directa de archivos no está disponible en tu tenant, copia los datos de la tabla de Excel y pégalos directamente en el campo de texto de Copilot Chat.

4. Ingresa el siguiente prompt:

```
Prompt B-1:

Analiza la tabla de pedidos fallidos adjunta. Por favor:

1. Indica el rango de fechas de entrega comprometida para estos
   15 pedidos.
2. Identifica si hay un patrón: ¿los pedidos fallidos se concentran
   en una zona geográfica, un carrier específico o un tipo de
   producto?
3. Calcula el valor total aproximado de los pedidos afectados
   si la columna de valor está disponible.
4. Señala cuáles son los 3 pedidos de mayor urgencia basándote
   en el criterio que consideres más relevante (justifica tu
   criterio).

Presenta los resultados en formato de lista estructurada, no
como párrafo continuo.
```

5. Guarda o copia los resultados del análisis; los necesitarás para los tres correos del Paso B-2.

**Resultado esperado:** Copilot presenta un análisis estructurado con: rango de fechas, patrón identificado (geográfico, por carrier o por producto), valor total estimado y los 3 pedidos prioritarios con justificación.

**Verificación:** Revisa manualmente en Excel que al menos 2 de los datos citados por Copilot (por ejemplo, el nombre del carrier o la zona geográfica más afectada) coincidan con los datos reales de la tabla.

---

#### Paso B-2a: Redactar la Disculpa Formal al Cliente

**Objetivo:** Generar una comunicación profesional de disculpa y plan de recuperación dirigida al cliente corporativo.

**Instrucciones:**

1. Abre Microsoft Outlook y crea un **nuevo correo electrónico** (botón `Nuevo correo` o `Ctrl + N`).
2. En el campo `Para:`, escribe la dirección del instructor o la dirección de práctica designada (no envíes a un cliente real).
3. Haz clic en el botón **"Borrador con Copilot"** en la cinta de opciones (o en el ícono de Copilot ✨ dentro del área de redacción).
4. En el panel de Copilot, ingresa el siguiente prompt:

```
Prompt B-2a:

Redacta un correo electrónico formal de disculpa dirigido al
Sr. Carlos Mendoza, Director de Compras de Distribuidora Andina S.A.

Contexto: 15 pedidos que debían entregarse ayer no fueron
despachados por un fallo en la coordinación con el carrier
[nombre del carrier identificado en el análisis B-1].
Los pedidos tienen un valor aproximado de [valor calculado en B-1].

El correo debe:
1. Reconocer el fallo sin evasivas y asumir responsabilidad.
2. Explicar brevemente la causa (sin excusas, solo hechos).
3. Presentar un plan de recuperación concreto con fechas
   comprometidas (usa: reentrega prioritaria en 24 horas para
   los 3 pedidos urgentes; resto en 48 horas).
4. Ofrecer una compensación simbólica (descuento del 5 % en
   la próxima factura).
5. Incluir un punto de contacto directo (nombre: Ana Torres,
   Gerente de Cuenta, teléfono: +57 310 000 0000).

Tono: profesional, empático, directo. Extensión: máximo 300 palabras.
Formato: párrafos cortos, sin bullets en el cuerpo principal.
```

5. Revisa el borrador generado. Si el tono no es el adecuado, usa la función **"Ajustar tono"** de Copilot (si está disponible en tu versión) o ingresa:

```
Prompt de ajuste B-2a-tono:

El correo suena demasiado formal/frío. Por favor, manteniendo
la profesionalidad, agrega una frase de apertura que muestre
empatía genuina con el impacto que esto tuvo en las operaciones
del cliente.
```

6. Guarda el borrador (no lo envíes aún). Anota en tu plantilla de protocolo el tiempo que tomó generar y ajustar el correo.

**Resultado esperado:** Un borrador de correo de 200–300 palabras que: reconoce el error, explica la causa, ofrece un plan de recuperación con fechas específicas, menciona la compensación y proporciona contacto directo.

**Verificación:** Lee el correo en voz alta. ¿Generaría confianza si lo recibieras como cliente? ¿Todas las fechas y datos son coherentes con el análisis del Paso B-1?

---

#### Paso B-2b: Redactar la Escalación Interna al Equipo de Operaciones

**Objetivo:** Comunicar la crisis al equipo interno con el nivel de urgencia y detalle técnico apropiados.

**Instrucciones:**

1. Crea un **nuevo correo** en Outlook.
2. Abre el panel de Copilot y usa el siguiente prompt:

```
Prompt B-2b:

Redacta un correo de escalación interna urgente dirigido al
equipo de Operaciones (Para: equipo-operaciones@empresa.com)
con copia al Gerente de Logística.

Asunto: [URGENTE] Fallo de entrega — 15 pedidos Distribuidora
Andina — Acción requerida en 2 horas

Contexto: Los mismos 15 pedidos fallidos del análisis anterior.

El correo debe:
1. Declarar el nivel de urgencia desde la primera línea
   (usar escala: CRÍTICO / ALTO / MEDIO).
2. Resumir el impacto: cliente afectado, número de pedidos,
   valor aproximado, riesgo de penalización contractual.
3. Solicitar acciones específicas a operaciones:
   a) Confirmar disponibilidad de carrier alternativo en 1 hora.
   b) Priorizar los 3 pedidos urgentes para despacho inmediato.
   c) Enviar actualización de estado cada 2 horas.
4. Indicar el plazo de respuesta esperado.

Tono: directo, técnico, orientado a la acción. Sin lenguaje
emocional. Extensión: máximo 200 palabras.
```

3. Revisa que el correo no contenga información confidencial del cliente que no deba circular internamente.
4. Guarda el borrador.

**Resultado esperado:** Un correo de escalación interna conciso (150–200 palabras) con nivel de urgencia declarado, impacto cuantificado y tres acciones específicas con plazos.

**Verificación:** ¿El correo puede ser leído y comprendido completamente en menos de 30 segundos? ¿Las acciones solicitadas son ejecutables por el equipo de operaciones?

---

#### Paso B-2c: Redactar la Alerta al Proveedor de Transporte

**Objetivo:** Comunicar formalmente la falla al carrier responsable, documentando el incidente para efectos contractuales.

**Instrucciones:**

1. Crea un **nuevo correo** en Outlook.
2. Abre el panel de Copilot y usa el siguiente prompt:

```
Prompt B-2c:

Redacta una alerta formal dirigida al representante comercial
del carrier [nombre del carrier del análisis B-1].

Asunto: Notificación formal de incumplimiento SLA —
[fecha de ayer] — Referencia: Distribuidora Andina

El correo debe:
1. Notificar formalmente el incumplimiento del SLA de entrega
   para 15 pedidos (citar número de guías si están disponibles
   en los datos).
2. Solicitar un informe de causa raíz en un plazo de 4 horas.
3. Indicar que el incidente queda registrado como antecedente
   para la evaluación de desempeño del carrier (ciclo mensual).
4. Solicitar confirmación de capacidad para reentrega en 24 horas.
5. Incluir una cláusula de advertencia: si no hay respuesta en
   4 horas, se activará el carrier de respaldo.

Tono: formal, firme, sin agresividad. El carrier es un socio
comercial a largo plazo. Extensión: máximo 250 palabras.
```

3. Revisa que el tono sea firme pero profesional; Copilot a veces genera textos demasiado agresivos en contextos de reclamo.
4. Si el tono es inadecuado, usa:

```
Prompt de ajuste B-2c-tono:

El correo suena amenazante. Por favor, mantén la firmeza y
los plazos, pero reformula las frases de advertencia para
que sean declarativas (hechos y consecuencias) en lugar de
amenazas directas.
```

5. Guarda el borrador.

**Resultado esperado:** Un correo formal de 200–250 palabras que documenta el incumplimiento, solicita causa raíz, confirma capacidad de reentrega y establece consecuencias claras sin deteriorar la relación comercial.

**Verificación:** Compara los tres correos (B-2a, B-2b, B-2c) lado a lado. ¿Son coherentes entre sí en cuanto a fechas, números de pedidos y compromisos? ¿El tono de cada uno es apropiado para su audiencia?

---

### Escenario C: Riesgo de Inventario Crítico — Diagnóstico y Memo Ejecutivo

**Tiempo estimado:** 20 minutos

**Contexto operativo:** El sistema de gestión de almacén (WMS) generó una alerta de inventario esta mañana. Tienes un dataset de 40 SKUs con niveles actuales, demanda promedio diaria y días de cobertura. Tu Director de Operaciones necesita un memo ejecutivo en 15 minutos identificando los 3 SKUs de mayor riesgo y las acciones recomendadas.

---

#### Paso C-1: Analizar el Dataset de Inventario

**Objetivo:** Identificar los SKUs con mayor riesgo de quiebre de stock usando Copilot.

**Instrucciones:**

1. Abre `Escenario_C_Inventario_SKU_Riesgo.xlsx` en Excel.
2. Navega a **Microsoft 365 Copilot Chat** y sube el archivo (o copia los datos).
3. Ingresa el siguiente prompt de diagnóstico:

```
Prompt C-1:

Eres un analista de inventarios logísticos. Analiza el dataset
de SKUs adjunto.

Por favor:
1. Calcula los días de cobertura restantes para cada SKU
   (stock actual / demanda diaria promedio) si esta columna
   no existe ya.
2. Identifica los 3 SKUs con menor días de cobertura.
3. Para cada uno de esos 3 SKUs, indica:
   a) Nombre o código del SKU
   b) Stock actual
   c) Días de cobertura calculados
   d) Nivel de riesgo: CRÍTICO (< 3 días), ALTO (3–7 días),
      MEDIO (7–14 días)
   e) Si hay algún dato adicional en la tabla que sugiera
      por qué el stock está bajo (tendencia de demanda,
      proveedor, categoría)
4. ¿Existe algún patrón común entre los SKUs de mayor riesgo
   (mismo proveedor, misma categoría, misma zona de almacén)?

Presenta los resultados en una tabla resumen.
```

4. Valida los resultados manualmente en Excel: verifica que los días de cobertura calculados por Copilot para al menos 2 SKUs sean correctos (stock actual ÷ demanda diaria).

> **Recordatorio de la Lección 3.1:** La calidad del diagnóstico depende directamente de la precisión del prompt y de la calidad de los datos. Si el dataset tiene celdas vacías o valores atípicos, Copilot puede generar cálculos incorrectos. Valida siempre los resultados numéricos.

**Resultado esperado:** Una tabla con los 3 SKUs de mayor riesgo, incluyendo stock actual, días de cobertura, nivel de riesgo y posible patrón común.

**Verificación:** Calcula manualmente los días de cobertura del SKU identificado como el más crítico. ¿Coincide con el resultado de Copilot? Si hay discrepancia > 10 %, identifica la causa (¿datos faltantes? ¿fórmula diferente?).

---

#### Paso C-2: Redactar el Memo Ejecutivo de Alerta

**Objetivo:** Convertir el diagnóstico técnico en una comunicación ejecutiva accionable.

**Instrucciones:**

1. Abre **Microsoft 365 Copilot Chat** o el panel de Copilot en Outlook (nuevo correo en modo borrador).
2. Ingresa el siguiente prompt:

```
Prompt C-2:

Redacta un memo ejecutivo de alerta de inventario crítico
dirigido al Director de Operaciones.

Encabezado del memo:
- Para: Director de Operaciones
- De: Coordinador de Inventarios
- Fecha: [fecha de hoy]
- Asunto: ALERTA CRÍTICA — Riesgo de Quiebre de Stock —
  3 SKUs en Zona Roja
- Clasificación: URGENTE

Contenido del memo:
1. Párrafo de apertura (2–3 oraciones): declara la situación
   y el nivel de urgencia.
2. Tabla de los 3 SKUs críticos con: código, días de cobertura,
   nivel de riesgo y acción recomendada para cada uno.
3. Análisis de impacto (3–4 oraciones): ¿qué ocurre si no se
   actúa en las próximas 24 horas? Menciona impacto en
   nivel de servicio, posibles pedidos afectados y costo
   de quiebre estimado (puedes usar un estimado genérico
   si no tienes el dato exacto).
4. Recomendaciones inmediatas (lista de 3 acciones con
   responsable y plazo):
   - Acción 1: contactar proveedor para orden de emergencia
   - Acción 2: activar stock de seguridad de otra ubicación
     (si aplica)
   - Acción 3: alertar al equipo comercial para gestionar
     expectativas de clientes
5. Cierre: solicitar aprobación para proceder con las acciones
   en un plazo de 2 horas.

Tono: ejecutivo, conciso, orientado a la decisión. El director
necesita aprobar o rechazar las acciones en minutos.
Extensión total: máximo 400 palabras.
```

3. Revisa el memo. Verifica que:
   - Los datos de los 3 SKUs en la tabla del memo coincidan con los resultados del Paso C-1.
   - El análisis de impacto sea realista y no exagerado.
   - Las recomendaciones sean ejecutables dentro del plazo indicado.
4. Copia el memo final en `Plantilla_Protocolo_Crisis.docx` en la sección de Escenario C.

**Resultado esperado:** Un memo ejecutivo estructurado de 300–400 palabras con tabla de SKUs críticos, análisis de impacto y tres recomendaciones con responsable y plazo.

**Verificación:** ¿Podría el Director de Operaciones tomar una decisión de aprobación o rechazo basándose únicamente en este memo, sin necesidad de consultar el dataset original? Si la respuesta es no, identifica qué información falta.

---

### Entregable Integrador: Protocolo Personal de Respuesta a Crisis

**Tiempo estimado:** 15 minutos

**Objetivo:** Sintetizar las lecciones aprendidas en los tres escenarios en un protocolo personal reutilizable.

---

#### Paso D-1: Construir el Protocolo con Copilot

**Instrucciones:**

1. Abre `Plantilla_Protocolo_Crisis.docx` con toda la información recopilada en los escenarios A, B y C.
2. Navega a **Microsoft 365 Copilot Chat** y usa el siguiente prompt:

```
Prompt D-1:

Con base en los tres escenarios de crisis logística que resolví
hoy (cuello de botella en almacén, falla de entrega a cliente
corporativo y riesgo de quiebre de stock), ayúdame a construir
un protocolo personal de respuesta a crisis logística.

El protocolo debe incluir:

1. PRINCIPIOS RECTORES (3–5 principios breves): qué valores
   o criterios deben guiar la toma de decisiones bajo presión.

2. ÁRBOL DE DECISIÓN RÁPIDA: para los primeros 15 minutos
   de una crisis, ¿qué preguntas debo hacerme para clasificar
   el tipo y severidad de la crisis?

3. CHECKLIST DE ACTIVACIÓN DE COPILOT: qué información debo
   tener lista antes de usar Copilot para diagnóstico
   (tipo de datos, formato, contexto mínimo requerido).

4. PLANTILLAS DE PROMPT REUTILIZABLES: resume en una tabla
   los 3 prompts más efectivos que usé hoy, indicando para
   qué tipo de crisis aplica cada uno.

5. CRITERIOS DE ESCALACIÓN: ¿cuándo debo escalar a mi gerente
   vs. resolver autónomamente? Define 3 umbrales claros.

Formato: documento estructurado con secciones numeradas,
listas y una tabla para las plantillas de prompts.
Tono: práctico, como una guía de referencia rápida.
```

2. Revisa el protocolo generado. Personalízalo manualmente con al menos 2 ajustes basados en tu experiencia real o en el contexto de tu organización.
3. Guarda el documento final como `Protocolo_Crisis_[TuNombre].docx`.

**Resultado esperado:** Un protocolo de 1–2 páginas con los 5 componentes solicitados, incluyendo una tabla de prompts reutilizables y criterios de escalación claros.

**Verificación:** ¿Podrías usar este protocolo mañana mismo en una crisis real sin necesidad de modificarlo significativamente? ¿Los prompts de la tabla están suficientemente detallados para funcionar sin contexto adicional?

---

## 7. Validación y Pruebas

Al finalizar los cuatro pasos de la práctica, verifica el cumplimiento de cada entregable:

| Entregable | Criterio de éxito | ✅ / ❌ |
|---|---|---|
| **Plan de acción Escenario A** | 5 pasos con acción, responsable, tiempo e indicador de éxito; coherente con el hilo de Teams | |
| **Correo de disculpa al cliente (B-2a)** | 200–300 palabras; reconoce error, plan de recuperación con fechas, compensación, contacto | |
| **Correo de escalación interna (B-2b)** | 150–200 palabras; nivel de urgencia declarado, 3 acciones con plazos | |
| **Alerta al carrier (B-2c)** | 200–250 palabras; documenta incumplimiento, solicita causa raíz, tono firme no agresivo | |
| **Tabla de SKUs críticos (C-1)** | 3 SKUs identificados; días de cobertura validados manualmente; nivel de riesgo correcto | |
| **Memo ejecutivo (C-2)** | 300–400 palabras; tabla de SKUs, análisis de impacto, 3 recomendaciones con responsable y plazo | |
| **Protocolo de crisis (D-1)** | 5 secciones completas; tabla de prompts reutilizables; al menos 2 ajustes personales | |

### Prueba de Calidad de Comunicaciones

Aplica esta rúbrica rápida a cada comunicación redactada (B-2a, B-2b, B-2c, C-2):

| Criterio | Sí | Parcial | No |
|---|---|---|---|
| ¿La primera oración comunica el propósito del mensaje? | | | |
| ¿Los datos citados son coherentes con el dataset original? | | | |
| ¿El tono es apropiado para la audiencia específica? | | | |
| ¿Cada acción solicitada tiene un responsable y un plazo? | | | |
| ¿El mensaje puede leerse y comprenderse en < 60 segundos? | | | |

> **Meta:** Al menos 4 de 5 criterios en "Sí" para cada comunicación. Si alguna comunicación tiene 2 o más criterios en "No", regresa al paso correspondiente y refina el prompt.

---

## 8. Solución de Problemas

### Problema 1: Copilot en Teams no aparece o no responde al prompt

**Síntoma:** El ícono de Copilot (✨) no está visible en el panel lateral de Teams, o al ingresar un prompt el sistema muestra el mensaje *"Copilot no está disponible en este canal"* o simplemente no genera respuesta.

**Causa probable:** La licencia de Microsoft 365 Copilot no está asignada correctamente al usuario, la versión de Teams instalada es la versión clásica (no la nueva versión ≥ 2.1), o el canal/chat específico no tiene habilitada la función de Copilot (algunos canales privados o chats de invitados tienen restricciones).

**Solución:**

```
Paso 1: Verifica la versión de Teams.
→ Clic en los tres puntos (...) junto a tu foto de perfil
→ Ayuda > Acerca de Microsoft Teams
→ Confirma que la versión sea 2.1 o posterior.
→ Si es la versión clásica, descarga la nueva versión desde:
   https://www.microsoft.com/es-es/microsoft-teams/download-app

Paso 2: Verifica la licencia.
→ Navega a https://portal.office.com
→ Clic en tu foto de perfil > "Ver cuenta"
→ En "Suscripciones", confirma que aparece
  "Microsoft 365 Copilot" como licencia activa.
→ Si no aparece, contacta al administrador de TI o al instructor.

Paso 3: Usa la alternativa web como respaldo.
→ Si la licencia está activa pero Teams no muestra Copilot,
  navega a https://m365.cloud.microsoft/chat en Edge.
→ Esta interfaz funciona independientemente de la versión
  de Teams y permite pegar el hilo del escenario como texto.
```

---

### Problema 2: Las respuestas de Copilot son genéricas y no reflejan los datos del escenario

**Síntoma:** Copilot genera respuestas que parecen plantillas genéricas de logística, sin mencionar datos específicos del hilo de Teams o del dataset de Excel (nombres de carriers, números de pedidos, SKUs específicos, horas concretas). El análisis no es útil para tomar decisiones.

**Causa probable:** El prompt no incluyó el contexto de los datos de manera explícita (el archivo no se adjuntó correctamente, o el hilo de Teams no se pegó en el campo de texto), o el prompt fue demasiado abierto sin instruir a Copilot a basarse en los datos proporcionados.

**Solución:**

```
Paso 1: Verifica que los datos están en el contexto del prompt.
→ En Copilot Chat, confirma que el archivo adjunto aparece
  como un chip/etiqueta antes de enviar el prompt.
→ Si no aparece, intenta pegar los datos directamente en el
  campo de texto, precedidos por la instrucción:
  "Usa EXCLUSIVAMENTE los siguientes datos para tu análisis:
  [pegar datos aquí]"

Paso 2: Reformula el prompt con instrucción explícita de citar.
→ Agrega al final de tu prompt:
  "Basa tu respuesta ÚNICAMENTE en los datos proporcionados.
  Cita valores específicos del dataset en tu respuesta.
  Si un dato no está disponible en los datos proporcionados,
  indícalo explícitamente en lugar de inventarlo."

Paso 3: Reduce el alcance del prompt.
→ Si el prompt pide demasiadas cosas a la vez, divídelo en
  prompts más pequeños y específicos. Por ejemplo, primero
  pide solo la tabla de días de cobertura, y en un segundo
  prompt pide el análisis de patrones.

Paso 4: Valida siempre los números manualmente.
→ Recuerda el principio de la Lección 3.1: "datos sucios
  producen análisis poco confiables." Verifica al menos
  2–3 valores clave en el dataset original antes de usar
  los resultados de Copilot en una comunicación.
```

---

## 9. Limpieza del Entorno

Al finalizar la práctica, realiza los siguientes pasos para mantener el entorno ordenado y proteger la información de los escenarios:

```
1. BORRADORES DE OUTLOOK:
   → Abre Outlook > carpeta "Borradores"
   → Elimina los tres correos de práctica (B-2a, B-2b, B-2c)
     o muévelos a una carpeta "Lab03_Archivado" si deseas
     conservarlos como referencia.
   → No envíes ningún correo a direcciones reales de clientes
     o proveedores.

2. ARCHIVOS LOCALES:
   → La carpeta Lab03_Crisis puede conservarse en tu equipo
     para referencia futura.
   → Si usaste datos reales de tu empresa (no recomendado),
     verifica que los archivos estén protegidos con contraseña
     o elimínalos del equipo si son confidenciales.

3. HISTORIAL DE COPILOT CHAT:
   → En Microsoft 365 Copilot Chat, las conversaciones se
     guardan en el historial de tu cuenta.
   → Si los datos del escenario son sensibles, considera
     eliminar la conversación:
     Copilot Chat > ícono de historial (🕐) > seleccionar
     conversación > eliminar.

4. CANALES DE TEAMS:
   → Si el instructor creó canales temporales para el
     escenario A, no los abandones manualmente; el instructor
     los archivará al finalizar la sesión.

5. ENTREGABLES:
   → Sube tu archivo Protocolo_Crisis_[TuNombre].docx al
     canal o carpeta de OneDrive indicado por el instructor
     para evaluación.
   → Confirma con el instructor el método de entrega antes
     de cerrar sesión.
```

---

## 10. Resumen

### Lo que Lograste en Esta Práctica

En 90 minutos aplicaste Microsoft 365 Copilot para resolver tres escenarios reales de crisis logística, desarrollando competencias que van más allá del uso básico de la herramienta:

| Escenario | Habilidad desarrollada | Herramienta utilizada |
|---|---|---|
| **A — Cuello de botella en almacén** | Diagnóstico basado en evidencia; síntesis de conversaciones de crisis; generación de planes de acción estructurados | Copilot en Teams / Copilot Chat |
| **B — Falla de entrega a cliente** | Redacción técnica profesional para tres audiencias distintas; ajuste de tono; coherencia entre comunicaciones | Copilot en Outlook |
| **C — Riesgo de quiebre de stock** | Análisis de datos tabulares; identificación de patrones de riesgo; comunicación ejecutiva orientada a la decisión | Copilot Chat + Outlook |
| **D — Protocolo integrador** | Sistematización de aprendizajes; construcción de herramientas reutilizables; prompt engineering documentado | Copilot Chat |

### Principios Clave para Llevar a la Práctica

1. **Copilot es un aliado de diagnóstico, no solo de redacción.** Su mayor valor en logística está en correlacionar variables que manualmente tomarían horas de revisión.
2. **La calidad del output depende de la calidad del input.** Datos limpios + prompts precisos = diagnósticos confiables. Datos sucios o prompts vagos producen respuestas genéricas inutilizables.
3. **Valida siempre los números.** Copilot puede cometer errores en cálculos. Verifica al menos 2–3 valores clave antes de usar los resultados en una comunicación formal.
4. **El tono importa tanto como el contenido.** En una crisis, el mismo mensaje con tono equivocado puede escalar el conflicto en lugar de resolverlo. Usa Copilot para ajustar el tono, pero revisa siempre el resultado.
5. **Documenta tus prompts efectivos.** El protocolo que construiste en el Escenario D es tu activo más valioso de esta sesión; los prompts que funcionaron hoy funcionarán en la próxima crisis real.

### Conexión con la Práctica 4

La Práctica 4 llevará estas capacidades a un nivel de automatización: construirás un **agente funcional de seguimiento de pedidos** en Copilot Studio que pueda responder preguntas de clientes de forma autónoma, usando como base los flujos de comunicación y diagnóstico que practicaste hoy. El dominio de Teams y Outlook adquirido en esta sesión es el prerrequisito directo para esa construcción.

---

### Recursos de Referencia

| Recurso | URL |
|---|---|
| Documentación oficial: Copilot en Microsoft Teams | https://support.microsoft.com/es-es/topic/copilot-en-microsoft-teams |
| Documentación oficial: Borrador con Copilot en Outlook | https://support.microsoft.com/es-es/office/borrador-de-un-mensaje-de-correo-electrónico-con-copilot-en-outlook |
| Microsoft 365 Copilot Chat | https://m365.cloud.microsoft/chat |
| Guía de prompt engineering para Microsoft 365 Copilot | https://adoption.microsoft.com/es-es/copilot/ |
| Teoría de las Restricciones — Instituto Goldratt | https://www.toc-goldratt.com/en/product/Theory-Of-Constraints |
| CSCMP — Glosario de KPIs logísticos | https://cscmp.org/CSCMP/Educate/SCM_Definitions_and_Glossary_of_Terms.aspx |

---

*Práctica 3 de 4 — Módulo 3: Operaciones y Manejo de Crisis con Microsoft 365 Copilot*
*Duración total: 90 minutos | Nivel Bloom: Aplicar | Complejidad: Media*

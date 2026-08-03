# Práctica 4 — Creación de un Agente para Seguimiento de Pedidos y Atención al Cliente Logístico

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Avanzada |
| **Audiencia** | Coordinadores de servicio al cliente, analistas de operaciones, gestores de pedidos y supervisores de mesa de ayuda. |
| **Tecnologías** | Microsoft Copilot Studio / Agentes Personalizados de Copilot (M365), Microsoft Word y Microsoft Excel. |
| **Enfoque** | Configuración de agentes conversacionales personalizados, automatización de atención al cliente y generación de reportes de servicio. |

---

## 2. Descripción Corta

En este laboratorio práctico de 90 minutos, los participantes aprenderán a diseñar, configurar e interactuar con un **Agente Personalizado de Copilot** especializado en el seguimiento de pedidos, gestión de estados logísticos y resolución de incidencias. A lo largo de 6 fases, el estudiante estructurará las instrucciones del agente (Prompt de Sistema), lo desplegará en la plataforma, interactuará con él para atender consultas avanzadas, exportará los resultados analíticos a Excel y Word, y resolverá un reto autónomo de modificación de parámetros.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Diseñar las instrucciones del sistema (System Prompt)** de un agente personalizado usando principios de ingeniería de prompts.
* **Configurar un Agente de Copilot** definiendo su rol, límites de actuación, tono de respuesta y base de conocimiento.
* **Consultar al agente en escenarios operativos complejos** (rastreo de guías, cambios de dirección, retrasos y garantías).
* **Consolidar el historial de atención del agente** exportando los datos a registros estructurados en Excel y reportes en Word.
* **Modificar y escalar las capacidades del agente** mediante la actualización de sus directrices internas.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot / Copilot Studio** (creación de agentes personalizados).
* Aplicación de **Microsoft Excel** abierta.
* Aplicación de **Microsoft Word** abierta.

---

## 5. Procedimiento Paso a Paso

### Fase 1: Diseño del Prompt de Sistema del Agente (System Prompt)

El primer paso para crear un agente inteligente es definir sus "Instrucciones de Sistema", las cuales delimitan su personalidad, reglas de negocio y forma de responder.

1. Abra **Microsoft Copilot Chat**.
2. Copie el siguiente prompt de diseño para estructurar el Prompt de Sistema de nuestro nuevo agente:

```
Actúa como un Arquitecto de Agentes de Inteligencia Artificial. Necesito diseñar el "Prompt de Sistema" (System Prompt/Instructions) para un Agente de Copilot especializado en "Atención y Seguimiento de Pedidos Logísticos" denominado "RastreoBot".

Escribe el prompt del sistema delimitado con las siguientes secciones:
1. **Rol y Objetivo:** Un asistente virtual experto en rastreo de envíos y atención postventa.
2. **Base de Datos Simulada (Contexto Interno):** Un listado sintético con 4 pedidos simulados en JSON/Markdown que incluyan: `Numero_Pedido`, `Cliente`, `Estado` (En tránsito, Entregado, Con Retraso, En Aduana), `Transportista`, `Guia`, y `ETA` (Fecha estimada de entrega).
3. **Reglas de Negocio:**
   - Si el pedido está "Con Retraso", pedir disculpas y ofrecer una guía de compensación.
   - Si el cliente quiere cambiar la dirección y el estado es "En tránsito", indicar que requiere validación de seguridad.
   - Nunca inventar datos de pedidos que no estén en la base de datos simulada.
4. **Tono y Estilo:** Extremadamente profesional, empático, claro y estructurado con viñetas.

Entrégame la redacción limpia del Prompt de Sistema listo para copiar.
```

3. Copie y guarde la estructura del Prompt de Sistema generada.

---

### Fase 2: Configuración e Implementación Paso a Paso del Agente

Aprenderemos a configurar el agente dentro del entorno de Microsoft Copilot utilizando la instrucción creada en la Fase 1.

#### Guía Paso a Paso para la Creación del Agente:

1. **Acceso al Creador de Agentes:**
   * En la interfaz de **Microsoft Copilot (M365 / Web)**, diríjase al panel lateral izquierdo o al menú superior y seleccione la opción **"Agentes"** o **"Crear un Copilot/Agente"** (Copilot Studio / Agent Builder).
2. **Definición del Perfil:**
   * **Nombre:** `RastreoBot - Seguimiento de Pedidos`
   * **Descripción:** `Agente inteligente para consulta de estados de envío, rastreo de guías y atención de incidencias logísticas.`
3. **Inyección de las Instrucciones:**
   * Ubique el campo **"Instrucciones" / "Instructions"** (Prompt de Sistema).
   * Pegue íntegramente la estructura del Prompt de Sistema que generó en la **Fase 1** (asegurándose de incluir la base de datos simulada de los 4 pedidos).
4. **Prueba Inicial y Guardado:**
   * Escriba un mensaje de prueba en el panel de vista previa: *"Hola, ¿cuál es tu función?"*.
   * Verifique que el agente responda según el rol y tono asignados.
   * Haga clic en **"Guardar"** / **"Publicar"** para activar su agente operativo.

---

### Fase 3: Interacción Operativa y Consultas al Agente

Una vez creado el agente, realizaremos simulaciones de atención a clientes reales interactuando directamente con él.

1. Abra la ventana de chat de su agente **RastreoBot**.
2. Ejecute las siguientes 3 consultas secuenciales para poner a prueba las reglas de negocio del agente:

* **Consulta A (Rastreo Estándar):**
  > *"Hola, me gustaría saber el estado de mi pedido #PED-1001 y la fecha estimada de entrega."*
* **Consulta B (Manejo de Contingencias y Retrasos):**
  > *"Necesito ayuda urgente con el pedido #PED-1003, no ha llegado y la página muestra retraso."*
* **Consulta C (Solicitud de Cambio Operativo):**
  > *"Quiero cambiar la dirección de entrega del pedido #PED-1002 porque no estaré en mi casa."*

3. Mantenga abierta la sesión de chat con las respuestas generadas por **RastreoBot**.

---

### Fase 4: Exportación de Interacciones y Registro Logístico en Excel

Consolidaremos las métricas y el registro de la atención realizada por el agente en una matriz de control en Excel.

1. Abra **Microsoft Excel** con un libro en blanco.
2. En el chat con su agente **RastreoBot**, ejecute el siguiente prompt de consolidación:

```
Con base en todas las consultas de atención que acabamos de realizar en este chat, genera una tabla resumida en formato Markdown con el registro de atención.

La tabla debe incluir las columnas:
- `Fecha_Atencion`
- `Numero_Pedido`
- `Cliente`
- `Tipo_Consulta` (Rastreo, Retraso, Cambio Dirección)
- `Estado_Final_Pedido`
- `Accion_Sugerida_Por_Agente`

Asegúrate de que la tabla sea clara para copiarla directamente a Excel.
```

3. Copie la tabla generada por el agente, péguela en Excel y guarde el archivo como `Registro_Atencion_Agente.xlsx`.

---

### Fase 5: Exportación de Informe de Desempeño del Agente a Word

Estructuraremos un reporte formal de calidad sobre las interacciones automatizadas para presentarlo a la supervisión del área.

1. Abra **Microsoft Word** con un documento en blanco.
2. Solicite a su agente la redacción del reporte formal con el siguiente prompt:

```
Actúa como Supervisor de Servicio al Cliente. Con base en la sesión de atención actual, redacta un "Informe de Auditoría de Atención Automatizada" formal en Microsoft Word.

Estructura del documento:
1. **Encabezado:** Nombre del Agente (`RastreoBot`), Fecha de Auditoría y Total de Casos Atendidos.
2. **Resumen de Operación:** Breve evaluación de cómo el agente aplicó las reglas de negocio en los casos de prueba.
3. **Desglose de Casos Críticos:** Análisis del manejo del pedido con retraso y la política de disculpas/compensación aplicada.
4. **Recomendaciones de Mejora:** 2 sugerencias para ajustar las instrucciones del agente en la siguiente versión.

Usa un tono corporativo y formal.
```

3. Copie la respuesta, péguela en su archivo de Word y guárdelo como `Informe_Auditoria_Agente.docx`.

---

### Fase 6: Reto de Aplicación Autónoma – Modificación y Escalación del Agente

**Escenario del Reto:** La gerencia requiere actualizar las capacidades de **RastreoBot** para que ahora también procese **Solicitudes de Devolución/Garantía** y gestione un nuevo pedido prioritario (`#PED-2005`).

#### Pistas y Guía para Modificar el Agente:

* **Pista 1 (Modificación del Prompt de Sistema en el Creador):**
  * Ingrese a la opción de **Editar Agente** en Copilot / Copilot Studio.
  * Localice la sección de **Instrucciones (Instructions)**.
  * Añada al prompt de sistema el nuevo pedido simulado: `Numero_Pedido: #PED-2005, Cliente: Innovaciones Tech, Estado: Entregado, Fecha_Entrega: Hace 2 días`.
  * Agregue una nueva **Regla de Negocio**: *"Si el cliente solicita Devolución o Garantía, verificar que la fecha de entrega sea menor a 5 días. Si cumple, generar un código de autorización simulado (ej. DEV-8899) e indicar el centro de acopio más cercano."*
  * Guarde los cambios del agente.

* **Pista 2 (Prueba de la Nueva Capacidad):**
  * Escriba a su agente modificado: *"Quiero devolver el producto del pedido #PED-2005 porque salió defectuoso."*
  * Verifique que valide la regla de menos de 5 días y entregue el código de autorización.

* **Pista 3 (Actualización de Entregables en Excel y Word):**
  * Copie la nueva respuesta del agente e intégrela como una nueva fila en su archivo `Registro_Atencion_Agente.xlsx` (pestaña `Reto_Devoluciones`).
  * En Word, agregue un anexo de 1 página titulado *"Anexo: Actualización de Capacidades de Devolución del Agente"* y guarde el documento final como `Informe_Auditoria_Agente_V2.docx`.

---

## 6. Conceptos Clave para Recordar

* **Prompt de Sistema (System Prompt):** Conjunto de directrices primarias que definen la personalidad, límites, conocimientos y reglas de actuación de un agente de IA.
* **Agente Personalizado (Copilot Agent):** Configuración especializada de la IA orientada a ejecutar tareas específicas dentro de un flujo de trabajo de negocio.
* **Gobierno y Auditoría de Agentes:** Proceso de monitoreo continuo donde se registran y revisan las interacciones de los bots para asegurar el cumplimiento de las políticas de la empresa.

---

## 7. Resultado Esperado del Estudiante

El portafolio de evidencias de esta práctica debe incluir:

1. **Agente Configurado y Funcionando:** El agente `RastreoBot` creado e implementado en la plataforma Copilot.
2. **Archivo de Excel (`Registro_Atencion_Agente.xlsx`):**
   * **Pestaña `Registro_Sesion`:** Tabla de las consultas atendidas en la Fase 4.
   * **Pestaña `Reto_Devoluciones`:** Registro del caso de devolución configurado en el Reto (Fase 6).
3. **Archivo de Word (`Informe_Auditoria_Agente_V2.docx`):**
   * Informe de desempeño del agente con el desglose de casos y el anexo de actualización de capacidades del reto.

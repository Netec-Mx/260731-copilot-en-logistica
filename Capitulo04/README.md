---LAB_START---
LAB_ID: 04-00-01
---MARKDOWN---
# Práctica 4 — Creación de un Agente para Seguimiento de Pedidos y Atención al Cliente Logístico

## Metadatos

| Campo              | Detalle                                                                 |
|--------------------|-------------------------------------------------------------------------|
| **Duración**       | 60 minutos                                                              |
| **Complejidad**    | Alta                                                                    |
| **Nivel Bloom**    | Crear                                                                   |
| **Módulo**         | Módulo 4 — Automatización y Agentes en Microsoft 365 Copilot            |
| **Práctica**       | 4 de 4 (secuencia obligatoria)                                          |
| **Licencia requerida** | Microsoft 365 Copilot (activa, asignada al usuario)                |

---

## Descripción General

En esta práctica construirás desde cero un agente conversacional funcional en **Microsoft Copilot Studio** orientado a operaciones logísticas. El agente será capaz de responder consultas de seguimiento de pedidos, reportar incidencias, gestionar solicitudes de reprogramación y escalar casos complejos a un agente humano. Al finalizar, publicarás el agente en **Microsoft Teams** y simularás tres conversaciones reales de cliente para validar su comportamiento. Esta práctica integra los conocimientos de automatización en Teams y Outlook adquiridos en la Lección 4.1, elevando la capacidad de Copilot de asistente personal a agente autónomo de atención al cliente.

---

## Objetivos de Aprendizaje

Al completar esta práctica serás capaz de:

- [ ] Diseñar y configurar un agente conversacional en Copilot Studio con al menos 4 temas principales orientados a operaciones logísticas.
- [ ] Implementar variables de conversación, condiciones lógicas y flujos de escalación a agente humano dentro de Copilot Studio.
- [ ] Publicar e integrar el agente con un canal de Microsoft Teams para uso interno o de atención al cliente.
- [ ] Automatizar notificaciones de estado de pedido mediante la configuración del agente en el entorno de Teams y Outlook.
- [ ] Evaluar la efectividad del agente mediante la simulación de escenarios logísticos reales y aplicar refinamientos basados en los resultados.

---

## Requisitos Previos

### Conocimiento

- Haber completado las **Prácticas 1, 2 y 3** del curso (especialmente la Práctica 3 sobre Teams y Outlook).
- Comprensión básica de flujos de conversación y árboles de decisión (no se requiere experiencia en programación).
- Familiaridad con el uso de prompts estructurados en Microsoft 365 Copilot (cubierto en Práctica 1).
- Conocimiento de los conceptos de automatización administrativa en Teams y Outlook presentados en la Lección 4.1.

### Acceso y Permisos

- Cuenta Microsoft 365 con **licencia Copilot activa** (M365 Copilot, no Copilot Free).
- Acceso a **Microsoft Copilot Studio** en `https://copilotstudio.microsoft.com` con rol de **Creador** en el entorno de Power Platform del tenant.
- **Microsoft Teams** instalado (versión 2.1 o posterior) con permisos para agregar aplicaciones y bots.
- El administrador de TI debe haber **habilitado la creación de agentes** en Copilot Studio para el tenant antes de la sesión.
- Documento de diseño del agente (plantilla proporcionada por el instructor) disponible en OneDrive.

> ⚠️ **Nota crítica:** Si el administrador de TI no ha habilitado Power Platform para tu cuenta, no podrás crear ni publicar el agente. Coordina esta habilitación con **al menos 5 días de anticipación** a la sesión.

---

## Entorno de Laboratorio

### Hardware Recomendado

| Componente        | Mínimo Requerido                              | Recomendado                        |
|-------------------|-----------------------------------------------|------------------------------------|
| Procesador        | Intel Core i5 8ª gen / AMD Ryzen 5            | Intel Core i7 / AMD Ryzen 7        |
| Memoria RAM       | 8 GB                                          | 16 GB                              |
| Almacenamiento    | 10 GB libres                                  | 20 GB libres                       |
| Pantalla          | 1366 × 768                                    | 1920 × 1080                        |
| Conectividad      | 10 Mbps bajada, conexión estable              | 25 Mbps bajada, baja latencia      |
| Audio             | Micrófono y altavoces/auriculares funcionales | Auriculares con cancelación de ruido |

### Software Requerido

| Aplicación                  | Versión Mínima                        | Verificación                                        |
|-----------------------------|---------------------------------------|-----------------------------------------------------|
| Microsoft Edge              | 115 o posterior                       | `edge://settings/help`                              |
| Microsoft Teams             | 2.1 o posterior (nueva versión)       | Teams → `...` → Acerca de → Versión                 |
| Microsoft Outlook           | M365 versión de escritorio            | Archivo → Cuenta de Office → Versión                |
| Microsoft Copilot Studio    | Versión actual (acceso web)           | `https://copilotstudio.microsoft.com`               |
| Microsoft OneDrive          | Incluido en M365 (sincronizado)       | Ícono en bandeja del sistema                        |

### Configuración Inicial del Entorno

Ejecuta las siguientes verificaciones **antes de comenzar** la práctica:

**1. Verificar licencia Copilot activa:**

```
1. Abre un navegador Microsoft Edge.
2. Navega a: https://portal.office.com
3. Haz clic en tu avatar (esquina superior derecha) → Ver cuenta.
4. En "Suscripciones", confirma que aparece "Microsoft 365 Copilot".
5. Si no aparece, contacta a tu administrador antes de continuar.
```

**2. Verificar acceso a Copilot Studio:**

```
1. En Microsoft Edge, navega a: https://copilotstudio.microsoft.com
2. Inicia sesión con tus credenciales corporativas de M365.
3. Confirma que puedes ver el botón "+ Crear" en la pantalla de inicio.
4. Si ves un mensaje de "Sin permisos" o "Acceso denegado",
   contacta a tu administrador de TI inmediatamente.
```

**3. Verificar entorno de Power Platform disponible:**

```
1. Dentro de Copilot Studio, en la esquina superior derecha,
   verifica que el selector de entorno muestra tu entorno
   organizacional (no "Default" ni un entorno de prueba vacío).
2. Si solo ves el entorno "Default (orgname)", es aceptable
   para esta práctica.
```

**4. Descargar archivos de práctica:**

```
1. Abre Microsoft OneDrive en el navegador:
   https://onedrive.live.com/business
2. Navega a la carpeta compartida por el instructor:
   "Curso M365 Copilot Logística > Práctica 4"
3. Descarga los siguientes archivos a tu carpeta local:
   - Plantilla_Diseño_Agente_Logistico.docx
   - Dataset_Pedidos_Simulados.xlsx
   - Guia_Temas_Agente.pdf
4. Guarda los archivos en: C:\Labs\Practica4\
```

---

## Instrucciones Paso a Paso

> 📋 **Estructura de la práctica:** Esta práctica se divide en cuatro fases secuenciales:
> - **Fase 1 (15 min):** Arquitectura del agente
> - **Fase 2 (20 min):** Construcción en Copilot Studio
> - **Fase 3 (15 min):** Integración con Teams
> - **Fase 4 (10 min):** Prueba, refinamiento y discusión

---

### FASE 1 — Arquitectura del Agente Logístico

#### Paso 1.1 — Definir el Propósito y Alcance del Agente

**Objetivo:** Establecer el contexto operativo del agente antes de construirlo, siguiendo el principio de que el contexto es el motor de Copilot (Lección 4.1).

**Instrucciones:**

1. Abre el archivo `Plantilla_Diseño_Agente_Logistico.docx` desde `C:\Labs\Practica4\`.

2. Completa la sección **"Propósito del Agente"** con la siguiente información base (puedes adaptar los valores al contexto de tu empresa si usas datos reales):

   ```
   Nombre del agente:     LogiBot — Asistente de Pedidos
   Empresa simulada:      Distribuidora Central S.A. de C.V.
   Audiencia objetivo:    Clientes internos (coordinadores) y 
                          clientes externos (distribuidoras)
   Idioma principal:      Español
   Canal de despliegue:   Microsoft Teams
   ```

3. En la sección **"Capacidades del Agente"**, marca las cuatro capacidades que construirás:

   ```
   [x] Seguimiento de pedido por número de pedido
   [x] Consulta de estado de entrega (en tránsito, retrasado, entregado)
   [x] Reporte de incidencias (daño, faltante, dirección incorrecta)
   [x] Solicitud de reprogramación de entrega
   ```

4. En la sección **"Limitaciones del Agente"**, documenta lo que el agente **no** hará:

   ```
   [ ] No procesará pagos ni modificará pedidos en el sistema ERP.
   [ ] No accederá a información financiera del cliente.
   [ ] No resolverá disputas contractuales.
   [ ] Escalará a agente humano cualquier caso que requiera
       criterio discrecional o información no disponible en el script.
   ```

5. Guarda el documento.

**Resultado esperado:** Documento de diseño con propósito, capacidades y limitaciones claramente definidos.

**Verificación:** Comparte el documento con el instructor o compañero de mesa para revisión antes de continuar a la siguiente fase.

---

#### Paso 1.2 — Diseñar el Árbol de Conversación

**Objetivo:** Mapear los 4 temas principales del agente con sus flujos de conversación antes de construirlos en la plataforma.

**Instrucciones:**

1. En el mismo documento, navega a la sección **"Árbol de Conversación"**.

2. Dibuja o completa el mapa de temas con la siguiente estructura base:

   ```
   AGENTE: LogiBot
   │
   ├── TEMA 1: Bienvenida y Menú Principal
   │   ├── Disparador: saludo inicial / mensaje de bienvenida
   │   └── Acción: presentar opciones 1-4 al usuario
   │
   ├── TEMA 2: Seguimiento de Pedido
   │   ├── Disparador: "seguimiento", "dónde está mi pedido",
   │   │              "estado de pedido", número de pedido
   │   ├── Variable: NumeroPedido (texto)
   │   ├── Variable: NombreCliente (texto)
   │   ├── Condición: si pedido existe → mostrar estado
   │   └── Condición: si pedido no existe → solicitar corrección
   │
   ├── TEMA 3: Reporte de Incidencia
   │   ├── Disparador: "incidencia", "problema", "daño",
   │   │              "faltante", "no llegó"
   │   ├── Variable: TipoIncidencia (opciones: daño/faltante/otro)
   │   ├── Variable: NumeroPedidoIncidencia (texto)
   │   └── Acción: generar número de caso y escalar a humano
   │
   └── TEMA 4: Reprogramación de Entrega
       ├── Disparador: "reprogramar", "cambiar fecha",
       │              "no puedo recibir", "nueva fecha"
       ├── Variable: FechaDeseada (texto/fecha)
       ├── Condición: si fecha disponible → confirmar
       └── Condición: si fecha no disponible → ofrecer alternativas
   ```

3. Identifica el **punto de escalación** para cada tema:

   | Tema | Condición de Escalación |
   |------|------------------------|
   | Seguimiento de Pedido | Pedido con más de 5 días de retraso |
   | Reporte de Incidencia | Siempre (requiere agente humano) |
   | Reprogramación | Más de 2 intentos fallidos de fecha |
   | Bienvenida | Usuario solicita "agente humano" explícitamente |

4. Guarda el documento.

**Resultado esperado:** Árbol de conversación documentado con 4 temas, variables identificadas y condiciones de escalación definidas.

**Verificación:** El árbol debe tener al menos 4 temas, al menos 3 variables de conversación identificadas y al menos 2 condiciones de escalación documentadas.

---

### FASE 2 — Construcción en Copilot Studio

#### Paso 2.1 — Crear el Agente en Copilot Studio

**Objetivo:** Inicializar el agente en la plataforma con la configuración base.

**Instrucciones:**

1. Abre Microsoft Edge y navega a `https://copilotstudio.microsoft.com`.

2. Inicia sesión con tus credenciales corporativas de Microsoft 365.

3. En la pantalla de inicio, haz clic en **"+ Crear"** (botón azul, esquina superior izquierda o centro de pantalla).

4. Selecciona **"Nuevo agente"** en el menú de opciones.

5. En la pantalla de creación asistida, completa los campos:

   ```
   Nombre del agente:  LogiBot — Asistente de Pedidos
   Descripción:        Agente de atención al cliente para seguimiento
                       de pedidos, reporte de incidencias y 
                       reprogramación de entregas de 
                       Distribuidora Central S.A. de C.V.
   Instrucciones:      Eres LogiBot, un asistente virtual de 
                       logística amigable y profesional. Ayudas a 
                       los clientes con el seguimiento de sus pedidos,
                       el reporte de incidencias y la reprogramación 
                       de entregas. Siempre saluda con cortesía, 
                       usa un tono formal pero accesible, y escala 
                       a un agente humano cuando el caso lo requiera.
                       Responde siempre en español.
   ```

6. En el campo **"¿Qué puede hacer este agente?"**, escribe:

   ```
   - Consultar el estado de un pedido por número
   - Reportar incidencias como daños o faltantes
   - Solicitar la reprogramación de una entrega
   - Escalar casos complejos a un agente humano
   ```

7. Haz clic en **"Crear"** y espera a que el sistema inicialice el agente (30-60 segundos).

**Resultado esperado:** El agente "LogiBot — Asistente de Pedidos" aparece en el panel de Copilot Studio con el estado "Borrador".

**Verificación:** Confirma que el agente aparece en la lista de agentes con el nombre correcto y que puedes acceder a su panel de edición haciendo clic sobre él.

---

#### Paso 2.2 — Configurar el Tema de Bienvenida

**Objetivo:** Personalizar el mensaje de bienvenida del agente con el contexto logístico.

**Instrucciones:**

1. Dentro del panel del agente, haz clic en la pestaña **"Temas"** en el menú lateral izquierdo.

2. Localiza el tema **"Saludo"** (o "Greeting") en la lista de temas del sistema. Haz clic sobre él para editarlo.

3. En el nodo de mensaje de bienvenida, reemplaza el texto predeterminado con:

   ```
   ¡Hola! Soy LogiBot, el asistente virtual de Distribuidora Central. 
   Estoy aquí para ayudarte con:
   
   1️⃣ Seguimiento de tu pedido
   2️⃣ Reportar una incidencia
   3️⃣ Reprogramar una entrega
   4️⃣ Hablar con un agente humano
   
   ¿Con cuál de estas opciones puedo ayudarte hoy?
   ```

4. Agrega un nodo de **"Pregunta"** después del mensaje de bienvenida:
   - Tipo de pregunta: **Opciones múltiples**
   - Variable de respuesta: `OpcionMenu` (tipo: texto)
   - Opciones:
     ```
     Opción 1: Seguimiento de pedido
     Opción 2: Reportar incidencia
     Opción 3: Reprogramar entrega
     Opción 4: Hablar con agente humano
     ```

5. Haz clic en **"Guardar"** en la esquina superior derecha.

**Resultado esperado:** El tema de bienvenida muestra el mensaje personalizado con las 4 opciones del menú y una variable `OpcionMenu` configurada.

**Verificación:** Usa el panel de **"Probar agente"** (botón en la esquina inferior derecha) y escribe "Hola". El agente debe responder con el mensaje de bienvenida y las 4 opciones.

---

#### Paso 2.3 — Construir el Tema de Seguimiento de Pedido

**Objetivo:** Crear el flujo de conversación más crítico del agente: la consulta de estado de pedido.

**Instrucciones:**

1. En la pestaña **"Temas"**, haz clic en **"+ Agregar tema"** → **"Desde cero"**.

2. Configura el tema con los siguientes datos:

   ```
   Nombre del tema:  Seguimiento de Pedido
   ```

3. En la sección **"Frases de activación"** (disparadores), agrega las siguientes frases (una por línea, presionando Enter entre cada una):

   ```
   seguimiento de pedido
   dónde está mi pedido
   estado de mi pedido
   quiero saber mi pedido
   número de pedido
   rastrear pedido
   cuándo llega mi pedido
   ```

4. Construye el flujo de conversación agregando los siguientes nodos en orden:

   **Nodo 1 — Mensaje de confirmación:**
   ```
   Con gusto te ayudo con el seguimiento de tu pedido. 
   Necesito algunos datos para buscarlo.
   ```

   **Nodo 2 — Pregunta (variable NumeroPedido):**
   ```
   Tipo: Texto
   Pregunta: ¿Cuál es el número de tu pedido? 
             (Ejemplo: PED-2024-0001)
   Variable: NumeroPedido
   ```

   **Nodo 3 — Pregunta (variable NombreCliente):**
   ```
   Tipo: Texto
   Pregunta: ¿Cuál es el nombre de la empresa o 
             persona que realizó el pedido?
   Variable: NombreCliente
   ```

   **Nodo 4 — Mensaje de confirmación de búsqueda:**
   ```
   Gracias, {NombreCliente}. Estoy consultando el estado 
   del pedido {NumeroPedido}...
   ```

   **Nodo 5 — Condición (simular estados):**

   Haz clic en **"+"** → **"Agregar condición"** y crea tres ramas:

   ```
   Rama A — "En tránsito":
   Condición: NumeroPedido termina en número par (simulado)
   Mensaje: Tu pedido {NumeroPedido} está EN TRÁNSITO. 
            Fecha estimada de entrega: mañana antes de las 18:00 hrs.
            El transportista asignado es Rápido Express.
            ¿Hay algo más en lo que pueda ayudarte?

   Rama B — "Retrasado":
   Condición: NumeroPedido termina en número impar (simulado)
   Mensaje: Tu pedido {NumeroPedido} presenta un RETRASO 
            de 2 días. La nueva fecha estimada es el próximo 
            jueves. El equipo ya fue notificado.
            ¿Deseas que te conecte con un agente para más detalles?

   Rama C — "No encontrado" (rama predeterminada):
   Mensaje: No encontré el pedido {NumeroPedido} en el sistema. 
            Por favor verifica el número e intenta nuevamente, 
            o escribe "agente" para hablar con un representante.
   ```

   > 💡 **Nota para el instructor:** En un entorno de producción, la condición se conectaría a una fuente de datos real (Dataverse, API REST, SharePoint). Para esta práctica usamos condiciones simuladas basadas en el número de pedido para demostrar la lógica sin necesidad de integración backend.

5. Al final de la **Rama B (Retrasado)**, agrega un nodo de **"Pregunta"**:
   ```
   Tipo: Opciones múltiples
   Pregunta: ¿Deseas hablar con un agente humano?
   Opciones: Sí, conéctame / No, gracias
   Variable: DeseasEscalar
   ```

6. Agrega un nodo de **"Condición"** después:
   ```
   Si DeseasEscalar = "Sí, conéctame"
   → Nodo de Acción: "Transferir a agente humano"
     Mensaje de transferencia: "Te estoy conectando con 
     un agente especializado. El tiempo de espera estimado 
     es de 5 minutos. ¡Gracias por tu paciencia!"
   ```

7. Haz clic en **"Guardar"**.

**Resultado esperado:** El tema "Seguimiento de Pedido" tiene un flujo completo con 2 variables (`NumeroPedido`, `NombreCliente`), 3 ramas condicionales y una ruta de escalación a agente humano.

**Verificación:** En el panel de prueba, escribe "quiero saber mi pedido". El agente debe solicitar el número de pedido y el nombre del cliente, luego mostrar un mensaje de estado simulado.

---

#### Paso 2.4 — Construir el Tema de Reporte de Incidencias

**Objetivo:** Crear el flujo para que los clientes reporten problemas con sus pedidos, con escalación automática a agente humano.

**Instrucciones:**

1. Agrega un nuevo tema: **"+ Agregar tema"** → **"Desde cero"**.

2. Configura:
   ```
   Nombre del tema: Reporte de Incidencia
   ```

3. Agrega las siguientes frases de activación:
   ```
   reportar incidencia
   tengo un problema con mi pedido
   mi pedido llegó dañado
   falta producto en mi pedido
   pedido incompleto
   no llegó mi pedido
   pedido con daño
   quiero reportar un problema
   ```

4. Construye el flujo con los siguientes nodos:

   **Nodo 1 — Mensaje empático:**
   ```
   Lamento escuchar que tuviste un problema con tu pedido. 
   Voy a ayudarte a registrar la incidencia de inmediato.
   ```

   **Nodo 2 — Pregunta (NumeroPedidoIncidencia):**
   ```
   Tipo: Texto
   Pregunta: ¿Cuál es el número del pedido con incidencia?
   Variable: NumeroPedidoIncidencia
   ```

   **Nodo 3 — Pregunta (TipoIncidencia):**
   ```
   Tipo: Opciones múltiples
   Pregunta: ¿Qué tipo de incidencia deseas reportar?
   Opciones:
     - Producto dañado
     - Producto faltante
     - Pedido no entregado
     - Dirección incorrecta
     - Otro
   Variable: TipoIncidencia
   ```

   **Nodo 4 — Pregunta (DescripcionIncidencia):**
   ```
   Tipo: Texto largo
   Pregunta: Por favor describe brevemente el problema 
             (máximo 200 caracteres):
   Variable: DescripcionIncidencia
   ```

   **Nodo 5 — Mensaje de confirmación con número de caso:**
   ```
   He registrado tu incidencia con los siguientes datos:
   
   📦 Pedido: {NumeroPedidoIncidencia}
   🔴 Tipo: {TipoIncidencia}
   📝 Descripción: {DescripcionIncidencia}
   🎫 Número de caso: INC-{NumeroPedidoIncidencia}-001
   
   Un agente especializado revisará tu caso en las 
   próximas 2 horas hábiles. ¿Deseas que te transfiera 
   ahora con un agente?
   ```

   **Nodo 6 — Pregunta de escalación:**
   ```
   Tipo: Opciones múltiples
   Opciones: Sí, hablar ahora / No, esperaré el seguimiento
   Variable: EscalarIncidencia
   ```

   **Nodo 7 — Condición de escalación:**
   ```
   Si EscalarIncidencia = "Sí, hablar ahora"
   → Transferir a agente humano
     Mensaje: "Transfiriéndote con el equipo de incidencias. 
     Tu número de caso es INC-{NumeroPedidoIncidencia}-001. 
     Compártelo con el agente."
   
   Si EscalarIncidencia = "No, esperaré el seguimiento"
   → Mensaje: "Perfecto. Recibirás una actualización por 
     correo electrónico en las próximas 2 horas hábiles. 
     ¿Puedo ayudarte con algo más?"
   ```

5. Haz clic en **"Guardar"**.

**Resultado esperado:** El tema "Reporte de Incidencia" captura 4 variables, genera un número de caso simulado y ofrece escalación inmediata o seguimiento por correo.

**Verificación:** En el panel de prueba, escribe "mi pedido llegó dañado". El agente debe solicitar el número de pedido, el tipo de incidencia y la descripción, luego confirmar el registro con número de caso.

---

#### Paso 2.5 — Construir el Tema de Reprogramación de Entrega

**Objetivo:** Implementar el flujo para solicitudes de cambio de fecha de entrega.

**Instrucciones:**

1. Agrega un nuevo tema: **"Reprogramación de Entrega"**.

2. Frases de activación:
   ```
   reprogramar entrega
   cambiar fecha de entrega
   no puedo recibir el pedido
   quiero otra fecha
   nueva fecha de entrega
   posponer entrega
   ```

3. Flujo de conversación:

   **Nodo 1:**
   ```
   Entendido, puedo ayudarte a gestionar una nueva 
   fecha de entrega para tu pedido.
   ```

   **Nodo 2 — Variable NumeroPedidoReprog:**
   ```
   Tipo: Texto
   Pregunta: ¿Cuál es el número del pedido que 
             deseas reprogramar?
   Variable: NumeroPedidoReprog
   ```

   **Nodo 3 — Variable FechaDeseada:**
   ```
   Tipo: Texto
   Pregunta: ¿Qué fecha prefieres para recibir 
             tu entrega? (Formato: DD/MM/AAAA)
   Variable: FechaDeseada
   ```

   **Nodo 4 — Variable HorarioPreferido:**
   ```
   Tipo: Opciones múltiples
   Pregunta: ¿Qué horario prefieres?
   Opciones:
     - Mañana (8:00 - 12:00)
     - Tarde (12:00 - 17:00)
     - Cualquier horario
   Variable: HorarioPreferido
   ```

   **Nodo 5 — Confirmación:**
   ```
   He registrado tu solicitud de reprogramación:
   
   📦 Pedido: {NumeroPedidoReprog}
   📅 Nueva fecha solicitada: {FechaDeseada}
   🕐 Horario preferido: {HorarioPreferido}
   
   ⚠️ Nota: La reprogramación está sujeta a 
   disponibilidad del transportista. Recibirás 
   confirmación en máximo 4 horas hábiles.
   
   ¿Hay algo más en lo que pueda ayudarte?
   ```

4. Haz clic en **"Guardar"**.

**Resultado esperado:** El tema "Reprogramación de Entrega" captura número de pedido, fecha deseada y horario preferido, y confirma la solicitud al cliente.

**Verificación:** En el panel de prueba, escribe "quiero cambiar la fecha de mi entrega". El agente debe solicitar los tres datos y confirmar la solicitud.

---

#### Paso 2.6 — Configurar la Escalación a Agente Humano

**Objetivo:** Asegurar que el agente puede transferir conversaciones a un agente humano de forma fluida desde cualquier punto del flujo.

**Instrucciones:**

1. En la pestaña **"Temas"**, localiza el tema del sistema **"Escalar a agente humano"** (o "Escalate"). Haz clic para editarlo.

2. Personaliza el mensaje de transferencia:
   ```
   Entendido. Voy a transferirte con uno de nuestros 
   agentes especializados de Distribuidora Central.
   
   📋 Resumen de tu consulta:
   - Pedido consultado: {NumeroPedido} (si aplica)
   - Tipo de solicitud: {OpcionMenu} (si aplica)
   
   ⏱️ Tiempo de espera estimado: 3-5 minutos
   Horario de atención: Lunes a Viernes, 8:00 - 18:00 hrs
   
   Un agente te atenderá en breve. ¡Gracias por 
   contactar a Distribuidora Central!
   ```

3. Verifica que el nodo de transferencia esté configurado como **"Finalizar conversación y transferir"** (no solo finalizar).

4. Agrega el tema **"Agente humano"** como disparador explícito:
   ```
   Frases de activación adicionales:
   - hablar con agente
   - agente humano
   - hablar con persona
   - representante
   - asesor
   ```

5. Haz clic en **"Guardar"**.

**Resultado esperado:** El agente puede ser invocado para transferir a un humano desde cualquier punto de la conversación con un mensaje claro y contextualizado.

**Verificación:** En el panel de prueba, escribe "quiero hablar con un agente". El agente debe responder con el mensaje de transferencia personalizado.

---

### FASE 3 — Integración con Microsoft Teams

#### Paso 3.1 — Publicar el Agente

**Objetivo:** Publicar el agente para que esté disponible para su despliegue en canales.

**Instrucciones:**

1. En el panel del agente en Copilot Studio, haz clic en el botón **"Publicar"** (esquina superior derecha, ícono de cohete o botón azul).

2. En el cuadro de confirmación, revisa el resumen del agente:
   ```
   Agente: LogiBot — Asistente de Pedidos
   Temas activos: 4 (Bienvenida, Seguimiento, Incidencia, Reprogramación)
   Estado: Listo para publicar
   ```

3. Haz clic en **"Publicar"** y espera el mensaje de confirmación (puede tomar 1-2 minutos).

4. Una vez publicado, verás el mensaje:
   ```
   ✅ "Tu agente ha sido publicado exitosamente."
   ```

**Resultado esperado:** El agente pasa de estado "Borrador" a "Publicado" y aparece disponible para configurar canales.

**Verificación:** En la lista de agentes, el estado del agente debe mostrar "Publicado" con la fecha y hora actuales.

---

#### Paso 3.2 — Conectar el Agente con Microsoft Teams

**Objetivo:** Configurar Microsoft Teams como canal de despliegue del agente.

**Instrucciones:**

1. En el panel del agente publicado, navega a la pestaña **"Canales"** en el menú lateral.

2. Localiza la tarjeta de **"Microsoft Teams"** y haz clic en **"Agregar canal"** o **"Configurar"**.

3. En la pantalla de configuración de Teams, completa:

   ```
   Nombre para mostrar en Teams:  LogiBot — Pedidos
   Descripción corta:             Asistente de seguimiento de 
                                  pedidos y atención al cliente
   Categoría:                     Productividad
   Ícono:                         (usar ícono predeterminado o 
                                  cargar logo de la empresa simulada)
   ```

4. Haz clic en **"Agregar a Teams"**.

5. El sistema generará un enlace de instalación. Copia el enlace.

6. Abre **Microsoft Teams** en tu computadora.

7. En Teams, haz clic en **"..."** (Más opciones) en la barra lateral izquierda → **"Aplicaciones"**.

8. En la barra de búsqueda, busca **"LogiBot"** o usa el enlace copiado para instalar el agente directamente.

9. Haz clic en **"Agregar"** para instalar el agente en tu cuenta de Teams.

10. Alternativamente, si tienes permisos de administrador del canal, agrega el agente a un **canal específico de Teams**:
    ```
    Canal destino: "Atención al Cliente - Logística" 
    (crea este canal si no existe en tu equipo de práctica)
    ```

**Resultado esperado:** LogiBot aparece como una aplicación instalada en Teams y es accesible desde el chat o desde el canal configurado.

**Verificación:** En Teams, abre el chat con **"LogiBot — Pedidos"** y escribe "Hola". El agente debe responder con el mensaje de bienvenida configurado en el Paso 2.2.

---

#### Paso 3.3 — Configurar Notificación Automática de Estado de Pedido

**Objetivo:** Implementar una notificación proactiva que el agente envíe en Teams cuando un pedido cambia de estado, aplicando los conceptos de automatización de la Lección 4.1.

**Instrucciones:**

1. En Copilot Studio, navega a la pestaña **"Acciones"** del agente (o **"Flujos"** dependiendo de la versión).

2. Haz clic en **"+ Agregar acción"** → **"Crear flujo en Power Automate"**.

3. En Power Automate (que se abre en una nueva pestaña), configura el flujo con la siguiente lógica:

   ```
   NOMBRE DEL FLUJO: Notificación de Estado de Pedido - LogiBot
   
   DISPARADOR: 
   Tipo: Desencadenador manual (para prueba)
   Descripción: Se activa cuando el estado de un pedido cambia
   
   PARÁMETROS DE ENTRADA:
   - NumeroPedido (texto)
   - NuevoEstado (texto): "En tránsito" / "Retrasado" / "Entregado"
   - NombreCliente (texto)
   - FechaEstimada (texto)
   
   ACCIÓN 1: Publicar mensaje en canal de Teams
   Conector: Microsoft Teams
   Acción: "Publicar mensaje en un chat o canal"
   Equipo: [Tu equipo de práctica]
   Canal: Atención al Cliente - Logística
   Mensaje:
   📦 ACTUALIZACIÓN DE PEDIDO
   
   Cliente: {NombreCliente}
   Pedido: {NumeroPedido}
   Estado: {NuevoEstado}
   Fecha estimada: {FechaEstimada}
   
   Este mensaje fue generado automáticamente por LogiBot.
   Para más información, escribe al agente o contacta 
   a tu coordinador asignado.
   
   ACCIÓN 2: Enviar correo en Outlook
   Conector: Office 365 Outlook
   Acción: "Enviar un correo electrónico (V2)"
   Para: [correo del participante para prueba]
   Asunto: Actualización de Pedido {NumeroPedido} — {NuevoEstado}
   Cuerpo:
   Estimado/a {NombreCliente},
   
   Le informamos que el estado de su pedido 
   {NumeroPedido} ha cambiado a: {NuevoEstado}.
   
   Fecha estimada de entrega: {FechaEstimada}
   
   Para consultas adicionales, puede comunicarse con 
   nuestro asistente LogiBot directamente en Teams.
   
   Atentamente,
   Equipo de Logística — Distribuidora Central
   ```

4. Haz clic en **"Guardar"** en Power Automate.

5. Regresa a Copilot Studio y vincula el flujo recién creado con el agente.

6. **Prueba la notificación:**
   ```
   En Power Automate, localiza el flujo 
   "Notificación de Estado de Pedido - LogiBot".
   Haz clic en "Ejecutar" (Run) con los siguientes 
   valores de prueba:
   
   NumeroPedido:  PED-2024-0042
   NuevoEstado:   Retrasado
   NombreCliente: Distribuidora Norte S.A.
   FechaEstimada: Jueves 19, antes de las 18:00 hrs
   ```

**Resultado esperado:** Aparece un mensaje en el canal de Teams y un correo en Outlook con los datos del pedido simulado, tal como se diseñó en el flujo.

**Verificación:** Confirma que:
- El mensaje aparece en el canal **"Atención al Cliente - Logística"** de Teams.
- El correo llega a tu buzón de Outlook con el asunto correcto.
- El formato del mensaje es legible y contiene todos los campos configurados.

---

### FASE 4 — Prueba, Refinamiento y Discusión

#### Paso 4.1 — Simular Conversación 1: Pedido en Tránsito

**Objetivo:** Validar el flujo de seguimiento para un escenario positivo.

**Instrucciones:**

1. En Microsoft Teams, abre el chat con **LogiBot — Pedidos**.

2. Ejecuta la siguiente conversación simulada (escribe exactamente estos mensajes):

   ```
   Tú:     Hola
   Bot:    [Mensaje de bienvenida con menú]
   
   Tú:     Quiero saber el estado de mi pedido
   Bot:    [Solicita número de pedido]
   
   Tú:     PED-2024-0042
   Bot:    [Solicita nombre del cliente]
   
   Tú:     Distribuidora Norte
   Bot:    [Muestra estado — En tránsito o Retrasado según la lógica configurada]
   
   Tú:     Gracias
   Bot:    [Respuesta de cierre]
   ```

3. Registra en la **Hoja de Evaluación** (en el documento de diseño):

   | Campo | Observación |
   |-------|-------------|
   | ¿El bot entendió el disparador? | Sí / No |
   | ¿Capturó correctamente las variables? | Sí / No |
   | ¿El estado mostrado fue coherente? | Sí / No |
   | ¿El tono fue apropiado? | Sí / No |
   | Ajuste necesario | (describir si aplica) |

**Resultado esperado:** El agente completa el flujo de seguimiento sin errores, mostrando el estado simulado del pedido con el nombre del cliente en el mensaje.

**Verificación:** Todas las variables (`NumeroPedido`, `NombreCliente`) deben aparecer correctamente en el mensaje de estado generado por el agente.

---

#### Paso 4.2 — Simular Conversación 2: Pedido Retrasado con Escalación

**Objetivo:** Validar el flujo de escalación a agente humano en un escenario de pedido retrasado.

**Instrucciones:**

1. Inicia una nueva conversación con LogiBot en Teams.

2. Ejecuta la siguiente simulación:

   ```
   Tú:     Necesito saber dónde está mi pedido, lleva 3 días de retraso
   Bot:    [Activa el tema de Seguimiento]
   
   Tú:     PED-2024-0077  [número impar → activa rama "Retrasado"]
   Bot:    [Solicita nombre]
   
   Tú:     Empresa Logística del Norte
   Bot:    [Muestra mensaje de retraso y pregunta si desea escalar]
   
   Tú:     Sí, conéctame
   Bot:    [Mensaje de transferencia a agente humano]
   ```

3. Registra las observaciones en la Hoja de Evaluación:

   | Campo | Observación |
   |-------|-------------|
   | ¿El disparador de urgencia funcionó? | Sí / No |
   | ¿La condición de retraso se activó? | Sí / No |
   | ¿La escalación fue fluida? | Sí / No |
   | ¿El mensaje de transferencia incluyó contexto? | Sí / No |
   | Ajuste necesario | (describir si aplica) |

**Resultado esperado:** El agente detecta el escenario de retraso, ofrece escalación y transfiere con mensaje contextualizado que incluye el número de pedido.

**Verificación:** El mensaje de transferencia debe incluir el número de pedido (`PED-2024-0077`) y el nombre del cliente capturado en la conversación.

---

#### Paso 4.3 — Simular Conversación 3: Pedido con Incidencia

**Objetivo:** Validar el flujo de reporte de incidencias con generación de número de caso.

**Instrucciones:**

1. Inicia una nueva conversación con LogiBot en Teams.

2. Ejecuta la siguiente simulación:

   ```
   Tú:     Mi pedido llegó con productos dañados
   Bot:    [Activa el tema de Reporte de Incidencia]
   
   Tú:     PED-2024-0055
   Bot:    [Pregunta tipo de incidencia]
   
   Tú:     Producto dañado
   Bot:    [Solicita descripción]
   
   Tú:     Tres cajas llegaron aplastadas, el contenido 
           está derramado y no es utilizable
   Bot:    [Genera número de caso y ofrece escalación]
   
   Tú:     No, esperaré el seguimiento
   Bot:    [Confirma que recibirá actualización por correo]
   ```

3. Registra las observaciones:

   | Campo | Observación |
   |-------|-------------|
   | ¿El agente mostró empatía en el primer mensaje? | Sí / No |
   | ¿Capturó correctamente el tipo de incidencia? | Sí / No |
   | ¿Se generó el número de caso? | Sí / No |
   | ¿El mensaje final fue claro sobre los próximos pasos? | Sí / No |
   | Ajuste necesario | (describir si aplica) |

**Resultado esperado:** El agente completa el flujo de incidencia, genera el número de caso `INC-PED-2024-0055-001` y confirma el seguimiento por correo.

**Verificación:** El número de caso generado debe incluir el número de pedido capturado durante la conversación.

---

#### Paso 4.4 — Aplicar Refinamientos Basados en Pruebas

**Objetivo:** Mejorar el agente con base en las observaciones registradas en las tres simulaciones.

**Instrucciones:**

1. Revisa la **Hoja de Evaluación** completada en los pasos 4.1, 4.2 y 4.3.

2. Identifica al menos **dos áreas de mejora** y aplica los ajustes en Copilot Studio:

   **Ejemplos de refinamientos comunes:**

   ```
   REFINAMIENTO A — Agregar frases de activación faltantes:
   Si el bot no entendió "lleva 3 días de retraso" como 
   disparador de seguimiento:
   → Ve al Tema "Seguimiento de Pedido"
   → Agrega frases: "retraso", "no ha llegado", 
     "días de retraso", "tardando mucho"
   → Guarda y republica el agente.
   
   REFINAMIENTO B — Mejorar mensaje de empatía:
   Si el tono del primer mensaje de incidencia no fue 
   suficientemente empático:
   → Ve al Tema "Reporte de Incidencia"
   → Edita el Nodo 1 para agregar más contexto emocional
   → Ejemplo: "Entiendo lo frustrante que puede ser 
     esta situación. Voy a ayudarte a resolverlo 
     lo antes posible."
   → Guarda y republica.
   
   REFINAMIENTO C — Agregar mensaje de tiempo de respera:
   Si el flujo de escalación no comunicó claramente 
   el tiempo de espera:
   → Ve al Tema "Escalar a Agente Humano"
   → Agrega en el mensaje: "Tiempo estimado: 3-5 minutos"
   → Guarda y republica.
   ```

3. Después de aplicar los refinamientos, **republica el agente**:
   ```
   En Copilot Studio → Botón "Publicar" → Confirmar
   ```

4. Ejecuta una prueba rápida del flujo refinado en Teams para confirmar la mejora.

**Resultado esperado:** Al menos dos refinamientos aplicados y verificados mediante prueba rápida en Teams.

**Verificación:** El comportamiento del agente después del refinamiento debe resolver los problemas identificados en las simulaciones.

---

#### Paso 4.5 — Discusión: Consideraciones Éticas y Operativas

**Objetivo:** Reflexionar sobre las implicaciones del uso de agentes de IA en atención al cliente logístico.

**Instrucciones:**

1. En grupo (o de forma individual si es práctica autodirigida), discute o anota tus respuestas a las siguientes preguntas:

   **Consideraciones éticas:**
   ```
   1. ¿En qué situaciones es éticamente correcto que un 
      agente de IA responda sin supervisión humana?
      
   2. ¿Cómo debe el agente comunicar claramente al cliente 
      que está hablando con un bot y no con una persona?
      (Nota: En muchas jurisdicciones esto es obligatorio 
      por ley. ¿Tu mensaje de bienvenida lo hace?)
      
   3. ¿Qué datos del cliente recopila el agente durante 
      la conversación? ¿Cómo se almacenan y protegen?
   ```

   **Consideraciones operativas:**
   ```
   4. ¿Qué métricas usarías para medir el éxito del 
      agente en producción? (Tasa de resolución, 
      satisfacción del cliente, tasa de escalación)
      
   5. ¿Cómo manejarías la actualización del agente cuando 
      cambien las políticas de entrega o los transportistas?
      
   6. ¿Qué plan de contingencia tendrías si el agente 
      falla durante un pico de operación (ej. temporada alta)?
   ```

2. Documenta al menos **3 conclusiones** en el documento de diseño del agente, sección **"Consideraciones Finales"**.

**Resultado esperado:** Documento de diseño completo con sección de consideraciones éticas y operativas documentada.

---

## Validación y Pruebas

### Lista de Verificación Final

Antes de considerar la práctica completa, verifica cada elemento:

| # | Elemento de Verificación | Estado |
|---|--------------------------|--------|
| 1 | Agente "LogiBot" creado y publicado en Copilot Studio | ☐ |
| 2 | Tema de Bienvenida con menú de 4 opciones funcional | ☐ |
| 3 | Tema de Seguimiento de Pedido con 2 variables y 3 ramas | ☐ |
| 4 | Tema de Reporte de Incidencia con generación de número de caso | ☐ |
| 5 | Tema de Reprogramación de Entrega con 3 variables | ☐ |
| 6 | Escalación a agente humano funcional desde al menos 2 temas | ☐ |
| 7 | Agente integrado y accesible en Microsoft Teams | ☐ |
| 8 | Flujo de notificación automática en Power Automate configurado | ☐ |
| 9 | Mensaje de notificación recibido en Teams y Outlook | ☐ |
| 10 | 3 conversaciones de prueba ejecutadas y documentadas | ☐ |
| 11 | Al menos 2 refinamientos aplicados y verificados | ☐ |
| 12 | Sección de consideraciones éticas completada | ☐ |

### Prueba de Aceptación Final

Ejecuta esta secuencia de prueba completa como validación final:

```
PRUEBA DE ACEPTACIÓN — LogiBot

1. En Teams, escribe: "Hola"
   ✅ Esperado: Mensaje de bienvenida con menú de 4 opciones

2. Selecciona: "Seguimiento de pedido"
   ✅ Esperado: Solicitud de número de pedido

3. Escribe: "PED-2024-0100"
   ✅ Esperado: Solicitud de nombre del cliente

4. Escribe: "Empresa de Prueba Final"
   ✅ Esperado: Mensaje de estado con nombre del cliente incluido

5. Escribe: "hablar con agente"
   ✅ Esperado: Mensaje de transferencia con contexto

6. Inicia nueva conversación y escribe: "pedido dañado"
   ✅ Esperado: Activación del tema de Reporte de Incidencia

7. Completa el flujo de incidencia
   ✅ Esperado: Número de caso generado (INC-PED-2024-0100-001 o similar)
```

---

## Solución de Problemas

### Problema 1: El agente no aparece en Microsoft Teams después de la publicación

**Síntomas:**
- Después de hacer clic en "Agregar a Teams" en Copilot Studio, el agente no aparece en la lista de aplicaciones de Teams.
- La búsqueda de "LogiBot" en Teams no devuelve resultados.
- El enlace de instalación generado por Copilot Studio muestra un error al abrirlo en Teams.

**Causa:**
Este problema ocurre típicamente por una de tres razones: (1) Las políticas de aplicaciones del tenant de Teams restringen la instalación de aplicaciones personalizadas o de terceros. (2) El agente fue publicado pero el canal de Teams no fue configurado correctamente antes de la publicación (el canal debe configurarse antes de publicar, no después). (3) Hay un retraso de propagación de hasta 15 minutos entre la publicación en Copilot Studio y la disponibilidad en Teams.

**Solución:**
```
PASO 1 — Verificar políticas de Teams:
1. El administrador de Teams debe navegar a:
   https://admin.teams.microsoft.com
2. Ir a: Aplicaciones de Teams → Directivas de configuración
3. Verificar que la directiva asignada al usuario permita
   "Cargar aplicaciones personalizadas".
4. Si no está habilitado, el administrador debe activar
   "Permitir cargar aplicaciones personalizadas" en la
   directiva correspondiente.

PASO 2 — Reconfigurar el canal antes de republicar:
1. En Copilot Studio, ve al agente → Canales → Microsoft Teams.
2. Elimina la configuración actual del canal Teams.
3. Reconfigura el canal con los datos correctos.
4. Guarda la configuración del canal ANTES de hacer clic en "Publicar".
5. Luego publica el agente.

PASO 3 — Esperar y reintentar:
1. Espera 15 minutos después de la publicación.
2. En Teams, cierra sesión y vuelve a iniciar sesión.
3. Busca nuevamente "LogiBot" en Aplicaciones.
4. Si persiste, usa el enlace directo de instalación
   generado por Copilot Studio.
```

---

### Problema 2: Las variables de conversación no se muestran en los mensajes del agente (aparecen como texto plano `{NumeroPedido}`)

**Síntomas:**
- En el panel de prueba o en Teams, los mensajes del agente muestran literalmente `{NumeroPedido}` o `{NombreCliente}` en lugar del valor capturado.
- El agente solicita correctamente los datos al usuario, pero no los utiliza en los mensajes posteriores.
- El número de caso generado muestra `INC-{NumeroPedidoIncidencia}-001` en lugar del número real.

**Causa:**
Este problema se presenta cuando las variables en los nodos de mensaje no están referenciadas correctamente mediante la sintaxis de variables de Copilot Studio. En lugar de usar el selector de variables de la interfaz, el texto fue escrito manualmente como texto plano entre llaves, lo cual no activa la interpolación de variables del sistema. También puede ocurrir si la variable fue creada con un nombre diferente al referenciado en el mensaje.

**Solución:**
```
PASO 1 — Verificar nombres exactos de variables:
1. En Copilot Studio, ve al Tema afectado.
2. Haz clic en el nodo de Pregunta donde se captura la variable.
3. Anota el nombre EXACTO de la variable (respeta mayúsculas,
   minúsculas y espacios). Ejemplo: "NumeroPedido" ≠ "numeropedido".

PASO 2 — Referenciar variables correctamente en mensajes:
1. Haz clic en el nodo de Mensaje donde la variable no se muestra.
2. En el editor de texto, posiciona el cursor donde debe
   aparecer el valor de la variable.
3. Haz clic en el ícono "{x}" (Insertar variable) en la 
   barra de herramientas del editor de mensajes.
4. Selecciona la variable correcta de la lista desplegable.
5. El sistema insertará la referencia en formato correcto
   (puede ser diferente a {NombreVariable} dependiendo
   de la versión de Copilot Studio).
6. NO escribas las llaves manualmente; usa siempre el
   selector de variables de la interfaz.

PASO 3 — Verificar con prueba inmediata:
1. Guarda el tema modificado.
2. En el panel de prueba, ejecuta el flujo completo.
3. Confirma que el valor capturado aparece correctamente
   en el mensaje de confirmación.
```

---

## Limpieza del Entorno

> ⚠️ **Importante:** Realiza los pasos de limpieza solo si el instructor lo indica explícitamente o si el entorno de práctica debe ser restaurado para otro grupo. Si deseas conservar el agente para referencia futura, omite los pasos de eliminación.

### Limpieza Opcional del Agente

```
OPCIÓN A — Desactivar el agente (recomendado para conservar el trabajo):
1. En Copilot Studio, navega al agente "LogiBot".
2. Haz clic en "..." → "Desactivar agente".
3. El agente queda en estado inactivo pero conserva 
   toda la configuración.

OPCIÓN B — Eliminar el agente (limpieza completa):
1. En Copilot Studio, navega al agente "LogiBot".
2. Haz clic en "..." → "Eliminar".
3. Confirma la eliminación en el cuadro de diálogo.
⚠️ Esta acción es irreversible.
```

### Limpieza de Teams

```
1. En Microsoft Teams, ve a Aplicaciones.
2. Localiza "LogiBot — Pedidos".
3. Haz clic derecho → "Desinstalar" o "Quitar".
4. Confirma la desinstalación.
```

### Limpieza de Power Automate

```
1. Navega a: https://make.powerautomate.com
2. En "Mis flujos", localiza: 
   "Notificación de Estado de Pedido - LogiBot".
3. Haz clic en "..." → "Eliminar".
4. Confirma la eliminación.
```

### Archivos Locales

```
Los archivos en C:\Labs\Practica4\ pueden conservarse 
como referencia. Si deseas limpiar:

1. Abre el Explorador de Archivos.
2. Navega a C:\Labs\Practica4\
3. Selecciona todos los archivos y elimínalos.
4. Vacía la Papelera de Reciclaje.
```

---

## Resumen

### Lo Que Construiste

En esta práctica de 60 minutos diseñaste y desplegaste un agente conversacional funcional de extremo a extremo para operaciones logísticas. Específicamente:

- **Arquitectura documentada:** Definiste el propósito, capacidades, limitaciones y árbol de conversación del agente antes de construirlo, aplicando el principio de diseño primero que garantiza coherencia en el flujo.

- **Agente funcional en Copilot Studio:** Construiste 4 temas principales (Bienvenida, Seguimiento de Pedido, Reporte de Incidencia, Reprogramación de Entrega) con variables de conversación, condiciones lógicas y escalación a agente humano — todo sin escribir código.

- **Integración con Teams:** Publicaste el agente y lo conectaste con Microsoft Teams, haciéndolo accesible como canal de atención interna para operaciones logísticas.

- **Automatización de notificaciones:** Configuraste un flujo en Power Automate que envía actualizaciones proactivas de estado de pedido tanto en Teams como en Outlook, integrando los conceptos de automatización administrativa de la Lección 4.1.

- **Validación mediante simulación:** Ejecutaste 3 conversaciones de cliente que cubren los escenarios operativos más críticos (pedido en tránsito, pedido retrasado, pedido con incidencia) y aplicaste refinamientos basados en los resultados.

### Conceptos Clave Aplicados

| Concepto | Aplicación en esta Práctica |
|----------|----------------------------|
| Automatización asistida por IA | Agente responde consultas sin intervención humana constante |
| Variables de conversación | Captura de NumeroPedido, NombreCliente, TipoIncidencia |
| Condiciones lógicas | Ramas de estado (En tránsito / Retrasado / No encontrado) |
| Escalación a agente humano | Activada por condición o solicitud explícita del usuario |
| Notificaciones proactivas | Flujo Power Automate → Teams + Outlook |
| Validación crítica de IA | Prueba de 3 escenarios y aplicación de refinamientos |
| Consideraciones éticas | Transparencia del bot, privacidad de datos, plan de contingencia |

### Conexión con el Curso

Esta práctica integra y eleva todo lo aprendido en el curso:
- Los **prompts estructurados** de la Práctica 1 son la base de las instrucciones del agente.
- Los **KPIs logísticos** de la Práctica 2 informan qué estados y métricas el agente debe comunicar.
- La **automatización en Teams y Outlook** de la Lección 4.1 se implementa concretamente en las notificaciones del agente.

### Recursos Adicionales

| Recurso | URL |
|---------|-----|
| Documentación oficial de Copilot Studio | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/](https://learn.microsoft.com/es-es/microsoft-copilot-studio/) |
| Guía de creación de temas en Copilot Studio | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-create-edit-topics](https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-create-edit-topics) |
| Integración de Copilot Studio con Teams | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams](https://learn.microsoft.com/es-es/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams) |
| Variables en Copilot Studio | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-variables](https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-variables) |
| Escalación a agente humano | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/advanced-hand-off](https://learn.microsoft.com/es-es/microsoft-copilot-studio/advanced-hand-off) |
| Mejores prácticas de diseño de agentes conversacionales | [https://learn.microsoft.com/es-es/microsoft-copilot-studio/guidance/](https://learn.microsoft.com/es-es/microsoft-copilot-studio/guidance/) |

---

> 🎓 **¡Felicitaciones!** Has completado las cuatro prácticas del curso. Ahora cuentas con las competencias para aplicar Microsoft 365 Copilot en flujos de trabajo logísticos reales: desde el diagnóstico y análisis de datos hasta la creación de agentes conversacionales autónomos de atención al cliente.

---
LAB_END---

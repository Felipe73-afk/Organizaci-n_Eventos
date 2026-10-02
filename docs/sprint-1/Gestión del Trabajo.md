# Gestión del Trabajo — Sprint 1

## Organizador de Eventos Independientes

## 1. Objetivo del Sprint 1

Permitir que una persona cree un evento con nombre, tipo y fecha, defina sus gestiones logísticas con título, plazo y horas estimadas, y cuente con validaciones y feedback claros. El sprint incluye la documentación técnica de la API con Swagger/OpenAPI, la interfaz para crear y gestionar el plan, las decisiones UX y la iteración documentada. El flujo completo React → API → base de datos fue verificado y se registra en la sección G1.

## 2. Historia de usuario

> Como persona que organiza un evento, quiero registrar el evento y sus gestiones logísticas con sus datos de planificación, para contar con un plan asociado y persistido y recibir feedback claro al trabajar con él.

Esta historia sintetiza el alcance oficial C1–C5 y G1 para organizar el trabajo de este documento. No se encontró una historia de usuario con esta redacción en los archivos del proyecto.

## 3. Desglose de tareas

### C1 — Creación y persistencia de eventos y gestiones

- Incorporar en el formulario los datos del evento: nombre, tipo y fecha.
- Permitir agregar gestiones con título, plazo y horas estimadas.
- Enviar los datos al endpoint de creación y persistir el evento y sus gestiones asociadas en SQLite.

### C2 — Validaciones y estados de interfaz

- Validar los datos del evento y cada gestión en el frontend antes del envío.
- Validar los datos recibidos en el backend y responder errores de validación.
- Mostrar estados de carga, éxito, error y vacío en las pantallas correspondientes.

### C3 — Documentación de la API

- Configurar la especificación OpenAPI 3.0 con `swagger-jsdoc` y el esquema Bearer JWT.
- Integrar Swagger UI en `/api/docs`.
- Documentar endpoints del alcance, sus cuerpos JSON y ejemplos de respuestas, incluidas respuestas `201` y `400` donde corresponden.

### C4 — Interfaz para creación y gestión logística

- Presentar los campos del evento y del plan logístico en el flujo de creación.
- Permitir editar los datos de las gestiones, agregarlas y quitarlas desde la interfaz disponible.
- Mostrar controles y etiquetas para título, plazo y horas estimadas.

### C5 — Decisiones UX e iteración

- Documentar dos decisiones UX del Sprint 1.
- Documentar una iteración real del formulario de creación y su verificación mediante revisión del código.

### C6 — Gestión del trabajo

- Organizar el alcance por criterio y tareas.
- Registrar criterios de aceptación, responsables o roles, estimaciones, estados, Definition of Done y evidencias.
- Distinguir evidencia de implementación, pruebas ejecutadas y evidencia pendiente.

### G1 — Verificación del flujo end-to-end

- Verificar desde React el envío de un evento y sus gestiones a la API.
- Confirmar que el backend persiste el evento y las gestiones asociadas en la base de datos.
- Confirmar la asociación consultando los datos persistidos después de la creación.

## 4. Criterios de aceptación

| Referencia | Criterios de aceptación |
|---|---|
| **C1** | El formulario permite ingresar nombre, tipo y fecha del evento y una o más gestiones con título, plazo y horas estimadas. El backend guarda el evento y cada gestión asociada al evento en la base de datos. |
| **C2** | Los datos incompletos o fuera de los límites implementados detienen el envío o producen una respuesta de validación del backend. La interfaz presenta estados visibles de carga, éxito, error y vacío en los flujos correspondientes. |
| **C3** | Swagger UI está disponible en `/api/docs`. La especificación OpenAPI incluye seguridad Bearer y documentación JSON de las operaciones del alcance, con ejemplos de respuestas `201` y `400` donde aplican. |
| **C4** | La pantalla de creación identifica los campos del evento y de las gestiones; permite editar, agregar y quitar gestiones, y muestra sus controles de plazo y horas. La vista de detalle permite gestionar las gestiones disponibles en el alcance. |
| **C5** | Existen dos decisiones UX documentadas y una iteración documentada con hallazgo, cambio y verificación. |
| **C6** | El documento organiza el trabajo C1–C6 y G1 e incluye criterios de aceptación, responsable/rol, estimación, estado, Definition of Done y evidencias, indicando explícitamente los datos no documentados. |
| **G1** | Un flujo iniciado desde React crea el evento a través de la API, persiste el evento y sus gestiones relacionadas en la base de datos y permite comprobar la asociación después de la creación. Verificado mediante la ejecución registrada en la sección G1. |

## 5. Responsable / rol

| Referencia | Responsable / rol |
|---|---|
| C1 | No documentado |
| C2 | No documentado |
| C3 | No documentado |
| C4 | No documentado |
| C5 | No documentado |
| C6 | No documentado |
| G1 | No documentado |

## 6. Estimación

| Referencia | Estimación |
|---|---|
| C1 | No documentado |
| C2 | No documentado |
| C3 | No documentado |
| C4 | No documentado |
| C5 | No documentado |
| C6 | No documentado |
| G1 | No documentado |

## 7. Estado

| Referencia | Estado |
|---|---|
| C1 | Completo |
| C2 | Completo |
| C3 | Completo técnicamente |
| C4 | Completo |
| C5 | Completo |
| C6 | En proceso |
| G1 | Completo — verificación end-to-end exitosa |

## 8. Definition of Done

**No documentada.** No se encontró una Definition of Done acordada en los documentos disponibles. No se establece aquí una regla nueva como si fuera oficial.

## 9. Evidencias

### Implementación existente

- **C1:** `frontend/src/pages/Crear.jsx` construye el envío con nombre, tipo, fecha y gestiones. `backend/routes/events.js` valida la creación y llama a `createEvent` y `createTask`. `backend/db.js` contiene inserciones SQL para eventos y gestiones, incluida la clave `event_id`.
- **C2:** `Crear.jsx` contiene validaciones y feedback del envío; `Eventos.jsx`, `EventoDetalle.jsx` y `frontend/src/components/States.jsx` implementan estados de carga, error, éxito y vacío. `events.js` contiene validaciones de backend y respuestas de error.
- **C3:** `backend/swagger.js` configura OpenAPI 3.0, `bearerAuth` y la búsqueda de documentación de rutas; `backend/app.js` integra Swagger UI en `/api/docs`; `backend/routes/events.js` contiene anotaciones para las operaciones documentadas de eventos y gestiones.
- **C4:** `Crear.jsx` implementa el formulario del evento y su plan logístico; `EventoDetalle.jsx` implementa la interfaz de gestión de las gestiones.
- **C5:** `docs/sprint-1/Decisiones de Diseño.md` y `docs/sprint-1/Bitácora de Iteración.md` contienen los documentos solicitados.

### Pruebas realizadas y artefactos de prueba

- No se ejecutó la suite automatizada `backend/test-e2e.js`. La verificación manual end-to-end realizada para G1 se documenta abajo; no se presenta como resultado de esa suite.
- Existe `backend/test-e2e.js`, pero su código no acredita una ejecución exitosa. Además, el payload de creación usado en ese archivo no incluye `type` ni `date`, que el handler actual requiere; y una aserción espera `422` para la creación sin gestiones, mientras el handler actual responde `400`. Por ello, este archivo requiere alineación y ejecución antes de usarlo como evidencia de aceptación del flujo actual.
- La revisión estática del código y de la especificación Swagger no sustituye pruebas de ejecución. Para G1, además, se realizó y registró la verificación en React, las respuestas de la API y la consulta SQLite que aparece a continuación.

### G1 — Verificación End-to-End

- **Flujo comprobado:** `React → POST /api/events → SQLite → GET /api/events/:id → React`.
- **Evento creado:** `E2E Sprint 1` (ID `11`).
- **Gestión creada:** `Reservar salón E2E` (ID `24`).
- **Resultado del POST:** `POST /api/events` respondió `201 Created`; React recibió la respuesta y navegó al detalle del evento.
- **Resultado del GET:** `GET /api/events/11` respondió `200 OK` y devolvió el evento con la gestión asociada.
- **Relación comprobada:** `tasks.event_id = 11`.
- **Base de datos consultada:** `backend/data/organizador.db`.
- **Valores finales comprobados mediante GET y SQLite:** el evento tiene tipo `Conferencia`, fecha `2026-10-20` y descripción `Verificación end-to-end Sprint 1`; la gestión tiene plazo `2026-10-10` y `2` horas estimadas.
- **Incidencia de codificación:** la primera entrada automatizada codificó incorrectamente los acentos de la descripción y el título. Ambos valores se corrigieron desde la interfaz React y los valores finales se confirmaron mediante GET y SQLite.
- **Incidencia de host:** el primer acceso se realizó mediante `127.0.0.1`, lo que hizo que el frontend intentara utilizar la URL de API de producción. La verificación válida continuó mediante `localhost` contra el backend local.
- **Resultado final:** verificación end-to-end exitosa después de las correcciones indicadas.

### Evidencia pendiente de generar

- Resultado de una prueba actualizada y ejecutada que cubra los campos requeridos del evento y sus gestiones.
- Si se requiere evidencia visual, generarla posteriormente. No se generaron capturas para este registro.

## 10. Pendientes

- **C6:** Confirmar o documentar responsables/roles, estimaciones y una Definition of Done acordada; el estado de C6 permanece en proceso.
- **Pruebas:** Alinear el artefacto `backend/test-e2e.js` con los campos y códigos de respuesta actuales y registrar su resultado de ejecución antes de presentarlo como evidencia.

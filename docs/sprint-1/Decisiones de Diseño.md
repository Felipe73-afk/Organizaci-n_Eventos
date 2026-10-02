# Decisiones de Diseño

## Sprint 1

### Decisión UX 1: Crear el evento junto con un plan logístico inicial

**Decisión**  
Reunir en un mismo formulario los datos del evento y la planificación de sus gestiones logísticas iniciales.

**Problema o necesidad que resuelve**  
Al crear un evento, la persona también necesita definir las primeras acciones para organizarlo. Capturar ambos elementos en el mismo flujo ayuda a comenzar el plan de trabajo de inmediato.

**Cómo se implementó**  
El formulario solicita nombre, tipo, fecha y una descripción opcional. Inicializa tres gestiones editables con título, plazo y horas estimadas; ofrece sugerencias, permite agregar gestiones y permite quitar una mientras se conserve al menos una. El plazo y las horas tienen controles de entrada, y el envío valida los datos de cada gestión.

**Resultado esperado para el usuario**  
La persona puede crear un evento acompañado de un plan inicial de trabajo y ajustar las gestiones antes de guardarlo.

**Evidencia en el código**  
`frontend/src/pages/Crear.jsx`: `emptyTask` y estado inicial de `tasks` (líneas 6 y 19); `SUGGESTED` y `onSuggested` (líneas 10 y 27); campos del evento, controles de gestiones y acciones para agregar o quitar (desde la línea 104); validación y envío en `onSubmit` (líneas 32–88). En `backend/routes/events.js`, el `POST /api/events` requiere de una a cincuenta gestiones y valida su título, plazo y horas (líneas 428–466).

### Decisión UX 2: Mostrar feedback claro durante las acciones y ante cada estado de la lista

**Decisión**  
Presentar feedback visible para los estados de carga, error, lista vacía y operación completada, con acciones útiles cuando corresponda.

**Problema o necesidad que resuelve**  
La persona necesita saber si el sistema está cargando, si una operación falló y cómo continuar cuando aún no hay eventos o gestiones.

**Cómo se implementó**  
La lista de eventos presenta un estado de carga, un error con opción para reintentar y, si no hay eventos, un mensaje con acceso a la creación. En el formulario, el botón de envío se deshabilita durante la petición y cambia su texto; los errores aparecen como alerta. Después de crear el evento, la vista de detalle muestra una confirmación. Las acciones de gestión también muestran mensajes de éxito.

**Resultado esperado para el usuario**  
La persona recibe una indicación visible del estado de la operación y puede identificar cómo continuar ante un error o una lista vacía.

**Evidencia en el código**  
`frontend/src/pages/Eventos.jsx`: estados de carga, error y lista vacía con acceso a crear (líneas 28–54). `frontend/src/components/States.jsx`: componentes accesibles `LoadingState`, `EmptyState`, `ErrorState` y `SuccessBanner` (líneas 1–39). `frontend/src/pages/Crear.jsx`: error con `role="alert"` y botón controlado por `busy` (líneas 95 y 220–221). `frontend/src/pages/EventoDetalle.jsx`: mensaje posterior a la creación, feedback de operaciones y estados de carga/error (líneas 25, 55–56, 82–96, 138–159).

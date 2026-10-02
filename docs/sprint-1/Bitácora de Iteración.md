# Bitácora de Iteración

## Sprint 1

### Validación de las gestiones logísticas al crear un evento

**Hallazgo**  
La implementación anterior de `onSubmit` filtraba las gestiones cuyo título tenía menos de dos caracteres. Para las gestiones restantes, podía enviar el plazo como `null` y sustituir las horas faltantes por `1`. Esto podía omitir silenciosamente gestiones incompletas o enviar datos que no cumplieran los requisitos del backend.

**Cambio**  
Se reemplazó el filtrado por una validación explícita de cada gestión: el título debe tener al menos dos caracteres, debe haber un plazo y las horas deben ser un número finito entre `0.25` y `24`. Si una gestión es inválida, se muestra un mensaje y se detiene el envío. Después de validar, `clean` mapea las gestiones sin asignar valores por defecto al plazo ni a las horas.

**Verificación**  
La revisión del código actual confirma que `frontend/src/pages/Crear.jsx`, en `onSubmit` (líneas 32–54), encuentra gestiones inválidas antes de construir `clean` y detiene el envío si encuentra una. En `backend/routes/events.js`, el endpoint de creación de eventos aplica validaciones correspondientes al título, al plazo y al rango de horas (líneas 442–466). Esta verificación se realizó mediante inspección del código; no se ejecutaron pruebas para esta documentación.

**Archivos relacionados**  
- `frontend/src/pages/Crear.jsx`
- `backend/routes/events.js`

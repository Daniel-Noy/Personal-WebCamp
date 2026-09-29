# US-07: Gestión de Eventos y Workshops (Backoffice)

- **Módulo:** Administración (Backoffice)
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-07-admin-events.md`

---

## Descripción

**Como** administrador del sistema  
**Quiero** crear, editar y organizar conferencias y talleres asignando fecha, categoría, ponente, bloque de horario y cupo disponible  
**Para** estructurar la agenda del evento y delimitar la capacidad física/virtual de cada sesión.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Creación de nuevo evento/taller

- **Dado** que he iniciado sesión como Administrador
- **Cuando** creo un evento especificando título, descripción, categoría (Conferencia / Workshop), día (Viernes / Sábado), horario, ponente y capacidad máxima (aforo)
- **Entonces** el evento queda programado en la base de datos
- **Y** su cupo disponible inicial es igual a la capacidad máxima definida
- **Y** queda visible en la agenda pública correspondiente.

### Escenario: Prevención de conflicto de horario por ponente

- **Dado** que un ponente ya tiene asignado un evento en el Día 1 en el bloque de 10:00 a 11:00
- **Cuando** intento asignarle otro evento en el mismo día y bloque horario
- **Entonces** el sistema arroja una alerta de conflicto de agenda y no permite guardar el evento solapado.

### Escenario: Actualización de aforo

- **Dado** que un evento tiene inscripciones registradas
- **Cuando** el administrador modifica la capacidad máxima a un número superior
- **Entonces** el número de cupos disponibles se recalcula proporcionalmente manteniendo la integridad.

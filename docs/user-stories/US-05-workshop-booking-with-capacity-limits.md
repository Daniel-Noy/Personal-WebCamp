# US-05: Reserva de Talleres con Control de Cupos

- **Módulo:** Registro a Eventos
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-05-workshop-booking.md`

---

## Descripción

**Como** asistente con Pase Presencial  
**Quiero** armar mi itinerario seleccionando hasta un máximo permitido de talleres y conferencias  
**Para** garantizar mi asiento en las sesiones de mi interés respetando el cupo de cada sala.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Inscripción exitosa a un taller con cupo disponible

- **Dado** que poseo un pase presencial y un evento tiene cupos disponibles (`available_slots > 0`)
- **Cuando** solicito inscribirme al evento
- **Entonces** el sistema registra mi inscripción
- **Y** decrementa en 1 el contador de cupos disponibles de ese evento
- **Y** el evento aparece en mi lista personal de eventos agendados.

### Escenario: Intento de inscripción en evento agotado

- **Dado** que un evento tiene 0 cupos disponibles (`available_slots == 0`)
- **Cuando** intento registrarme a dicho evento
- **Entonces** la acción es rechazada con un mensaje de "Cupos agotados"
- **Y** la base de datos no sufre modificaciones de sobrecupo.

### Escenario: Límite máximo de eventos alcanzado

- **Dado** que ya he reservado el número máximo permitido de eventos para mi boleto (ej. 5 eventos)
- **Cuando** intento seleccionar un evento adicional
- **Entonces** el sistema bloquea la acción indicando que he alcanzado el límite permitido de reservas.

### Escenario: Cancelación o liberación de reserva

- **Dado** que tengo un evento previamente reservado
- **Cuando** decido cancelar mi inscripción a ese evento
- **Entonces** se elimina el registro de mi inscripción
- **Y** se incrementa en 1 el cupo disponible del evento.

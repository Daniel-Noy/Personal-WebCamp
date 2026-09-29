# US-08: Monitoreo de Asistentes y Boletos Emitidos

- **Módulo:** Administración (Backoffice)
- **Prioridad:** Media / Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-08-admin-attendees.md`

---

## Descripción

**Como** administrador del evento  
**Quiero** consultar la lista de asistentes registrados con sus pases, tokens y regalos asignados  
**Para** supervisar la emisión de boletos y verificar la legitimidad de un asistente.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Listado de asistentes y filtrado
- **Dado** que he iniciado sesión como Administrador
- **Cuando** accedo a la sección `/admin/registrados`
- **Entonces** observo la tabla paginada de asistentes con su nombre, email, tipo de pase (Presencial, Virtual, Gratis), código/token del boleto y regalo elegido.

### Escenario: Búsqueda rápida por token o correo
- **Dado** que busco un asistente específico
- **Cuando** ingreso su token de boleto o dirección de correo en el buscador
- **Entonces** la lista filtra en tiempo real mostrando únicamente los registros coincidentes.

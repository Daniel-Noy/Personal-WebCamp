# US-03: Visualización de Boleto Digital en Panel de Asistente

- **Módulo:** Panel de Asistente
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-03-ticket-dashboard.md`

---

## Descripción

**Como** asistente registrado que cuenta con un pase adquirido  
**Quiero** visualizar mi boleto digital con su código/token único e información del pase  
**Para** presentar mi credencial de acceso físico o virtual al evento.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Asistente con boleto activo

- **Dado** que he iniciado sesión y poseo un boleto emitido (presencial, virtual o gratis)
- **Cuando** accedo a la sección `/boleto` o al panel principal
- **Entonces** visualizo mi boleto digital mostrando:
    - Nombre completo del titular
    - Tipo de pase (Presencial / Virtual / Gratuito)
    - Token o código alfanumérico único generado
    - Regalo seleccionado (si es pase presencial).

### Escenario: Asistente sin boleto adquirido

- **Dado** que he iniciado sesión pero aún no he completado la adquisición de ningún boleto
- **Cuando** accedo a mi panel de control
- **Entonces** el sistema me muestra un llamado a la acción invitándome a seleccionar y adquirir un paquete de acceso.

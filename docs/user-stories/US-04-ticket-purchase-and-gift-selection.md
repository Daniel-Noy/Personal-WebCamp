# US-04: Adquisición de Pases y Selección de Regalo

- **Módulo:** Venta de Boletos / Checkout
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-04-ticket-purchase.md`

---

## Descripción

**Como** usuario autenticado  
**Quiero** seleccionar un tipo de pase (Presencial, Virtual o Gratuito), elegir mi regalo promocional (si aplica) y confirmar la adquisición  
**Para** asegurar mi participación oficial en el evento.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Registro en Pase Gratuito

- **Dado** que soy un usuario autenticado sin boleto previo
- **Cuando** selecciono la opción "Pase Gratuito" y confirmo mi registro
- **Entonces** el sistema emite inmediatamente un boleto con tipo `gratis` y token único
- **Y** soy redirigido a mi panel para ver mi boleto digital.

### Escenario: Adquisición de Pase Presencial con selección de regalo

- **Dado** que soy un usuario autenticado adquiriendo un pase presencial
- **Cuando** elijo mi regalo conmemorativo disponible (ej. Playera con talla) y confirmo el pago/orden
- **Entonces** se registra la compra con el paquete `presencial`
- **Y** se asocia el regalo seleccionado al registro del boleto
- **Y** se descuenta o contabiliza la demanda del regalo elegido.

### Escenario: Prevención de doble compra de pase

- **Dado** que ya cuento con un pase activo emitido
- **Cuando** intento iniciar un nuevo flujo de compra de boleto
- **Entonces** el sistema me notifica que ya cuento con un pase activo y me redirige a la gestión de mi boleto existente.

# Definición del MVP - DevWebCamp

Definición del alcance y objetivo del Producto Mínimo Viable (MVP) para la plataforma **DevWebCamp**, derivado de la visión general en [README.md](file:///C:/Users/pepe_/Files/Dev/Port/devcamp/README.md).

---

## 1. Declaración de Objetivo del MVP

> **Proveer una plataforma web centralizada y funcional que permita la promoción de la conferencia, la adquisición y generación de boletos digitales (presencial, virtual y gratuito), la reserva de conferencias y workshops con cupos limitados en tiempo real, y un panel administrativo básico para la gestión de ponentes y eventos.**

---

## 2. Problema y Solución

| Problema | Solución MVP |
| :--- | :--- |
| Dispersión de información del evento y ponentes. | Portal público con landing page, agenda segmentada por día y catálogo de ponentes. |
| Gestión desordenada de cupos en talleres. | Registro digital con control de aforo en tiempo real (bloqueo automático al agotarse). |
| Falta de trazabilidad y validación de asistentes. | Emisión de boleto digital con token/código único por asistente. |
| Complejidad en la administración manual. | Backoffice administrativo para alta y edición de ponentes, horarios y eventos. |

---

## 3. Alcance del MVP (In-Scope vs Out-of-Scope)

### ✅ Dentro del Alcance (MVP Core)

1. **Portal Público:**
   - Landing page informativa (fechas, cronograma y tabla comparativa de pases).
   - Catálogo de ponentes (foto, bio, tags y redes).
   - Visualización del cronograma (Viernes / Sábado) organizado por bloques de horarios y categorías.

2. **Autenticación y Cuentas:**
   - Registro e inicio de sesión de usuarios (Laravel Fortify).
   - Panel de asistente: visualización del boleto digital con identificador único.

3. **Adquisición de Boletos y Selección de Talleres:**
   - Selección de tipo de pase: Presencial, Virtual o Gratuito.
   - Flujo de pago o adquisición gratuita de boleto.
   - Selección de regalo conmemorativo para pases presenciales.
   - Reserva de talleres/conferencias con verificación de cupo disponible por evento.

4. **Panel de Administración (Backoffice):**
   - Autenticación de administradores protegida por middleware/roles.
   - CRUD de Ponentes (nombre, bio, redes, imagen).
   - CRUD de Eventos (título, categoría, día, bloque horario, ponente y cupo máximo).
   - Listado de asistentes y boletos emitidos.

---

### ⏸️ Fuera del Alcance Inicial (Post-MVP)

- Métricas y dashboards analíticos complejos en tiempo real.
- Autenticación avanzada con Passkeys / WebAuthn (se mantiene auth estándar + 2FA básico).
- Escáner QR móvil para acreditación física en la puerta.
- Streaming de video incrustado directamente en la plataforma.

---

## 4. Criterios de Éxito del MVP

1. **Flujo de Usuario Completo:** Un usuario puede registrarse, obtener un pase presencial, elegir su regalo, agendar sus talleres sin solapamiento de horarios y ver su boleto con token único.
2. **Consistencia de Cupos:** El sistema no permite sobrecupo en ningún evento (control de concurrencia e integridad en base de datos).
3. **Autonomía Administrativa:** El equipo organizador puede dar de alta nuevos ponentes y horarios desde el backoffice sin intervención técnica directa en base de datos.
4. **Calidad y Cobertura:** Suites de prueba en Pest cubriendo los flujos críticos (compra/registro, reserva de cupos, reglas de negocio de eventos).

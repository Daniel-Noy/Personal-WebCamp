# DevWebCamp

Plataforma integral para la gestión, promoción y venta de accesos a eventos y conferencias tecnológicas (presenciales y virtuales).

---

## 🎯 Objetivo del Proyecto

Centralizar en una sola aplicación web la experiencia completa de una conferencia tech de varios días:

- La difusión pública del evento, ponentes y agenda.
- La compra de accesos/boletos e inscripción a conferencias y workshops según disponibilidad.
- La administración y monitoreo de ponentes, horarios, cupos, regalos y métricas en tiempo real.

---

## 🚀 Módulos y Funcionalidades

### 1. Portal Público

- **Landing Page Informativa:** Presentación del evento, fechas, cuenta regresiva interactiva, ubicación y propuesta de valor.
- **Catálogo de Ponentes:** Perfiles detallados de conferencistas (biografía, áreas de especialidad/tags y redes sociales).
- **Agenda / Cronograma:** Calendario de conferencias y workshops segmentados por día (Viernes, Sábado), bloques de horarios y categorías.
- **Pases y Paquetes:** Comparativa de tipos de acceso:
    - **Pase Presencial:** Acceso completo a charlas, talleres, regalo conmemorativo y credencial.
    - **Pase Virtual:** Acceso vía streaming a conferencias y talleres.
    - **Pase Gratuito:** Acceso general limitado a conferencias vía streaming.

### 2. Autenticación y Cuentas de Usuario

- Registro de asistentes, confirmación de correo y restablecimiento de contraseña (con Laravel Fortify).
- Perfil de usuario con gestión de credenciales y autenticación en dos factores (2FA / Passkeys).
- Panel de Asistente: visualización del boleto digital con código único / token y formato de credencial imprimible.

### 3. Registro a Eventos y Venta de Boletos

- **Checkout e Integración de Pagos:** Flujo de pago para la adquisición de boletos de pago (PayPal / Pasarelas de pago) o registro inmediato en pases gratuitos.
- **Selección de Regalos:** Elección de artículos promocionales (camisetas con talla, stickers, pines) para los asistentes presenciales.
- **Reserva de Talleres y Conferencias:** Los usuarios con pase presencial pueden armar su agenda seleccionando hasta un número máximo de eventos sujetos a cupo limitado en tiempo real.

### 4. Panel de Administración (Backoffice)

- **Métricas y Estadísticas:** Resumen de ingresos generados, total de asistentes registrados, desglose por tipo de pase y demanda de regalos.
- **Gestión de Ponentes:** CRUD completo con carga optimizada de imágenes, redes sociales y etiquetas tecnológicas.
- **Gestión de Eventos:** CRUD de charlas y workshops asignando categoría, ponente, día, horario y límite de disponibilidad/aforo.
- **Gestión de Asistentes:** Listado y búsqueda de participantes, tipos de acceso adquiridos y estado de sus boletos.
- **Control de Regalos:** Monitoreo de regalos más solicitados para control de inventario.

---

## 🛠️ Stack Tecnológico

- **Backend:** PHP 8.3+ / Laravel (Modelos Eloquent, Migraciones, Seeders, Policies, Fortify)
- **Frontend:** React 19, TypeScript, Inertia.js v3, Tailwind CSS v4, Lucide Icons, Radix UI
- **Base de Datos:** SQLite / MySQL / PostgreSQL
- **Rutas Tipadas:** Laravel Wayfinder

---

## 💻 Entorno de Desarrollo

### Requisitos Previos

Asegúrate de tener instaladas las siguientes herramientas:

- **PHP >= 8.3** (con extensiones `pdo`, `sqlite3`, `mbstring`, `openssl`, `curl`)
- **Composer** (gestor de dependencias de PHP)
- **Node.js >= 20.x** y **npm**

---

### Instalación Rápida

El proyecto incluye un script automatizado para la configuración inicial:

```bash
composer run setup
```

Este comando realiza las siguientes tareas de forma automática:

1. Instala dependencias de PHP (`composer install`).
2. Crea el archivo `.env` a partir de `.env.example`.
3. Genera la clave de la aplicación (`php artisan key:generate`).
4. Ejecuta las migraciones de base de datos (`php artisan migrate --force`).
5. Instala dependencias de JavaScript (`npm install`).
6. Compila los assets iniciales (`npm run build`).

---

### Instalación Paso a Paso

Si prefieres realizar el proceso manualmente:

1. **Instalar dependencias de PHP y Node:**

    ```bash
    composer install
    npm install
    ```

2. **Configurar variables de entorno:**

    ```bash
    cp .env.example .env
    # En Windows PowerShell:
    # copy .env.example .env
    ```

3. **Generar la clave de la aplicación:**

    ```bash
    php artisan key:generate
    ```

4. **Configurar la base de datos:**
   Por defecto, el proyecto utiliza SQLite. Crea el archivo de base de datos si no existe:

    ```bash
    # En Linux/macOS:
    touch database/database.sqlite

    # En Windows PowerShell:
    New-Item -ItemType File -Path database/database.sqlite -Force
    ```

5. **Ejecutar migraciones (y datos de prueba):**
    ```bash
    php artisan migrate --seed
    ```

---

### Ejecutar el Proyecto

Para iniciar tanto el servidor de desarrollo de Laravel como Vite de manera concurrente:

```bash
composer run dev
```

> Alternativamente, puedes ejecutar `php artisan dev`. La aplicación estará disponible en [http://localhost:8000](http://localhost:8000).

#### Ejecución en terminales separadas (opcional)

Si requieres correr los procesos de forma independiente:

- **Servidor Laravel:**
    ```bash
    php artisan serve
    ```
- **Compilador Vite:**
    ```bash
    npm run dev
    ```

---

### Comandos Útiles

- **Pruebas:**
    ```bash
    php artisan test
    # o con Pest directamente:
    vendor/bin/pest
    ```
- **Linter de código PHP (Laravel Pint):**
    ```bash
    composer lint
    # o para verificar sin modificar:
    composer lint:check
    ```
- **Verificación de tipos TypeScript:**
    ```bash
    npm run types:check
    ```

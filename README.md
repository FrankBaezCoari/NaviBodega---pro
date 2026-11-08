# 🛒 NaviBodega Pro - Sistema de Pedidos y Tienda de Abarrotes

Un sistema web completo, profesional y modular para la gestión de víveres, abarrotes y suministros (con precios por kilo, enlatados, galletas, verduras y carnes).

Desarrollado para ser **robusto, seguro y 100% portable**, sin dependencias externas complejas ni configuraciones complicadas de bases de datos.

---

## 📋 Requisitos para Ejecutar el Proyecto

Para que cualquier persona pueda ejecutar esta aplicación en su computadora, solo necesita cumplir con lo siguiente:

### 1. Requisitos Obligatorios
| Requisito | Detalle | ¿Dónde conseguirlo? |
| :--- | :--- | :--- |
| **Node.js** | Versión **18, 20, 22 o 24 LTS** (Recomendado Node 22 o 24 por soporte SQLite nativo). | Descarga gratuita oficial en [nodejs.org](https://nodejs.org/). |
| **Navegador Web** | Cualquier navegador moderno: Chrome, Edge, Firefox, Brave o Safari. | Ya viene preinstalado en cualquier sistema. |

### 2. Conexión a Internet
* **Ligera conexión a Internet** en la primera carga para renderizar los iconos de interfaz (*FontAwesome*) y el diseño visual (*Tailwind CSS*) a través de sus CDN oficiales.
* El backend, la base de datos SQLite y la API REST corren **100% en local** (`localhost:3000`).

### 3. Ventajas Clave (Lo que NO necesitas instalar)
* ❌ **NO requiere `npm install`:** Cero paquetes pesados de npm. Todo el servidor, enrutador y base de datos fueron creados usando módulos estándar nativos de Node.js.
* ❌ **NO requiere XAMPP, MySQL ni Postgres:** La base de datos es un archivo local SQLite (`data/navibodega.db`) que viene preconfigurado y no requiere configuración de servidores.
* ❌ **NO requiere compiladores C++:** Funciona al instante en cualquier computadora sin errores de instalación.

---

## 🌟 Características Principales

### 1. 🔐 Autenticación y Control de Acceso por Roles (RBAC)
- **Login Inicial Limpio**: Inicio de sesión seguro con contraseñas cifradas (*Scrypt*) y tokens de sesión criptográficos (*HMAC-SHA256*).
- **Creación de Cuenta para Clientes**: Formulario de registro simplificado para clientes y capitanes con:
  - Nombre completo del responsable.
  - Empresa (opcional).
  - Teléfono.
  - Nombre de la embarcación.
  - Correo electrónico y contraseña.
- **División de Vistas según el Rol**:
  - **Cliente**: Accede a su catálogo de víveres, carrito de pedidos, registro de datos de embarcación (nombre, responsable, fecha de zarpado) y seguimiento de pedidos con aprobación de cotizaciones.
  - **Administrador**: Panel de administración de bodega, control de inventario y stock, ajuste de precios en Soles (S/) por ítem y emisión de guías de entrega.

### 2. 🇵🇪 Moneda Oficial: Soles (S/)
- Todos los precios, subtotales, costos de envío/entrega y totales de pedidos están calculados y expresados en **Soles (S/)**.

### 3. ⚓ Portal del Cliente
- **Catálogo de Productos y Víveres**:
  - *Víveres Secos y Granos* (Arroz, azúcar, fideos, menestras, aceite, harina).
  - *Frescos y Carnes* (Carne de res, pollo, cerdo, verduras, huevos, quesos).
  - *Bebidas y Agua* (Bidones de agua 20L, botellas personales, rehidratantes, café).
  - *Limpieza* (Detergente industrial, jabón líquido, bolsas de basura, papel).
  - *Seguridad y Herramientas* (Cabos de maniobra, guantes de trabajo, chalecos salvavidas).
- **Datos de la Embarcación Simplificados**:
  - Únicamente requiere: **Nombre de la Embarcación**, **Capitán / Responsable** y **Fecha Estimada de Zarpado** *(no se requiere matrícula ni sitio de atraque)*.
- **Aprobación de Cotizaciones**:
  - Cuando la bodega cotiza el pedido en Soles, el cliente puede revisar el detalle y **Aprobar la Cotización** directamente con un solo clic.

### 4. 📦 Portal de Administración de Bodega
- **Dashboard Ejecutivo (en Soles S/)**:
  - Pedidos por cotizar.
  - Pedidos cotizados en espera de aprobación.
  - Pedidos en preparación.
  - Pedidos entregados.
  - Facturación total en Soles (S/).
  - Alertas de stock bajo.
- **Gestión de Cotizaciones**:
  - Ajuste de precio unitario por cada producto en Soles.
  - Costo de envío/entrega configurable.
  - Flujo de estados: *Pendiente* ➔ *Cotizado* ➔ *Aprobado* ➔ *En Preparación* ➔ *Listo* ➔ *Entregado*.
- **Control Maestro de Inventario**:
  - Agregar nuevos productos.
  - Editar precios y stock en tiempo real.
  - Eliminar productos.
- **Guía de Entrega Imprimible**:
  - Documento formal de entrega de víveres con campos de firma conforme y desglose en Soles (S/), compatible con impresión directa o PDF (`Ctrl + P`).

---

## 🚀 Cómo Ejecutar el Proyecto

### Requisitos
- Únicamente tener instalado **Node.js** (versión 18, 20, 22 o 24).
- No requiere instalar bases de datos externas (MySQL, Postgres, etc.) ni herramientas de compilación C++.

### Opción A: En Windows (Recomendado)
Haz doble clic en el archivo:
```bash
iniciar.bat
```
¡Listo! Se iniciará el servidor y se abrirá tu navegador automáticamente en `http://localhost:3000`.

### Opción B: Desde la Consola (Windows, Mac o Linux)
1. Abre tu terminal en la carpeta del proyecto:
```bash
cd navibodega-pro
```
2. Inicia el servidor:
```bash
npm start
# o directamente:
node server.js
```
3. Ingresa en tu navegador a:
```
http://localhost:3000
```

---

## 👥 Credenciales de Prueba Preconfiguradas

| Rol | Correo Electrónico | Contraseña | Perfil |
| :--- | :--- | :--- | :--- |
| **Administrador de Bodega** | `admin@navibodega.com` | `admin123` | Jefe de Bodega (Acceso total) |
| **Cliente / Embarcación** | `capitan@pesquero.com` | `cliente123` | Barco San Martín |
| **Nuevo Cliente** | *Registrar en pestaña "Crear Cuenta"* | *Tu contraseña* | Registro instantáneo |

---

## 📁 Estructura del Código

```
navibodega-pro/
├── server.js               # Servidor HTTP nativo con enrutador API REST y servidor de estáticos
├── db.js                   # Módulo de base de datos SQLite nativo con persistencia en Soles (S/)
├── data/                   # Directorio de persistencia de datos (base de datos SQLite)
│   └── navibodega.db
├── public/                 # Frontend de la aplicación web
│   ├── index.html          # Vista unificada (Login, Registro, Portal Cliente, Portal Admin, Modales)
│   ├── css/
│   │   └── style.css       # Estilos personalizados y reglas de impresión
│   └── js/
│       ├── api.js          # Cliente HTTP para comunicación con los endpoints REST
│       ├── auth.js         # Lógica de login, registro, manejo de tokens y sesión
│       ├── client.js       # Catálogo en Soles, carrito, checkout y pedidos
│       ├── admin.js        # Dashboard KPI, cotizador por ítem, control de stock y clientes
│       └── app.js          # Coordinador principal, toasts y guías imprimibles
├── package.json            # Configuración y comandos del proyecto
├── iniciar.bat             # Lanzador rápido de un solo clic para Windows
├── iniciar.sh              # Lanzador para Linux y macOS
└── README.md               # Esta documentación
```

---

## 📤 ¿Cómo Compartir el Proyecto a Otra Persona?

Para compartir este proyecto con un compañero, profesor o cliente:

1. **Comprime la carpeta `navibodega-pro` en un archivo `.zip`**:
   - También dispones del archivo ya comprimido `navibodega-pro.zip`.
2. **La persona que lo reciba solo necesita**:
   - Descomprimir el archivo zip.
   - Hacer doble clic en `iniciar.bat` (en Windows) o escribir `node server.js` en su terminal.
   - ¡No tiene que ejecutar instalaciones complejas ni configurar bases de datos! La base de datos SQLite se crea y se autogestiona sola.

---

© 2026 Bodega Marítima "El Puerto" & NaviBodega Pro. Todos los derechos reservados.

# Nicolett Studio Fantasy

Aplicación web de Nicolett Studio Fantasy. Permite consultar los servicios del salón, reservar horas con un abono de $5.000 y llevar la agenda, las fichas de atención y el inventario.

Proyecto de título Capstone APT 2026, Duoc UC, sección 003-D, grupo 9.

## Equipo

| Integrante | Responsabilidad |
|---|---|
| José Cueto Moreira | Scrum Master y desarrollo frontend |
| Benjamín Moya Meza | Product Owner y desarrollo backend |

Docente guía: Paz Constanza Morales Saavedra. Cliente: Nicolett Studio Fantasy, Buin, Región Metropolitana.

[Sitio del proyecto](https://nicolette-studio.vercel.app) 

El proyecto ya está funcionando en [nicolette-studio.vercel.app](https://nicolette-studio.vercel.app). Para verlo y probarlo, se puede entrar directamente al sitio sin instalarlo de forma local.

## Funciones

- Catálogo de servicios, precios y profesionales.
- Consulta de disponibilidad y reserva con abono mediante Flow.
- Acceso del personal con Firebase Authentication y permisos por rol.
- Agenda, fichas de atención, consumo de insumos e inventario.
- Galería de trabajos con aprobación de administración.
- Consulta de citas de la clienta mediante un código enviado a su correo.

## Tecnologías

El sitio está hecho con HTML, CSS y JavaScript. El servidor usa Node.js 24 y Express, con Firebase Authentication para el acceso del personal y Firestore para guardar los datos. Los abonos se pagan con Flow y los correos se envían con EmailJS.

## Estructura

| Ruta | Contenido |
|---|---|
| `index.html` | Página principal y contenedor de las vistas |
| `reset-password.html` | Recuperación de contraseñas |
| `css/` e `img/` | Estilos e imágenes |
| `js/app.js` | Navegación y generación de vistas |
| `js/main.js` | Eventos e inicialización de la interfaz |
| `js/mockData.js` | Acceso a datos y estado de la sesión mediante StorageHelper |
| `js/modules/` | Funciones de citas, clientas, inventario, autenticación e interfaz |
| `backend/` | API, servicios y pruebas |
| `api/index.js` | Entrada del servidor para Vercel |
| `firestore.rules` | Reglas de acceso a Firestore |
| `firebase.json` | Configuración de Firestore y sus emuladores |
| `vercel.json` | Instalación y rutas del despliegue |
| `iniciar_backend.bat` | Inicia el servidor en Windows |

## Desarrollo local

Se necesita Node.js 24. Desde esta carpeta, instalar las dependencias:

```powershell
npm ci
npm --prefix backend ci
```

Para trabajar con datos de prueba se usan los emuladores de Firebase. También se necesita Firebase CLI y Java compatible con el emulador de Firestore; se recomienda Java 21 o superior.

En una terminal, desde esta carpeta:

```powershell
firebase emulators:start --only auth,firestore --project demo-nicolett
```

En otra terminal, también desde esta carpeta:

```powershell
$env:LOCAL_FIREBASE_EMULATORS="1"
npm start
```

Abrir el sitio en `http://127.0.0.1:3000`. El panel de los emuladores queda en `http://127.0.0.1:4000`.

Los usuarios y los datos de prueba se crean desde el panel de los emuladores. En este modo los pagos externos están desactivados. Más detalles en [backend/EMULATORS.md](backend/EMULATORS.md).

## Pruebas

```powershell
npm --prefix backend test
```

Las pruebas con servicios simulados no comprueban pagos reales ni la configuración de Firebase en producción. Para comprobar la integración local deben estar iniciados los emuladores.

## Documentación

| Documento | Propósito |
|---|---|
| [backend/README.md](backend/README.md) | API y configuración del servidor |
| [backend/EMULATORS.md](backend/EMULATORS.md) | Uso de los emuladores de Firebase |
| [backend/SECURITY_SETUP.md](backend/SECURITY_SETUP.md) | Configuración de seguridad y preparación del entorno |
| [backend/BOOKING_NOTES.md](backend/BOOKING_NOTES.md) | Funcionamiento de las reservas |
| [backend/BOOKING_DIAGNOSIS.md](backend/BOOKING_DIAGNOSIS.md) | Revisión de datos y problemas de reservas |

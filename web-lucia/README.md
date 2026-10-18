# Web de Lucía Castro — Arquitectura · Pintura · Escenografía

Web profesional con servidor propio (Node.js + Express) y base de datos **MongoDB**.

## Qué guarda la base de datos

| Colección | Para qué sirve |
|---|---|
| `mensajes` | Lo que la gente envía desde el formulario de contacto (nombre, correo, teléfono, tema, mensaje, leído/no leído). |
| `obras` | Los cuadros de la sección Pintura: título, técnica, medidas, año, descripción, imagen, disponible/vendida, destacada, visible y orden. |
| `imagenes` | Las fotos de los cuadros subidas desde el panel (se guardan en la propia base de datos). |

La obra marcada como **destacada** aparece en `pintura.html`; el resto, en la galería de `pintura-mas.html`.
Si el servidor no responde, la web sigue funcionando y muestra los cuadros de ejemplo.

## Panel de administración — `/admin`

Lucía entra en `https://SU-DOMINIO/admin` con la clave `ADMIN_TOKEN` y puede:
- leer los mensajes, marcarlos como leídos, responder por correo y borrarlos;
- añadir, editar, ocultar o borrar cuadros y subir sus fotos (JPG, PNG o WEBP, máx. 8 MB).

## Estructura

```
web-lucia/
├── public/            ← la web (HTML, CSS, JS) y el panel admin.html
├── server/
│   ├── index.js       ← arranque del servidor
│   ├── app.js         ← Express: seguridad, rutas y web estática
│   ├── models/        ← esquemas de MongoDB (Mensaje, Obra, Imagen)
│   ├── routes/        ← API pública y API del panel
│   ├── seed.js        ← carga las obras de ejemplo
│   └── test/          ← pruebas automáticas
├── .env.example       ← variables de configuración
└── package.json
```

## Puesta en marcha en tu ordenador

Necesitas **Node.js 20 o superior**.

1. **Crea la base de datos** (gratis) en [MongoDB Atlas](https://www.mongodb.com/cloud/atlas):
   1. Crea un clúster gratuito (M0).
   2. En *Database Access*, crea un usuario con contraseña.
   3. En *Network Access*, permite el acceso (`0.0.0.0/0` si vas a publicar en Render).
   4. En *Connect → Drivers*, copia la cadena de conexión `mongodb+srv://...`.
2. **Configura el proyecto:**
   ```bash
   cd web-lucia
   npm install
   cp .env.example .env
   ```
   Abre `.env` y rellena `MONGODB_URI` (añade el nombre de la base, p. ej. `/lucia-castro`, antes del `?`)
   y `ADMIN_TOKEN`. Puedes generar una clave segura con:
   ```bash
   node -e "console.log(require('crypto').randomBytes(24).toString('base64url'))"
   ```
3. **Carga las obras de ejemplo** (opcional): `npm run seed`
4. **Arranca:** `npm start` y abre <http://localhost:3000> (panel en <http://localhost:3000/admin>).

## Publicar en internet gratis (sin comprar dominio)

La web queda en una dirección gratuita del tipo `https://lucia-castro.onrender.com`,
accesible desde cualquier ordenador o móvil. Coste: 0 €.

1. **Base de datos:** crea el clúster gratuito en MongoDB Atlas (pasos de arriba).
   En *Network Access* añade `0.0.0.0/0` (Render no tiene una IP fija) y copia la cadena
   `mongodb+srv://...`, añadiendo `/lucia-castro` antes del `?`.
2. **Render:** entra en [render.com](https://render.com) con tu cuenta de GitHub.
3. Pulsa **New → Blueprint**, elige este repositorio y la rama donde está la web.
   Render lee el archivo `render.yaml` de la raíz y lo configura todo solo.
4. Cuando lo pida, pega la cadena de MongoDB en `MONGODB_URI` y pulsa **Apply**.
5. En unos minutos la web estará en `https://lucia-castro.onrender.com`
   (si el nombre está cogido, Render añade unas letras al final).
6. La clave del panel la genera Render: *lucia-castro → Environment → ADMIN_TOKEN*.
   Con ella se entra en `https://lucia-castro.onrender.com/admin`.
7. Opcional: `npm run seed` en tu ordenador (con el `.env` apuntando a Atlas) carga las obras de ejemplo.

**A tener en cuenta del plan gratuito:** si nadie visita la web durante 15 minutos, Render la
"duerme", y la siguiente visita tarda alrededor de un minuto en cargar. Después va a velocidad normal.
Si más adelante queréis un dominio propio (`luciacastro.es`), se añade en *Settings → Custom Domains*
sin cambiar nada del código.

Sirve cualquier alojamiento de Node.js (Railway, Fly.io, un VPS…).
Si prefieres publicar la parte estática aparte (por ejemplo en GitHub Pages), pon la URL del servidor
en `apiUrl` dentro de `public/assets/config.js` y añade el dominio de la web a `CORS_ORIGIN` en el servidor.

## Personalizar

- **Contacto y portfolio:** `public/assets/config.js`. El portfolio apunta por defecto a
  `public/assets/portfolio-lucia-castro.pdf`; copia ahí el PDF o pon un enlace externo.
- **Textos:** en cada archivo `.html` de `public/`.
- **Cuadros:** desde el panel `/admin`.

## Seguridad incluida

- Panel protegido con clave (`ADMIN_TOKEN`, mínimo 16 caracteres; comparación segura).
- Límite de 5 mensajes cada 15 minutos por persona y campo trampa contra bots.
- Validación de todos los datos en el servidor y cabeceras de seguridad (Helmet, CSP).
- El archivo `.env` con las contraseñas nunca se sube a GitHub (`.gitignore`).

## Pruebas

```bash
npm test
```
Las pruebas con base de datos arrancan un MongoDB temporal automáticamente
(o usan `MONGODB_TEST_URI` si la defines). No tocan tu base de datos real.

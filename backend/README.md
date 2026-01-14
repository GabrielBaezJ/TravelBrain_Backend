# 🔧 TravelBrain Backend API

Backend REST API para TravelBrain - Sistema de planificación de viajes inteligente.

## 🚀 Stack Tecnológico

- **Node.js** 18+
- **Express.js** 5.2.1
- **MongoDB** con Mongoose
- **JWT** para autenticación
- **Bcrypt** para seguridad

## 📦 Instalación

```bash
npm install
```

## ⚙️ Configuración

Crea un archivo `.env` en la raíz:

```env
PORT=3004
NODE_ENV=development
MONGODB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/travel_brain
JWT_SECRET=tu_secreto_jwt_aqui
GOOGLE_CLIENT_ID=tu_google_client_id
FRONTEND_URL=http://localhost:5173
```

## 🎯 Iniciar Servidor

```bash
# Desarrollo
npm run dev

# Producción
npm start
```

El servidor estará disponible en: `http://localhost:3004`

## 📡 API Endpoints

### Autenticación
- `POST /api/auth/register` - Registrar usuario
- `POST /api/auth/login` - Iniciar sesión
- `POST /api/auth/logout` - Cerrar sesión
- `POST /api/auth/google` - Login con Google

### Usuarios
- `GET /api/users/profile` - Obtener perfil (requiere auth)
- `PUT /api/users/profile` - Actualizar perfil (requiere auth)
- `GET /api/users` - Listar usuarios (admin)

### Viajes
- `GET /api/trips` - Obtener viajes del usuario
- `POST /api/trips` - Crear nuevo viaje
- `GET /api/trips/:id` - Obtener viaje específico
- `PUT /api/trips/:id` - Actualizar viaje
- `DELETE /api/trips/:id` - Eliminar viaje

### Destinos
- `GET /api/destinations` - Obtener destinos
- `POST /api/destinations` - Crear destino
- `GET /api/destinations/search` - Buscar destinos

### Clima
- `GET /api/weather/:location` - Obtener clima de ubicación

### Favoritos
- `GET /api/favorites` - Obtener favoritos del usuario
- `POST /api/favorites` - Agregar a favoritos
- `DELETE /api/favorites/:id` - Eliminar de favoritos

## 📁 Estructura del Proyecto

```
backend/
├── models/              # Modelos de Mongoose
│   ├── users.js
│   ├── trips.js
│   ├── destinations.js
│   ├── weather.js
│   └── favorite_routes.js
├── routes/              # Rutas de la API
│   ├── authRoutes.js
│   ├── userRoutes.js
│   ├── tripRoutes.js
│   ├── destinationRoutes.js
│   ├── weatherRoutes.js
│   └── favoriteRoutes.js
├── utils/               # Utilidades
│   └── cache.js
├── server.js            # Punto de entrada
├── package.json
├── .env                 # Variables de entorno (no commit)
└── .env.example         # Ejemplo de variables
```

## 🔐 Autenticación

El API usa JWT (JSON Web Tokens) para autenticación. Incluye el token en el header:

```
Authorization: Bearer <tu_token_jwt>
```

## 🌍 Variables de Entorno

| Variable | Descripción | Requerido |
|----------|-------------|-----------|
| `PORT` | Puerto del servidor | No (default: 3004) |
| `NODE_ENV` | Entorno (development/production) | No |
| `MONGODB_URI` | URI de MongoDB | **Sí** |
| `JWT_SECRET` | Secret para JWT | **Sí** |
| `GOOGLE_CLIENT_ID` | Client ID de Google OAuth | No |
| `FRONTEND_URL` | URL del frontend para CORS | No |

## 🚀 Deployment en Render

1. Crea un nuevo Web Service en Render
2. Conecta este repositorio
3. Configura:
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Environment**: Node
4. Agrega las variables de entorno en Settings
5. Deploy!

### Variables de Entorno en Render
```
MONGODB_URI=tu_mongodb_uri
JWT_SECRET=tu_jwt_secret
NODE_ENV=production
FRONTEND_URL=https://tu-frontend.onrender.com
```

## 📊 Health Check

```bash
curl http://localhost:3004/api/health
```

Respuesta:
```json
{
  "status": "ok",
  "message": "TravelBrain Backend is running",
  "timestamp": "2026-01-14T..."
}
```

## 🧪 Testing

```bash
# Instalar dependencias de testing
npm install --save-dev jest supertest

# Ejecutar tests
npm test
```

## 🐛 Troubleshooting

### Error de conexión a MongoDB
- Verifica que la URI sea correcta
- Asegúrate de que tu IP esté en la whitelist de MongoDB Atlas
- Comprueba tu conexión a internet

### Puerto ya en uso
```bash
# Linux/Mac
lsof -i :3004
kill -9 <PID>

# Windows
netstat -ano | findstr :3004
taskkill /PID <PID> /F
```

## 📝 Licencia

ISC

## 👥 Contribuir

Pull requests son bienvenidos. Para cambios mayores, abre un issue primero.

---

**Backend desarrollado con ❤️ para TravelBrain**

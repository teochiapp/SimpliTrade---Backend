# 🚀 SimpleTrade Backend - Strapi API

Backend API para SimpleTrade, desarrollado con Strapi CMS para gestión de trades y datos de trading.

## 📋 Requisitos

- **Node.js**: v18.x o superior
- **npm**: v8.x o superior
- **Base de datos**: SQLite (desarrollo) / PostgreSQL (producción)

## 🔧 Instalación

```bash
# Instalar dependencias
npm install

# Crear archivo de configuración
cp .env.example .env

# Configurar variables de entorno en .env
# (Ver sección Variables de Entorno)

# Ejecutar migraciones
npm run build

# Iniciar en modo desarrollo
npm run develop
```

## 🌐 Variables de Entorno

Crear archivo `.env` con las siguientes variables:

```env
# Host y Puerto
HOST=0.0.0.0
PORT=1337

# Claves de seguridad (generar nuevas para producción)
APP_KEYS=your-app-keys-here
API_TOKEN_SALT=your-api-token-salt
ADMIN_JWT_SECRET=your-admin-jwt-secret
TRANSFER_TOKEN_SALT=your-transfer-token-salt
JWT_SECRET=your-jwt-secret

# Base de datos (SQLite para desarrollo)
DATABASE_CLIENT=sqlite
DATABASE_FILENAME=.tmp/data.db

# URLs del frontend (CORS)
STRAPI_ADMIN_CLIENT_URL=http://localhost:3000
STRAPI_ADMIN_CLIENT_PREVIEW_SECRET=your-preview-secret

# Para producción con PostgreSQL
# DATABASE_CLIENT=postgres
# DATABASE_HOST=localhost
# DATABASE_PORT=5432
# DATABASE_NAME=simpletrade
# DATABASE_USERNAME=your-username
# DATABASE_PASSWORD=your-password
# DATABASE_SSL=false
```

## 📦 Scripts Disponibles

```bash
# Desarrollo
npm run develop          # Iniciar en modo desarrollo
npm run start           # Iniciar en modo producción
npm run build           # Construir aplicación

# Strapi específico
npm run strapi          # CLI de Strapi
npm run strapi generate # Generar API/controllers
```

## 🏗️ Estructura del Proyecto

```
simpletrade-backend/
├── config/             # Configuración de Strapi
│   ├── admin.js       # Panel de administración
│   ├── api.js         # Configuración API
│   ├── database.js    # Base de datos
│   ├── middlewares.js # Middlewares (CORS, etc.)
│   ├── plugins.js     # Configuración de plugins
│   └── server.js      # Servidor
├── database/          # Base de datos SQLite
├── src/
│   ├── api/          # APIs personalizadas
│   │   └── trade/    # API de trades
│   ├── extensions/   # Extensiones de Strapi
│   └── middlewares/  # Middlewares personalizados
├── public/           # Archivos públicos
└── types/           # Tipos TypeScript generados
```

## 🔗 API Endpoints

### Trades
- `GET /api/trades` - Obtener todos los trades
- `POST /api/trades` - Crear nuevo trade
- `GET /api/trades/:id` - Obtener trade específico
- `PUT /api/trades/:id` - Actualizar trade
- `DELETE /api/trades/:id` - Eliminar trade

### Autenticación
- `POST /api/auth/local/register` - Registro de usuario
- `POST /api/auth/local` - Login de usuario

## 🔒 Configuración CORS

Para desarrollo local, el CORS está configurado para permitir `localhost:3000`.

Para producción, actualizar en `config/middlewares.js`:

```javascript
module.exports = [
  {
    name: 'strapi::cors',
    config: {
      origin: ['https://tu-frontend-domain.com'],
      methods: ['GET', 'POST', 'PUT', 'DELETE'],
    },
  },
  // ... otros middlewares
];
```

## 🚀 Deployment

### Preparación para Coolify

1. **Variables de entorno**: Configurar todas las variables en Coolify
2. **Base de datos**: Usar PostgreSQL para producción
3. **Build**: Coolify ejecutará `npm run build` automáticamente
4. **Start**: Comando de inicio `npm start`

### Variables para Coolify

```env
NODE_ENV=production
HOST=0.0.0.0
PORT=1337
DATABASE_CLIENT=postgres
DATABASE_HOST=tu-postgres-host
DATABASE_PORT=5432
DATABASE_NAME=simpletrade_prod
DATABASE_USERNAME=tu-usuario
DATABASE_PASSWORD=tu-password
STRAPI_ADMIN_CLIENT_URL=https://tu-frontend.app
```

## 🆘 Troubleshooting

### Error de base de datos
```bash
rm -rf .tmp/
npm run build
```

### Error de permisos
```bash
# Verificar permisos de archivos
chmod -R 755 .
```

### Error de CORS
- Verificar configuración en `config/middlewares.js`
- Asegurar que el frontend URL esté en la lista de orígenes permitidos

## 📝 Notas de Desarrollo

- **Admin Panel**: Accesible en `http://localhost:1337/admin`
- **API Docs**: Disponible en modo desarrollo
- **Database**: SQLite para desarrollo, PostgreSQL recomendado para producción
- **Security**: Cambiar todas las claves secretas para producción

## 🔧 Comandos Útiles

```bash
# Resetear admin password
npm run strapi admin:reset-user-password --email=admin@example.com

# Generar nuevas API keys
npm run strapi generate:api

# Exportar/Importar data
npm run strapi export
npm run strapi import
```

---

💡 **Tip**: Para deployment, asegurar que todas las variables de entorno estén configuradas correctamente y usar PostgreSQL para base de datos en producción.

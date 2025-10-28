# ✅ Configuración Correcta en Coolify

## 🔴 CAMBIOS NECESARIOS:

### 1. Build Pack
**ACTUAL:** ❌ Nixpacks  
**CORRECTO:** ✅ **Dockerfile** (Custom)

### 2. Instalar/Build/Start Commands

Deberías configurar manualmente:

**Install Command:**
```bash
npm ci --production=false
```

**Build Command:**
```bash
npm run build
```

**Start Command:**
```bash
docker-entrypoint.sh npm run start
```

### 3. Base Directory
**ACTUAL:** `/` ✅ Correcto

### 4. Publish Directory
**ACTUAL:** `/` ✅ Correcto  

**(Para Strapi, no necesitas publish directory porque todo está compilado)**

## ⚠️ IMPORTANTE: Variables de Entorno

Necesitas agregar TODAS estas variables en Coolify:

```
HOST=0.0.0.0
PORT=1337
NODE_ENV=production
APP_KEYS=7b2c4e9f3a6d1e8c5b7a2f4d9e6c3a1b8f5e2d7c4a9b6f3e1d8c5b2a7f4e,9d3e6f2a5b8c1d4e7f2a5b8c3d6e9f4a1b7c4d1e8f3a6b9c2d5e8f1a4b7,4f1a6c9d2e5f8b3a1c7d4e9f2a6b5c8d3e7f1a4b9c2d6e5f8a3b1c4d7e,8e3f6a2b5c1d9e6f3a8c4b7d2e5f1a4b9c8d3e7f2a6b1c4d8e5f3a7b9
API_TOKEN_SALT=c9e4f2a7b3d1e8f5a2b6c9d0e3f6a1b4c7d2e5f8a3b6c1d4e7f2a5b8c3d6e9f4
ADMIN_JWT_SECRET=a7f3b9c2d8e1f6a4b5c7d9e2f3a6b8c1d4e7f0a3b6c9d2e5f8a1b4c7d0e3f6a9b2
TRANSFER_TOKEN_SALT=2b5f8c1d4e7a3b9f2c6d1e8f5a7b3c9d6e2f8a1b5c4d9e3f7a2b6c8d1e5f9
JWT_SECRET=3d7f4a8b2c6e9f1d5a8c3b7e2f6a9d4c1e8f3b6a2c9d5e8f1a4b7c3d6e9f2a5
ENCRYPTION_KEY=a7f3b9c2d8e1f6a4b5c7d9e2f3a6b8c1d4e7f0a3b6c9d2e5f8a1b4c7d0e3f6a9b2
DATABASE_CLIENT=sqlite
DATABASE_FILENAME=.tmp/data.db
PUBLIC_URL=https://admin.simplitrade.surcodes.com
STRAPI_ADMIN_BACKEND_URL=https://admin.simplitrade.surcodes.com
STRAPI_ADMIN_CLIENT_PREVIEW_SECRET=7c2f5b9e3a6d1c8f4b7a2e6d9c3f1a8b5c2e9d6f3a1b8c4e7d2a5f9b6c3e8
STRAPI_ADMIN_CLIENT_URL=https://admin.simplitrade.surcodes.com
STRAPI_BACKEND_URL=https://admin.simplitrade.surcodes.com
STRAPI_LOG_LEVEL=info
CI=false
```

## 📝 PASOS PARA CORREGIR:

### 1. Cambiar de Nixpacks a Dockerfile
En la sección "Build Pack", selecciona **"Dockerfile"** en lugar de "Nixpacks"

### 2. Llenar los comandos manualmente
No dejes que se detecten automáticamente:

- **Install Command:** `npm ci --production=false`
- **Build Command:** `npm run build`
- **Start Command:** `docker-entrypoint.sh npm run start`

### 3. Agregar Variables de Entorno
Ve a la pestaña "Environment Variables" y agrega todas las variables de arriba.

### 4. Guardar y Deploy
Click en "Save" y luego en "Deploy"

## ✅ CONFIGURACIÓN FINAL CORRECTA:

```
Name: Backend
Build Pack: Dockerfile ✅
Is it a static site? NO
Domains: https://admin.simplitrade.surcodes.com/
Direction: Both www & non-www ✅
Install Command: npm ci --production=false
Build Command: npm run build
Start Command: docker-entrypoint.sh npm run start
Base Directory: /
Publish Directory: / (o deja vacío)
Ports Exposes: 1337 ✅
```


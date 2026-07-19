# Weather App

Aplicación de ejemplo con backend Node/Express y frontend React/Vite.

## Estructura

- `backend/`: servidor Node.js que consume datos de Open-Meteo.
- `frontend/`: aplicación React con Vite que consulta al backend.

## Ciudades soportadas

- Madrid
- Londres
- París
- Ciudad de México
- Quito

## Requisitos

- Node.js 18+ instalado
- npm disponible en el sistema

## Instalación

1. Abrir terminal en `c:\DESARROLLO\LUIS\proyecto\backend`
2. Ejecutar:
   ```powershell
   npm install
   ```
3. Abrir otra terminal en `c:\DESARROLLO\LUIS\proyecto\frontend`
4. Ejecutar:
   ```powershell
   npm install
   ```

> Si `npm` no se reconoce, puede que Node.js no esté en el PATH. En Windows, asegúrate de que `C:\Program Files\nodejs` está en la variable de entorno `PATH`.

## Ejecución

### Backend

1. En la carpeta `backend`
2. Ejecutar:
   ```powershell
   npm start
   ```
3. El servidor se levantará en:
   - `http://localhost:4001`

### Frontend

1. En la carpeta `frontend`
2. Ejecutar:
   ```powershell
   npm run dev
   ```
3. El frontend se levantará en el puerto configurado (por defecto `4002`):
   - `http://localhost:4002/`

> Nota: para desarrollo local no es necesario build. Para producción o despliegue en Vercel, el frontend sí se compila con `npm run build`.

## Uso

1. Abre el navegador en `http://localhost:4002/`.
2. Selecciona una ciudad del menú.
3. Haz clic en `Consultar clima`.
4. Verás el clima actual y el pronóstico semanal.

## API del backend

- `GET /api/weather?city=<ciudad>`

Ciudades válidas: `madrid`, `london`, `paris`, `mexico`, `quito`.

Ejemplo:

```powershell
curl http://localhost:4001/api/weather?city=quito
```

## Notas

- El backend no usa base de datos.
- El backend obtiene datos de `https://api.open-meteo.com`.
- El frontend usa proxy para redirigir `/api` al backend.

## Despliegue en Vercel

Este proyecto incluye una configuración para desplegar en Vercel:

- `vercel.json`: define los builds y rutas.
- `api/weather.js`: función serverless que reemplaza el backend de Express en producción.

### Pasos para desplegar

1. Instala el CLI de Vercel si aún no lo tienes:
   ```powershell
   npm install -g vercel
   ```
2. Inicia sesión o crea cuenta:
   ```powershell
   vercel login
   ```
3. Desde la raíz del proyecto (`c:\DESARROLLO\LUIS\proyecto`), ejecuta:
   ```powershell
   vercel
   ```
4. Sigue los pasos del asistente y acepta la configuración predeterminada.

### Qué se publicará

- La app React se compilará desde `frontend/` y se servirá como contenido estático.
- La ruta del backend será `/api/weather` y funcionará con la función serverless en `api/weather.js`.

### Uso en Vercel

Después del despliegue, la aplicación estará disponible en la URL que te entregue Vercel. Solo abre la URL y usa el menú para seleccionar una ciudad.

### Despliegue desde la web de Vercel

Si prefieres usar la interfaz web de Vercel en lugar del CLI:

1. Conecta tu repositorio (GitHub, GitLab o Bitbucket) a Vercel.
2. Selecciona el proyecto y la rama que deseas desplegar.
3. Verifica que el archivo `vercel.json` está en la raíz del repositorio.
4. Asegúrate de que Vercel detecta el build desde `frontend/` y la función serverless en `api/weather.js`.
5. Haz clic en "Deploy".

Vercel construirá el frontend y expondrá la ruta del backend en `/api/weather`. Cuando el despliegue complete, usa la URL pública generada para abrir la app.

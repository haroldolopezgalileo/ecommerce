# Configuración de Vite React en GitHub Pages

Para subir el proyecto de Vite con React a GitHub Pages, sigue estos pasos:

**Paso 1: Configura tu proyecto de Vite para GitHub Pages**
Abre el archivo vite.config.js y agrega la propiedad base en la configuración de Vite. Esta propiedad debe ser el nombre de tu repositorio precedido por una barra (/nombre-del-repositorio/). Esto es necesario para que las rutas funcionen correctamente en GitHub Pages.

```javascript
// vite.config.js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/nombre-del-repositorio/' // Reemplaza con el nombre de tu repositorio
})
```

Guarda los cambios en vite.config.js.

**Paso 2: Instala el paquete gh-pages**
Este paquete te ayudará a realizar el deploy automáticamente a GitHub Pages.

```bash
npm install gh-pages --save-dev
```

**Paso 3: Configura los scripts en package.json**
En el archivo package.json, agrega dos scripts para generar el build y para hacer el deploy en GitHub Pages.

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
  },
}
```

Ejecuta el comando `npm run build` antes de deploy para asegurarse de que la versión más reciente de tu proyecto esté lista.

El script de deploy utiliza gh-pages para subir la carpeta dist generada por Vite al branch gh-pages de tu repositorio, pero esto debe ser ya una vez has subido tus cambios al repositorio, a inicio no debes ejecutarlo.

**Paso 4: Realiza el primer commit y sube el proyecto a GitHub**
Inicializa un repositorio de Git si aún no lo has hecho:

```bash
git init
git add .
git commit -m "Initial commit"
```

Agrega el repositorio de GitHub como remoto y sube el proyecto (asegúrate de reemplazar <username> y <nombre-del-repositorio> con tu usuario y el nombre de tu repositorio):

```bash
git remote add origin https://github.com/<username>/<nombre-del-repositorio>.git
git branch -M main
git push -u origin main
```

**Paso 5: Ejecuta el deploy a GitHub Pages**
Con el proyecto en GitHub y configurado, ejecuta el siguiente comando para hacer el deploy:

```bash
npm run deploy
```
Esto publicará tu proyecto en GitHub Pages en la rama gh-pages. GitHub creará automáticamente la página en la URL:

```php
https://<username>.github.io/<nombre-del-repositorio>/
```

**Paso 6: Habilita GitHub Pages en tu repositorio**
- Ve a tu repositorio en GitHub.
- Haz clic en Settings (Configuración).
- En el menú lateral, selecciona Pages.
- Asegúrate de que la fuente esté configurada en la rama gh-pages y en la carpeta root.
- Guarda los cambios.

**Paso 7: Verifica el deployment**
Después de unos minutos, tu proyecto debería estar disponible en la URL:

```php
https://<username>.github.io/<nombre-del-repositorio>/
```

¡Y listo! Tu proyecto de Vite con React debería estar funcionando en GitHub Pages.
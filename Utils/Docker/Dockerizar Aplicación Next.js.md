### Guía para Crear y Desplegar una Aplicación Node.js con Docker

Este tutorial te guiará a través de los pasos para crear un contenedor Docker utilizando una imagen oficial de Node.js como base y desplegar la aplicación en modo producción. Utilizaremos un `Dockerfile` para construir la imagen y un archivo `docker-compose.yml` para configurar y manejar el servicio.

#### 1. Crear el `Dockerfile`

El `Dockerfile` es esencial para definir cómo se construirá la imagen de Docker para tu aplicación. A continuación, te explico cada sección del archivo:

1. **Usa una imagen base oficial**  
   Se utiliza `node:18-alpine` como la base de la imagen. Esta es una versión ligera de Node.js optimizada para producción.
   ```dockerfile
   FROM node:18-alpine
   ```

2. **Establece el directorio de trabajo**  
   Dentro del contenedor, estableceremos el directorio de trabajo como `/app`.
   ```dockerfile
   WORKDIR /app
   ```

3. **Copia los archivos de dependencias**  
   Copiamos `package.json` y `package-lock.json` para que Docker instale solo las dependencias necesarias.
   ```dockerfile
   COPY package*.json ./
   ```

4. **Instala las dependencias**  
   Usamos `npm install` para instalar las dependencias especificadas en los archivos `package.json`.
   ```dockerfile
   RUN npm install
   ```

5. **Copia el resto del código**  
   Copiamos todos los archivos del proyecto al contenedor.
   ```dockerfile
   COPY . .
   ```

6. **Construye la aplicación**  
   Ejecuta el comando para construir la aplicación (si es necesario, por ejemplo, en aplicaciones con React).
   ```dockerfile
   RUN npm run build
   ```

7. **Expone el puerto de la aplicación**  
   Definimos el puerto en el que correrá la aplicación dentro del contenedor.
   ```dockerfile
   EXPOSE 3000
   ```

8. **Comando de inicio en modo producción**  
   Definimos el comando para iniciar la aplicación en modo producción.
   ```dockerfile
   CMD ["npm", "start"]
   ```

#### 2. Crear el `docker-compose.yml`

Este archivo simplifica la ejecución de la aplicación utilizando Docker Compose. Aquí se configura el servicio, se mapean puertos y se definen variables de entorno.

1. **Versión de Docker Compose**  
   Especificamos la versión del archivo de configuración.
   ```yaml
   version: '3.8'
   ```

2. **Definir el servicio de la aplicación**  
   Configuramos el servicio principal llamado `app`.
   ```yaml
   services:
     app:
       build: .
       ports:
         - '3000:3000'
   ```

3. **Configurar las variables de entorno**  
   Definimos `NODE_ENV` como `production` para que la aplicación corra en modo producción.
   ```yaml
       environment:
         - NODE_ENV=production
   ```

4. **Montar volúmenes**  
   Mapeamos el directorio actual al directorio de trabajo dentro del contenedor, permitiendo el desarrollo en tiempo real.
   ```yaml
       volumes:
         - .:/app
   ```

5. **Política de reinicio**  
   Configuramos el contenedor para que se reinicie automáticamente si falla o si el servidor se reinicia.
   ```yaml
       restart: always
   ```

#### 3. Código Final

A continuación, te dejo el código final para ambos archivos:

**`Dockerfile`**
```dockerfile
# Usa una imagen oficial de Node.js como base
FROM node:18-alpine

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia el package.json y package-lock.json para instalar dependencias
COPY package*.json ./

# Instala las dependencias
RUN npm install

# Copia el resto del código de la aplicación
COPY . .

# Construye la aplicación
RUN npm run build

# Exponer el puerto que utilizará la aplicación
EXPOSE 3000

# Comando para iniciar la aplicación en modo producción
CMD ["npm", "start"]
```

**`docker-compose.yml`**
```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - '3000:3000'
    environment:
      - NODE_ENV=production
    volumes:
      - .:/app
    restart: always
```

Con estos archivos, podrás construir y desplegar tu aplicación de Node.js en un contenedor Docker de manera eficiente.
#### 4. Contemplación Final
**Recuerda tener desactivado standalone en tu "next.config.js" 
```
// output: 'standalone',
```
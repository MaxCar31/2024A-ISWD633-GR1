# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name mi_nginx -v C:\Users\LabP3E004\Desktop\Practica\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de nginx, se verá el contenido de la carpeta html de tu máquina host.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor será reemplazado por el archivo index.html que se encuentra en la carpeta html del host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de nginx, verás el nuevo template HTML que has descargado y descomprimido en la carpeta html del host.

### Eliminar el contenedor
```
docker rm -f mi_nginx
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Al crear nuevamente el contenedor con el volumen de tipo host, el contenido del directorio html en el host se montará en /usr/share/nginx/html en el contenedor, por lo que el servidor nginx servirá el contenido actual de la carpeta html del host.

### ¿Qué hace el comando pwd?

El comando pwd muestra la ruta del directorio de trabajo actual en el sistema de archivos del host.

### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name mi_nginx --publish published=80,target=80 -v ${PWD}/html:/usr/share/nginx/html nginx:alpine

```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name mi_nginx --publish published=80,target=80 -v $(pwd -W)/html:/usr/share/nginx/html nginx:alpine

```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name mi_nginx --publish published=80,target=80 -v $(pwd)/html:/usr/share/nginx/html nginx:alpine
```


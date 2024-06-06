# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)
```
docker run -d --name mi_nginx --publish 8080:80 -v C:\Users\mateo\Documents\Practica3\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de nginx, verás el contenido del directorio C:\Users\mateo\Documents\Practica3\html servido por el servidor web nginx.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor original será reemplazado por el archivo index.html que se encuentra en C:\Users\mateo\Documents\Practica3\html. Si no hay un archivo index.html en el host, nginx mostrará un error 403 Forbidden o una página vacía. 
<img width="928" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/d2074d46-49aa-4388-a8fc-e3d9684bb994">


### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?

Al ingresar al servidor de nginx, se verá el contenido del nuevo template descargado de HTML5 UP servido por nginx.

<img width="922" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/5c16d1aa-0303-48f4-ba7c-4f4a2da5a762">


### Eliminar el contenedor

```
docker rm -f mi_nginx
```
<img width="330" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/5c9508b1-57f6-464c-8448-fa0cf6c2310c">

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Al crear nuevamente el contenedor con el mismo volumen de tipo host, nginx servirá el contenido de C:\Users\mateo\Documents\Practica3\html sin cambios, ya que los archivos en el host no se ven afectados por la eliminación del contenedor.

### ¿Qué hace el comando pwd?

El comando pwd imprime el directorio de trabajo actual. En el contexto de Docker, se usa para obtener la ruta absoluta del directorio actual para montar volúmenes correctamente.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```


# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](imagenes/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 

Una imagen es una plantilla de solo lectura que define el contenido del contenedor. Un contenedor, por otro lado, es una instancia en ejecución de una imagen. Mientras que las imágenes se utilizan para crear contenedores, los contenedores son los entornos ejecutables que se derivan de estas imágenes. En otras palabras, la imagen es el plano y el contenedor es el edificio construido a partir de ese plano.

![Imagen y contenedores](imagenes/imagenYcontenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**

```
docker pull hello-word
```


**¿Qué es nginx**

Nginx es un servidor web de alto rendimiento y proxy inverso utilizado para manejar múltiples protocolos de Internet, incluyendo HTTP, HTTPS, SMTP, POP3 e IMAP. Es conocido por su alta eficiencia y capacidad para gestionar grandes volúmenes de conexiones concurrentes, lo que lo hace ideal para aplicaciones web modernas, equilibrado de carga y proxy de correo.

Descargar la imagen  **nginx** en la versión **alpine**

```
docker pull nginx:alpine

```

### Listar imágenes

```
docker images
```

# COLOCAR UNA CAPTURA DE PANTALLA DEL RESULTADO 

**Identificadores**
En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 

```
docker inspect hello-world
```

**¿Con qué algoritmo se está generando el ID de la imagen**

El ID de la imagen Docker se genera utilizando el algoritmo de hash SHA-256. Este algoritmo toma el contenido de la imagen y genera un identificador único, garantizando que cualquier cambio en el contenido de la imagen producirá un ID diferente.

### Filtrar imágenes

```
docker images | grep <termino a buscar>
```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 

```
docker rmi hello-world
```


-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```


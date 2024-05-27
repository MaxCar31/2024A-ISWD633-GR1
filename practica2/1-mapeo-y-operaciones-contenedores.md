# Mapeo de Puertos 
### Usando una forma más semántica cuando se especifican puertos

```
docker run -d --name jenkins-server --publish published=8080,target=8080 --publish published=50000,target=50000 jenkins/jenkins:alpine3.18-jdk11

```
### Publicando todos los puertos
```
docker run -P -d --name jenkins-server jenkins/jenkins:alpine3.18-jdk11
```

-P: le indica a Docker que asigne automáticamente puertos aleatorios en tu host para todos los puertos expuestos por el contenedor.

**Recordar**
No puedes mapear puertos a un contenedor existente directamente después de su creación con Docker. El mapeo de puertos debe especificarse en el momento de crear y ejecutar el contenedor.

### Crear contenedor de Jenkins puertos contenedor: 8080 (interface web) y 50000 (comunicación entre nodos) imagen: jenkins/jenkins:alpine3.18-jdk11
# COMPLETAR
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/c195889f-0917-4890-92b6-809ef7dab79c)

# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:8080
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/b3501ba8-dfd2-46c0-b75d-26b98afbb96f)

### ¿Cómo obtener la contraseña solicitada?
Para obtener la contraseña solicitada es necesario ingresar al contenedor.

![Imagen](imagenes/jenkins.PNG)

# Operaciones con contenedores

### Ejecutar un comando en un contenedor de Docker en ejecución
```
docker exec jenkins-server ls -l
```


# COMPLETAR
### ¿Para qué se usa el comando ls?

El comando ls se utiliza en sistemas operativos Unix y similares (como Linux y macOS) para listar el contenido de un directorio. Al ejecutar ls, obtienes una lista de archivos y directorios dentro del directorio actual o especificado.

### ¿Para qué sirve el argumento -l junto al comando ls?

El argumento -l junto al comando ls proporciona una lista detallada del contenido del directorio. La salida en modo detallado incluye información adicional sobre cada archivo y directorio, como:

- Permisos: Indican quién puede leer, escribir o ejecutar el archivo.
- Número de enlaces: Muestra cuántos enlaces apuntan al archivo.
- Propietario: Indica el usuario propietario del archivo.
- Grupo: Indica el grupo al que pertenece el archivo.
- Tamaño: Muestra el tamaño del archivo en bytes.
- Fecha y hora: Indica la última fecha y hora en que el archivo fue modificado.
- Nombre: Muestra el nombre del archivo o directorio.

### Usar el contenedor de jenkins creado previamente y ejecutar el comando ls con el argumento -l
# COMPLETAR
# COLOCAR UNA CAPTURA DE PANTALLA
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/e9ae4ef9-8420-4e25-9a6e-6bace7155f70)

### Para ejecutar un shell interactivo en un contenedor de Docker especificado.
El comando **docker exec** te permite acceder a la sesión shell de un contenedor en ejecución, estarás dentro del contenedor y podrás ejecutar comandos como si estuvieras en una terminal normal. 
Para saber qué comando utilizar para abrir una terminal dentro de un contenedor, es útil conocer la imagen base del contenedor, ya que diferentes imágenes pueden usar diferentes shells o comandos para abrir una terminal. Puedes verificar la documentación de la imagen del contenedor en Docker Hub o en el repositorio de la imagen para obtener información específica sobre cómo abrir una terminal en esa imagen.
- Para imágenes basadas en Debian o Ubuntu, puedes probar con bash.
- Para imágenes basadas en Alpine Linux, puedes probar con sh.
![Imagen](imagenes/jenkins-i.PNG)
```
docker exec -i jenkins-server ls
```
-i: mantiene abierta la entrada estándar (stdin) del contenedor. Esto significa que puedes enviar datos al proceso que se está ejecutando en el contenedor a través de la terminal local. *Sin embargo, esto no asigna un terminal al contenedor, por lo que no podrás ver la salida del proceso de forma interactiva.*

### Ejecutar una de las siguientes instrucciones
```
docker exec -it jenkins-server /bin/bash 
```

**Considerar**
- /bin/bash: Al especificar la ruta completa del shell, Docker buscará el ejecutable /bin/bash en el sistema de archivos del contenedor y lo ejecutará. Esto es útil cuando quieres asegurarte de que se está utilizando un shell específico que está ubicado en una ubicación conocida en el sistema de archivos del contenedor. 
- bash: Al especificar solo el nombre del shell, Docker buscará el comando bash en las rutas del sistema (por lo general, en las rutas definidas en la variable de entorno PATH) del contenedor y lo ejecutará. Esto asume que bash está disponible en alguna de las rutas del sistema definidas en el contenedor.

Ejecutar
```
echo "Hola mundo"
```

Ejecutar
```
whoami
```
# COLOCAR UNA CAPTURA DE PANTALLA
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/14eec254-cdf5-4c75-b1ca-541b5ea47940)

**Si se visualiza el mensaje command not found, considerar**
El problema se debe a que no se ha asignado un terminal de salida al contenedor al ejecutar el comando. Cuando usas docker exec -i jenkins-server /bin/bash en Windows, el comando se ejecuta pero no hay un terminal asignado para mostrar la salida del comando ls.


### Para ejecutar un shell interactivo bidireccional en un contenedor de Docker especificado.
Ejecutar un shell interactivo bidireccional en un contenedor de Docker significa abrir una sesión de shell en el contenedor que permite la interacción bidireccional entre la terminal local y el contenedor. Es decir, puedes enviar comandos desde tu terminal local al contenedor y recibir la salida de esos comandos de vuelta en tu terminal local, al igual que si estuvieras trabajando directamente en la terminal del contenedor.

![Imagen](imagenes/jenkins-it.PNG)

```
docker exec -it jenkins-server /bin/sh
```

### Ahora puedes acceder al contenedor de jenkins y obtener la contraseña ubicada en /var/jenkins_home/secrets/initialAdminPassword

# COMPLETAR

### Colocar una captura de pantalla de la ventana que aparece después de colocar la contraseña.
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/2e96e8de-2231-45f0-b131-6422c19f45d4)
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/8a90ced0-76fa-4959-8fcd-7d17c23daeef)


**Para este punto no es necesario continuar con la instalación de Jenkins**


### Para ver los logs de un contenedor

```
docker logs -t -n 100 jenkins-server
```
-t: para incluir la fecha y la hora






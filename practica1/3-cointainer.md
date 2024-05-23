# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
# COMPLETAR

```
docker create --name srv-web nginx:alpine
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/c729c3d4-e33a-4e9b-8d27-e5b985af2524)


Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
# COMPLETAR
```
docker create hello-world
```

### Listar los contenedores ejecutándose o no

```
docker ps -a
```

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/4931c0fe-429e-4daf-98f2-1d8bb1723f3f)


### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```

Iniciar el contenedor srv-web 
# COMPLETAR
```
docker start srv-web
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/1759bc17-0830-4496-a17b-a42db77dd667)



### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/538409d2-9a35-49d5-92c5-5239a3207a51)


### Para detener un contenedor

```
docker stop <nombre contenedor>
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/86b9b333-8497-47aa-8d73-cb791bf4a32b)



### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```

![Ecosistema de Docker](imagenes/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR

```
docker run --name srv-web2 nginx:alpine
```

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/11081ea5-d2ac-4c53-aefe-da8599b33abf)


**¿Qué sucede luego de la ejecución del comando?**
# COMPLETAR  
Después de ejecutar el comando, Docker crea un nuevo contenedor a partir de la imagen especificada y lo inicia inmediatamente. Si no se especifica la opción -d (modo detach), el contenedor se ejecuta en primer plano, capturando la entrada estándar (stdin) del terminal. Esto significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

Cuando se ejecuta un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
# COMPLETAR

```
docker run -d --name srv-web3 nginx:alpine
```

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/37308cd3-7a5f-4ea6-a083-b237e29eb50b)


### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR
```
docker rm hello-world
```
Verificar que el contenedor que se eliminó
# COMPLETAR
```
docker ps -a | grep hello-world
```
### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR
```
docker rm -f srv-web3
```

Verificar que el contenedor que se eliminó
# COMPLETAR
```
docker ps -a | grep srv-web3
```
### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR
```
docker inspect srv-web
```

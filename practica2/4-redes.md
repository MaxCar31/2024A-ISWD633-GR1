# Redes
Las redes son un componente fundamental que permite la comunicación entre contenedores, así como la comunicación de los contenedores con el mundo exterior. 
![Imagen](imagenes/redes.PNG)
- Bridge: Esta es la red por defecto en Docker. Permite la comunicación entre contenedores en el mismo host. Cada contenedor conectado a la red bridge tiene una IP propia en la subred de la red bridge.
    -  Brige por default: Cuando se ejecuta un contenedor, Docker crea automáticamente una red de tipo bridge por default. Esta red se utiliza para permitir la comunicación entre contenedores en el mismo host. Cada contenedor conectado a esta red obtiene su propia dirección IP en la subred de la red bridge.
    - Bridge creada por nosotros: Un usuario también puede crear sus propias redes de tipo bridge en Docker. Esto puede ser útil para organizar y segmentar los contenedores de una aplicación de manera más controlada. Al crear una red bridge personalizada, se puede especificar un rango de direcciones IP y otras configuraciones de red específicas. Los contenedores conectados a esta red utilizarán las direcciones IP de la subred definida por el usuario.
- Host: Con esta red, los contenedores comparten la red del host en lugar de tener su propia interfaz de red. Esto puede mejorar el rendimiento de red, pero los contenedores pueden entrar en conflicto con los puertos del host si intentan utilizar los mismos puertos.
- None: Con esta red, se deshabilita la configuración de red. Los contenedores que usan esta red tienen su propia red de bucle invertido y no pueden comunicarse con otros contenedores a menos que se conecten explícitamente a una red.

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```

### Para saber a qué red está conectado un contenedor

```
docker inspect <nombre contenedor>
```
ó
```
docker network inspect <nombre red> 
```

### Vincular contenedor a una red
```
docker network connect <nombre red> <nombre contenedor>
```

### Para desvincular un contenedor de una red
```
docker network disconnect <nombre red> <nombre contenedor>
```

### Para listar las redes existentes
```
docker network ls
```

### Crear los contenedores y las redes que se presentan en el esquema. Usar para todos los contenedores la imagen de nginx:alpine

![Imagen](imagenes/esquema-ejercicio-redes.PNG)

### Paso 1: Crear las Redes
Primero, creare las dos redes net-curso1 y net-curso2 de tipo bridge como se muestra a continuación.

```
docker network create net-curso01 -d bridge
docker network create net-curso02 -d bridge 
```

<img width="851" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/73bc0bf0-de68-4d8e-b1da-9737ad710e48">


### Paso 2: Crear los contenedores y vincularlos a sus respectivas redes.

#### Con respecto al Contenedor 1 y 2 en net-curso01:

```
docker run -d --name contenedor1 --network net-curso01 nginx:alpine
docker run -d --name contenedor2 --network net-curso01 nginx:alpine
```
<img width="953" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/5b132ae8-baa1-49f2-a25d-ecc5c9622357">

#### Contenedor 3 en ambas redes net-curso01 y net-curso02

```
docker run -d --name contenedor3 --network net-curso01 nginx:alpine
docker network connect net-curso02 contenedor3
```
<img width="952" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/1372d0c9-54a1-4768-954b-c526bce38b0f">

<img width="882" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/c8f24190-e594-4a41-aac6-f2f799d59d9f">

#### Contenedor 4 en net-curso02:

```
docker run -d --name contenedor4 --network net-curso02 nginx:alpine
```
<img width="958" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/17d064a4-f77c-4e36-852f-0f885cf4107d">


### Verificar las Conexiones:

Se inspecciona las conexiones esten conectadas a las redes correctas mediante los siguiente comandos. 

```
docker inspect contenedor1
docker inspect contenedor2
docker inspect contenedor3
docker inspect contenedor4
```
Pero por facilidad se va a inspeccion por redes creadas. 
## Inspeccion por Redes 

```
docker network inspect net-curso01 
docker network inspect net-curso02
```

### Capturas de la estructura creada:

#### Enlistar las Redes creadas 

<img width="715" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/781521f8-9fc6-42cb-9248-0ab31dbe5206">


Notemos como en la net-curso01 Se encuentra el contenedor1, contenedor2 y contenedor 3.

<img width="542" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/9699196f-45ba-46e7-be10-57e18a2bbae9">

Notemos como en la net-curso02 Se enecuentra el contenedor3 y contedor4. 

<img width="597" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/4aa40436-f598-4521-ae83-0fdc37bb1662">


# Eliminar las redes creadas.

<img width="801" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/d86575fb-1e80-480b-bb21-f43010320c6c">


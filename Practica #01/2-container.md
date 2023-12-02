### Crear un contenedor
- `docker create --name <nombre-contenedor> <nombre-imagen>:<tag>` //Si no se le coloca el nombre al contenedor, se asiga uno al azar

- `docker create <nombre-imagen>:<tag>` //por ejemplo docker create nginx:alpine quiere decir que se crea un contenedor con un nombre al azar con la imagen nginx con la versión (tag) alpine

### Listar contenedores ejecutandose
- `docker ps` //lista los contenedores ejecutandose

### Listar contenedores ejecutandose o no 
- `docker ps -a` //lista todos los contenedores 

### Para iniciar un contenedor
- `docker start <nombre-contenedor>` //con run creamos, pero con start inicializamos

### Para detener un contenedor
- `docker stop <nombre-contenedor>`

### Para crear un contenedor y ejecutarlo inmediatamente
- `docker run --name <nombre-contenedor> <nombre-imagen>:<tag>` //Crea y ejecuta el contenedor (es importante recalcar que la ejecucion queda vinculado en el terminal (como una espcie de loop) y para salir debemos de poner ctrl + C )

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
- `docker run -d --name <nombre-contenedor> <nombre-imagen>:<tag>` 
  
El `-d` sirve para ejecutar el contenedor en segundo plano (detached mode), es decir para desvincular del terminal

### Para eliminar un contenedor
- `docker rm <nombre-contenedor>` //Se elimina si el contenedor NO se está ejecutando

### Para eliminar un contenedor si se está ejecutando

- `docker rm -f <nombre-contenedor>` //Se va a detener y se va a eliminar

### Para inspeccionar un contenedor
- `docker inspect <nombre-contenedor>` 

## Para crear un mapeo de puertos (puerto host y puerto contenedor)

- `docker run -d --name <nombre-contenedor> -p <puerto-host>:<puerto-contenedor> <nombre-imagen>:<tag>`

IMPORTANTE
**Puerto-host:** Este es el puerto en el cual tú deseas que el servicio del contenedor sea accesible desde fuera del contenedor. Puedes elegir cualquier puerto en el host que esté disponible y no esté siendo utilizado por otro servicio. Puedes utilizar el puerto 8080, 3000, o cualquier otro que prefieras.

**Puerto-contenedor**: Estos son los puertos que están expuestos por el contenedor y son definidos por la configuración del contenedor o la imagen. A menudo, en la documentación de la imagen o del servicio que estás utilizando, encontrarás información sobre qué puertos están expuestos por defecto en el contenedor. Debes usar estos puertos al mapearlos al puerto del host con el argumento `-p`.

`-p <puerto-host>:<puerto-contenedor>`: Mapea un puerto del host al puerto del contenedor. Esto permite que servicios dentro del contenedor sean accesibles desde fuera del contenedor a través del puerto especificado en el host.

***IMPORTANTE***: No duplicar el puerto host, ya que estamos vinculando ese puerto específico en el host al puerto específico en el contenedor. Si intentamos asignar el mismo puerto del host a otro contenedor sin algún mecanismo de distribución de tráfico (algún proxy), obtendrás un error porque el puerto ya está en uso.


### Para mapear mas de un puerto

- `docker run -d --name <nombre-contenedor> -p <puerto-host01>:<puerto-contenedor01> -p <puerto-host02>:<puerto-contenedor02> <nombre-imagen>:<tag>`

Ej: docker run -d --name prueba -p 80:80 -p 3000:80 jenkins:alpine
![Alt text](images/image.png)



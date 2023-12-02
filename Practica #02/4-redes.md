### Crear una red de tipo bridge

- `docker network create <nombre-red> -d bridge`
  
- Ej: `docker network create net-course01 -d bridge`


### Crear un contenedor vinculado a una red

- `docker run -d --name <nombreContenedor> --network <nombre Red> <Imagen>`
- Ej: `docker run -d --name nginx1 --network net-course01 nginx`

### Para saber a que red esta conectado un contenedor
- `docker inspect <nombre contenedor>`
- `docker network inspect <nombre red>`
  
- Ej: `docker network inspect net-course01`


### Vincular contenedor a una red

- `docker network connect <nombre red> <nombre servidor>`
- Ej: `docker network connect net-couse02 nginx3`


### Desvincular contenedor de una red

- `docker network disconnect <nombre red> <nombre servidor>`
- Ej: `docker network connect net-course02 nginx3`


### Para listar las redes existentes

- `docker network ls`

### Eliminar contenedores detenidos, redes no usadas, imagenes huerfanas

- `docker system prune`

### Eliminar contenedores detenidos, redes no usadas, imagenes sin vincular a ningun contenedor y caché

- `docker system prune -a`

El borrar la imagen no supone un problema ya que actua como un instalador (la imagen ya se instaló en el contenedor), entonces esto es como una manera de limpieza
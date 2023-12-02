### Listar imágenes

Recordar que `<tag>` es solo si queremos una versión en específico, no es obligatorio, si no se pone, la versión es la mas actual (latest)
- `docker images`

### Descargar imágenes

- `docker pull <nombre-imagen>` // se descarga la ultima versión
- `docker pull <nombre-imagen>:<tag>` //para descargar una versión en especifico

### Filtrar imágenes

- `docker images | grep <termino-buscar>` //Para buscar una imagen en especifico (recordar hacerlo en la terminal bash porque en el cmd de windows no funciona)
### Inspeccionar una imagen

- `docker inspect <nombre-imagen>` //Sirve para obtener información de la imagen (red etc)
- `docker inspect <nombre-imagen>:<tag>` 

### Para eliminar una imagen

- `docker rmi <nombre-imagen>:<tag>` //Consideración: si la imagen que queremos elimianar se esta ejecutando, necesariamente debemos de matar el proceso 
- `docker rmi -f <nombre-imagen>:<tag>` //Matamos el proceso y eliminamos la imagen docker rmi -f hello-world

### Tarea 3
Crear el contenedor rabbitmq con mapeo de 2 puertos host-contenedor 15672 y el 5672

 `docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management-alpine`

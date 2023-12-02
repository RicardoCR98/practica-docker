### Para mapera puertos mas rapido

- `docker run -d --name <contenedor> --publish published=valor,target=valor <imgen>:<tag>`

### Tarea N°4
1. crear un contenedor de jenkins puertos contenedor: 8080 (interface web), 50000 jenkins/jenkins:alpine3.18-jdk11

- `docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:alpine3.18-jdk11`

2. Crear contenedor de Redis puerto contenedor: 6379 redis:alpine

- `docker run -d –name redis -p 6379:6379 redis:alpine`



### Para mapera puertos mas rapido

- `docker run -d --name <contenedor> --publish published=valor,target=valor <imgen>:<tag>`

- Ej: `docker run -d --name jenkins --publish 8080:8080 --publish 50000:50000 jenkins/jenkins:alpine3.18-jdk11`

Recordar que --publish se puede abreviar con -p que es exactamente lo mismo
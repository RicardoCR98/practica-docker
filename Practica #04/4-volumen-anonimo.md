
# 4.  **Volumen Anónimo**


### a.  *Crear un volumen anónimo*

``` batch
docker run -d \--name server-nginx -v /usr/share/nginx/html --publish published=9800,target=80 nginx:alpine
```

### b. *Eliminar el contenedor y el volumen*
```batch
docker rm -fv server-nginx
```
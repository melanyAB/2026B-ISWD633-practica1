# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name svr1 -p 8080:80 -v C:\Users\P3E010-D\Documents\nginx\html:/usr/share/nginx/html nginx:alpine
```
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar a http://localhost:8080, el servidor nginx muestra el error 403 Forbidden, lo que significa que el servidor recibió la solicitud, pero no permite acceder al contenido solicitado.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor queda reemplazado visualmente por el contenido de la carpeta html de la computadora, la carpeta del host está vacía, no contiene un archivo index.html el nginx muestra el error 403 Forbidden.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor Nginx mediante el navegador, utilizando la dirección http://localhost:3000, se muestra la página web correspondiente a la plantilla descargada de HTML5 UP.

### Eliminar el contenedor
```
docker rm -f svr1
```

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Al crear nuevamente el contenedor Docker a página web de la plantilla vuelve a estar disponible en nginx.



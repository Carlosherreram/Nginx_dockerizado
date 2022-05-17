# Servidor web nginx en docker

## Carlos Herrera Martín

### En la siguiente práctica instalaremos una imágen de nginx en un contenedor docker que alojará un archivo html que podremos ver desde nuestro navegador.
### Desde una máquina ubuntu.


### Descarga de la imágen nginx

Para instalar nginx deberemos de ejecutar desde la terminal de nuestra máquina el siguiente comando : ``docker run --rm -d -p 8080:80 --name web nginx``.


# Servidor web nginx en docker

## Carlos Herrera Martín

### En la siguiente práctica instalaremos una imágen de nginx en un contenedor docker que alojará un archivo html que podremos ver desde nuestro navegador.
### Desde una máquina ubuntu.




Para instalar nginx deberemos de ejecutar desde la terminal de nuestra máquina el siguiente comando :

``docker run --rm -d -p 8080:80 --name web nginx``.


![Screenshot_20220517_175631](https://user-images.githubusercontent.com/91744455/168873261-934e59e7-cbfe-46bb-8d60-03909abbbbeb.png)


Si ahora accedemos a nuestro navegador y visitamos : localhost:8080  nos aparecerá la siguiente página que nos servirá para confirmar que la instalación ha sido exitosa.

![Screenshot_20220517_175728](https://user-images.githubusercontent.com/91744455/168873632-72c6c8c6-733d-46f0-b212-f68268f8a991.png)

A continuación debemos liberararemos el contenedor llamado web con el siguiente comando:

``docker stop web``

A continuación desde Documentos crearemos una carpeta llamada nginx y en su interior otra llamada site-content, dentro de site-content crearemos un archivo html con este contenido :
![Screenshot_20220517_180600](https://user-images.githubusercontent.com/91744455/168874043-0d46effa-0d23-434d-9a94-6a4e5204eead.png)


y ejecutamos: 

``docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx``


![Screenshot_20220517_180654](https://user-images.githubusercontent.com/91744455/168874256-fd4b64da-74b4-4f3f-87d8-1487f31e0fea.png)


A continuación crearemos una imágen personalizada, para ello crearemos un Dockerfile en la carpeta nginx que contendrá los siguientes comandos:

``FROM nginx:latest
COPY ./site-content/index.html /usr/share/nginx/html/index.html``


Lo siguiente que debemos hacer es ejecutar el comando:

``docker build -t webserver .``

y asi construiremos nuestra imágen.

Lo último que faltaría hacer sería alojar nuestra imágen en el contenedor llamado web usando este comando:

``docker run --rm -d -p 8080:80 --name web webserver``
![Screenshot_20220517_191158](https://user-images.githubusercontent.com/91744455/168875004-a1661b9c-54eb-4c31-be64-a0d1ead73aa8.png)


y desde nuestro navegador comprobar que todo ha funcionado correctamente.
![Screenshot_20220517_191233](https://user-images.githubusercontent.com/91744455/168875025-fb0a0fad-04ea-4035-84eb-fcd893fbc17d.png)



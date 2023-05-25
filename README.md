# AWSbeanstalkPHPdocker
AWS Lab 12 Using Beanstalk and CloudFormation

1 - Nos aseguramos de tener funcionando lo explicado en el video "Listas Python Microservicios" https://www.youtube.com/watch?v=-kbp4tQVY0s con el github "https://github.com/cesarbobadilla/TiemposListas" o "https://github.com/cesarbobadilla/TiemposListasEnlazadas", si lo tenemos funcionando en https://labs.play-with-docker.com/ deberíamos tener un dominio de salida en el puerto 5000 con flask parecido a "http://ip172-18-0-26-chn8gig9ec4g00fdlo7g-5000.direct.labs.play-with-docker.com/", recordemos que podemos probar que funcione bien agregandio /api/# por ejemplo, suponiendo que el anterior sea el dominio "http://ip172-18-0-26-chn8gig9ec4g00fdlo7g-5000.direct.labs.play-with-docker.com/api/7" por ejemplo.

2 - En otra instancia de play-with-docker, máquina local o ambiente de desarrollo, generamos con el archivo de index.php donde reemplazamos el dominio explicado en el punto 1, adicional a eso creamos el archivo Dockerfile que esta en los archivos de este repositorio y ahí se detalla que será expuesto en el puerto 3000, con eso a mano procedemos a crear el contenedor de Docker, en el video generamos el contenedor con nombre demophp, entonces usamos el comando:

docker build -t demophp .

3 - Lo siguiente es registrarse en consola con 

docker login

4 - Nos registramos con las credenciales de nuestra cuenta de docker hub, https://hub.docker.com/ , ingresamos nuestro usuario luego contraseña, lo siguiente es prepararlo para subirlo a docker hub, y finalmente subirlo a docker hub, eso lo hacemos con:

docker tag demophp cesarbm/demophp:v1
docker push cesarbm/demophp:v1

5 - Podemos validar que subio correctamente el archivo en nuestra cuenta de docker hub

6 - Lo siguiente es ir a Beanstalk en plataforma elegimos Docker y en la opción de "Código de aplicación", por defecto se encuentra marcada una aplicación por defecto, entonces marcamos "Cargar el código" y modificamos el archivo  adjunto en este repositorio "Dockerrun.aws.json", especificamente la línea:
"Name": "cesarbm/demophp:v1" 
Reemplazando por el nombre de su cuenta en docker hub así como el nombre que se puso anteriormente, especificamente en docker tag.

7 - Con el archivo modificado procedemos a subirlo en la opción "Cargar el código", "Cargar Aplicación" y "Elegir archivo", le ponemos un valor a "Etiqueta de versión" y lo siguiente es seguir los pasos que nos da el laboratorio 12 "AWS Lab 12 Using Beanstalk and CloudFormation"



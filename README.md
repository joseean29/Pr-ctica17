# Pr-ctica17
1 Práctica 17: Balanceo de carga con HAProxy

En esta práctica vamos a modificar los archivos docker-compose.yml que hemos creado en las prácticas 15 y 16, y vamos a incluir un nuevo contenedor Docker con HAProxy para balancear la carga de los contenedores que ejecutan la aplicación web.

Posteriormente deberá realizar la implantación de ambos sitios web en Amazon Web Services (AWS) haciendo uso de contenedores Docker y de la herramienta Docker Compose.
Abrir los puetos

    80
    8080
    1936
    3306 

Añadimos a nustro docker-compose (#documentamos los puestos en apache):

    A continuación se muestra un fragmento de un archivo docker-compose.yml que incluye un servicio de balanceo de carga con HAProxy que nos puede servir de ejemplo: 

<1> Utilizaremos la imagen dockercloud/haproxy que está disponible en Docker Hub.

<2> El puerto 80 será el puerto del servicio que queremos balancear.

<3> El puerto 1936 nos permite acceder a una página web con información estadística del balanceador.

<4> Creamos un enlace con el servicio que queremos balancear. Los enlaces permiten que los contenedores se descubran entre sí y transfieran de manera segura información sobre un contenedor a otro contenedor.

<5> Es necesario montar el socket UNIX del Docker daemon (/var/run/docker.sock) para que el contenedor lb pueda comunicarse con el Docker daemon y obtener información del resto de contenedores.
Cómo escalar los servicios definidos en un archivo docker-compose.yml

Cuando ejecutamos docker-compose tenemos la posibilidad de indicar el número de instancias que queremos tener de cada uno de los servicios que vamos a crear.

El comando sería el siguiente:

docker-compose up --scale SERVICE=NUM

Donde:

    SERVICE es el nombre del servicio que queremos escalar
    NUM es el número de instancias que queremos tener de ese servicio.

Ejemplo:

En el siguiente ejemplo estaríamos iniciando todos los servicios que están definidos en el archivo docker-compose.yml y para el servicio de wordpress estaríamos creando 4 instancias.

docker-compose up --scale wordpress=4

    En el siguiente ejemplo estaríamos iniciando todos los servicios que están definidos en el archivo docker-compose.yml y para el servicio de apache estaríamos creando 4 instancias. docker-compose up --sacale apache=4 

Si inciamos nuesto navegador con nustra ip aparcera nustra pila lamp


Sinciamos nuesto navegador con nustra ip con :1936

usuario:stats contraseña:stats imagen

    Tendremos toda la informacion general 

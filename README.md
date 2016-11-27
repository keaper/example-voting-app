La votación definitiva
=========

Primeros pasos
---------------



Levantar el compose

    $ docker-compose up

La aplicación funcionará en [http://localhost:5000](http://localhost:5000), y los resultados se verán en [http://localhost:5001](http://localhost:5001).

Arquitectura
-----

![Architecture diagram](architecture.png)

* Aplicación en Python para elegir entre las dos opciones (frontend) 
* Una BBDD en memoria REDIS que recolecta las votaciones 
* Un worker desarrollado en .NET que pasa los votos en memoria a BBDD
* Una BBDD Postgres que guarda sus datos en un volumen de Docker en disco
* La aplicación desarrollada en Node.js para mostrar los votos en tiempo real




¿Cómo hacer la demo?

Mostrar DockerHub
Mostrar GitHub, hablar del concepto de branch y de fork

Montar la UI- > docker run -d -p 9000:9000 --privileged -v /var/run/docker.sock:/var/run/docker.sock uifd/ui-for-docker

Docker ps
Docker images

http://40.69.46.74:9000/ DockerUI

Entrar en mi GitHub

git clone https://github.com/keaper/votacion.git

Entrar con nano en compose y explicarles lo que hace
docker-compose up -d
Poner en segundo plano -d

http://40.69.46.74:5000/ votacion
http://40.69.46.74:5001/ resultados

http://bit.ly/lapreguntadefinitiva


Ver que hay que modificar el style
result/views/stylesheets/style.css - > #choice width:450px; -> 500px
Compilar de nuevo la imagen -> "docker build --no-cache -t keaper/votingapp_result-app ."
Poner el nombre de la versión -> docker tag 0e5574283393 keaper/votingapp_result-app:3.0
Docker push keaper/votingapp_result-app




docker-compose down
borrar todos los contenedores -> docker rm $(docker ps -a -q)
Parar todos los contenedores -> docker stop $(docker ps -a -q)
Borrar todas las imágenes ->docker rmi $(docker images -a -q)
Forzar borrado de imágenes "docker rmi -f”

docker build --no-cache -t keaper/votingapp_voting-app .
docker build --no-cache -t keaper/votingapp_worker .

la votación definitiva
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


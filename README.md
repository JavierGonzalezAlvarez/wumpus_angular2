# Wumpus

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 9.0.6.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

# Juego del wumpus
Version Front en Angular - existe una version creada en python en este mismo repositorio
Autor: Javier González
IDE: VSC
Entorno: ubuntu 20.04
Fecha: 12/12/2020
version: 1.0

# instalar angular
$ npm angular -g @angular/cli

#  crear proyecto
$ ng new wumpus --skipTests=true
-routing: y
-style: scss

# pasos
1. barra navegador, body y footer => OK
2. pintar grilla => OK
3. crear movimientos dentro de la grilla del cazador => OK
4. posiciones de los actores al inicio de partida => OK
5. posición del cazador respecto al resto de actores => OK
6. mensajes personalizados => PENDIENTE
7. contador de flechas y lanzar flechas => PENDIENTE

#  crear componentes header, body y footer
cd src/app
$ ng g component components/header
$ ng g component components/body
$ ng g component components/footer

# crear carpeta icons
wumpus/src/assets/icons

# crear carpeta img
incorporar imagen de wumpus sacada de google
wumpus/src/assets/img

# cambiar favicon
angular.json
index.html

# crear componente help
$ ng g component components/help

# instalar material design
ng add @angular/material
-indigo/pink
-y
-y

index.html, añadir:
 <link href=”https://fonts.googleapis.com/icon?family=Material+Icons” rel=”stylesheet”>  

app.module.ts, añadir:
import {MatIconModule} from '@angular/material/icon';
MatIconModule,

listado:
https://www.softaox.info/1000-angular-material-icons-list-mat-icon/

# crear directorio clases
app/clases

# crear servicio nav (barra navegador menu)
crear carpeta servicios - comunicación entre componentes
src/app/services

$ src/app/services/ng generate service nav
$ src/app/services/ng generate service mensajes


## dockerizacion - crear network
-------------------------------------
crear network:
$ docker network create angular-nginx-networks

comandos:
$ docker-compose up --build -d 
$ docker-compose start
$ docker-compose stop
$ docker-compose down

crear imagen desde docker (no docker-compose)
------------------------------------------------
$ docker build -t angular_wumpus .

listar imagenes
----------------
$ docker images

## entrar en el contenedor
----------------------------
docker container ls
docker exec -i -t container_id /bin/bash

docker exec -i -t 5b04716490e8 /bin/bash
dentro del contenedor=> ng serve

## Desde el navegador, una vez arrancado docker: docker-compose start
----------------------------------------------------------------------
http://localhost:3200/

en caso de que el puerto 4200 este en uso:
----------------------------------------------
matar el proceso anterior o cambiar el puerto por defecto o cambiar de puerto en docker o en comando:
$ ng serve --port 4201

## eliminar todas con contenedores
--------------------------------
docker rm $(docker ps -a -q) -f

## eliminar todas las imagenes
-----------------------------
docker rmi $(docker images -q) 

## despliegue
----------------
$ ng build --prod

## IP del juego en instancia de aws- ec2
--------------------------------------------
http://18.219.17.118/

## otra opcion: instalar pm2 para ejecutar npm start directamente
------------------------------------------------------------------
$ sudo apt install npm
$ sudo npm install pm2 -g
$ sudo pm2 start npm -- start


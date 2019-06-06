# Mi camara

Un proyecto simple para mostrar el alcance de herramientas open source del mundo de raspberry y pytyhon.


## Pasos

La herramienta que mas me gusta por su versatilidad para el manejo de la camara de las raspberry es **mjpg-streamer**

https://github.com/jacksonliam/mjpg-streamer

Para instalarla sigamos los siguientes pasos.

    $sudo apt-get update
    $sudo apt-get upgrade -y
    $sudo apt-get install build-essential libjpeg8-dev imagemagick libv4l-dev cmake -y
    $make
    $sudo make install

y para correr un web server que contenga el streaming de video

    $/usr/local/bin/mjpg_streamer -i "input_uvc.so -r 1280x720 -d /dev/video0 -f 30 -q 80" -o "output_http.so -p 8080 -w /usr/local/share/mjpg-streamer/www"

esto nos permite tener una imagen en http://ipDeMiRaspberry:8081/?action=stream

Adicionalmente en la demo que construi para la charla, arme un archivo bash para manejarlo como un servicio

    $./mjpeg-streamer.sh start


### Jupyter notebook

Para constuir el server que va a exponer el kernel de python para que podamos ejecutarlo remotamente use Jupyter (https://jupyter-notebook.readthedocs.io/en/stable/)

Me gusta use **pyenv** para tener ordenadas mis versiones de Python (le dejo **Ariel Ramos** el honor de armarles una charla al respecto) y **virtualenv** para ordenar todas esas librerias adicionales que uso.

Mi server lo arranco con

    $jupyter notebook
    
y lo accedo desde cualquier navegador de una maquina con acceso a la misma red que las raspberry

http://ipDeMiRaspberry:8888/tree?


### GpioZero

Esta libreria viene con la distro oficial de raspbian, pero se puede instalar con

    $sudo apt-get install python-gpiozero

o con **pip** en el propio ambiente de **virtualenv** si quieren mantener el orden.
Pero lo mas importante es que si quieren usan PWM por hardware van a tener que instalar si o si RPi.GPIO para que funcione como backend de gpiozero.


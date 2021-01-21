# RASAChatbotXP
Prueba de chatbot con metodología XP

## Guias de instalación

Dependiendo el sistema operativo, algunos pasos en la configuración de Python pueden ser distintos por lo que se recomienda en casos de algun problema,
revisar los videos tutoriales sobre la instalación de RASA en dicho SO. (https://www.youtube.com/watch?v=4ewIABo0OkU&list=PL75e0qA87dlEWUA5ToqLLR026wIkk2evk)

## Configuracion del 'enviroment'

Se recomienda crear un 'environment' especifico para el proyecto, por lo que crearemos una carpeta nueva, dentro de la consola iremos a su ubicacion e insertaremos el 'environment'.

### sudo apt install python3-NombreEnvironment           (Ubuntu)
### conda create --name NombreEnvironment python==3.7.6  (Windows 10 - Anaconda)

Posteriormente lo activaremos en Ubuntu con

### source ./NombreEnvironment/bin/activate 

En anaconda se puede iniciar directamente desde la interfaz de Anaconda Navigator.

## Instalar RASA y archivos adicionales (Ubuntu)

En Ubuntu necesitaremos colocar las siguientes lineas en la consola para instalar todo lo necesario para nuestro chatbot.

### pip install -U pip
### pip install rasa
### pip install spacy
### python -m spacy download es_core_news_md

## Instalar RASA y archivos adicionales (Windows 10 - Anaconda)

En anaconda necesitaremos colocar las siguientes lineas en la consola para instalar todo lo necesario para nuestro chatbot.

### conda install ujson
### conda install tensorflow
### pip install rasa
### pip install spacy
### python -m spacy download es_core_news_md

## Iniciar un proyecto con RASA

Para que se creen los archivos basicos del proyecto necesitaremos escribir en la consola

### rasa init

esto iniciara el proceso y debemos indicarle en que carpeta serán creados, si se deja vacío, se instalará en la ruta donde se encuentre actualmente la consola.
Una vez creados, estos se pueden sobreescribir con los archivos en la rama 'master'.

## Comandos importantes de rasa

### rasa train      (para entrenar al bot, debe usarse siempre luego de hacer un cambio en los archivos del chatbot)
### rasa shell      (para probar una conversacion por consola)
### rasa shell nlu  (para comprobar los grados de certeza en las intenciones de una frase que escriba el usuario)

## Comandos para establecer un servidor local

Se recomienda utilizar dos consolas, cada una para mantener activos los servicios de cada comando.

### rasa run -m models --enable-api --cors "*" --debug  
### rasa run actions

En el caso de querer usar WebSocket para incluirlo dentro de una pagina web, se recomienda agregar el script de BotFront (https://github.com/botfront/rasa-webchat) 
al HTML de dicha pagina, inicializar la herramienta de 'ngrok' y colocarle el comando

### ngrok http 5005

de esta manera se iniciara un canal utilizando ngrok, que proveera igualmente un IP, que sera la utilizada dentro del script para contactar con el chatbot.

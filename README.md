# AlarmaCiudadana

Sistema de alerta ciudadana.
Bocinas instaladas alrededor de la comunidad que la comunidad podrá hacer sonar cuando haya un incidente: robo o secuestro.

El sistema está compuesto por:
* un teléfono celular con interfaz serie (comandos AT) para recibir mensajes de texto
* un sistema arduino-compatible que reciba el mensaje del celular, y reaccione a él
* bocinas instaladas alrededor de la comunidad que sonarán cuando la comunidad envíe un mensaje al teléfono
* un mecanismo de comunicación entre las bocinas para notificarse de que tienen que sonar
* un sistema de energía solar para mantener el sistema independiente de la red de energía
* aplicación de pánico android que enviará mensajes predefinidos para hablar notificar de las alarmas.

# Comportamiento del sistema

* ante un robo o secuestro, un vecino activa su aplicación de pánico
* la aplicación envía un mensaje SMS a un número predefinido, asociado al teléfono celular con interfaz serie
* el teléfono celular con interfaz serie recibe el mensaje
* el sistema arduino compatible verifica periódicamente el celular ante mensajes nuevos, y lee el mensaje
* en base al contenido del mensaje, y al origen del mensaje, identifica ubicación y tipo de incidencia
* el sistema arduino compatible envía un mensaje a través del mecanismo de comunicación (idealmente LORA, pero puede ser wifi) a las bocinas correspondientes para que suenen
* el sistema arduino de las bocinas verifican periódicamente el mecanismo de comunicación a la espera de un mensaje del sistema conectado al teléfono celular con interfaz serie
* al recibir un mensaje, las bocinas correspondientes emiten un sonido a través de sus bocinas para alertar sobre el evento sucedido

#Comportamientos adicionales

* monitorear las baterias
* alerta de prueba (con sonido de prueba personalizado)
* monitoreo del crédito disponible del teléfono y el tiempo que le queda de vigencia
* sensor de movimiento anti-vandalismo

# Documentación

* comunicación arduino-celular:
  * https://www.circuitsathome.com/mcu/programming/interfacing-arduino-to-a-cellular-phone/comment-page-2/
  * http://old.pinouts.ru/CellularPhones-A-N/nokia_dku-5_cable_pinout.shtml
  * https://electronics.stackexchange.com/questions/65934/receiving-sms-using-gsm-and-controlling-led-using-arduino
* Alternativa: arduino gsm module: https://www.arduino.cc/en/Guide/ArduinoGSMShield
  * arduino esp8266 gsm module connection: https://stackoverflow.com/questions/41872756/interface-nodemcu-esp8266-with-gsm-module 
* comunicación arduino-bocinas: https://github.com/sudomesh/disaster-radio
* hacer sonar bocinas (solo arduino esp8266): https://github.com/earlephilhower/ESP8266Audio
* un ejemplo de una bocina y sus consumos: http://www.superinventos.com/s111203.htm . 350mA al sonar.

# Materiales para el prototipo

* parlante con amplificador y bateria: https://articulo.mercadolibre.com.mx/MLM-569071421-bocina-mini-recargable-reproductor-mp3-micro-sd-ks-139-_JM (o incluso uno que tengamos)
* panel solar: https://articulo.mercadolibre.com.mx/MLM-646825659-panel-solar-de-6-v-10-w-17-a-portatil-usb-cargador-celular-_JM
* protoboard: https://articulo.mercadolibre.com.mx/MLM-550353382-protoboard-fuente-5v-cables-dupont-65-piezas-_JM
* regulador a usb: https://articulo.mercadolibre.com.mx/MLM-590860576-powerbank-1500mha-bateria-universal-economica-colores-mc13-_JM
* esp8266: https://articulo.mercadolibre.com.mx/MLM-557096991-tarjeta-nodemcu-wifi-esp8266-version-3-arduino-ide-lua-_JM
* lora chip: https://articulo.mercadolibre.com.mx/MLM-638644102-lora-rfm95-915-mhz-transceptor-inalambrico-antena-base-_JM
* A6 GSM/GPRS o SIM900 module
  * https://articulo.mercadolibre.com.mx/MLM-637770258-iot-a6-gsm-a6-gprs-no-sim800-sim800l-_JM
  * https://articulo.mercadolibre.com.mx/MLM-641676707-modulo-gsm-gprs-sim900-shield-4g-adaptadores-sim-arduino-_JM

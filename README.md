# ArduinoOTA
Minimal OTA updater

Copier credentials.h.template en credentials.h.
Modifier dans credentials.h WIFI_SSID et WIFI_PASS => Gaffe, si on se plante, après c'est mort.
Build.
Noter l'adresse mac du sonoff à updater.
Utiliser ota_updater.py de homie (la bonne version!) pour upload le firmware.bin dans le sonoff.
Le sonoff redémarre.
Check l'ip DHCP que le sonoff a récupéré (en fonction de l'adresse mac).
Dans le platformio.ini du nouveau firmware Homie, ajouter :
upload_protocol = espota
upload_port = {IP DU SONOFF}

A METTRE A JOUR / A TESTER : UPLOAD DU SPIFFS *AVANT* LE FIRMWARE
Récupérer la config JSON (ou l'adapter, ou repartir d'un truc connu.., ou encore ne rien mettre pour passer en mode config).
La mettre dans le data/homie du projet.
Mettre aussi le uibundle.
Upload SPIFFS avec espota en utilisant le bon board_build.ldscript (eagle.flash.1m128.ld ou eagle.flash.1m64.ld ??)

Bien faire gaffe que le board_build.ldscript quand on fait firmware.bin est identique à quand on fait le SPIFFS.
Faire un build/upload comme dhab : ça va utiliser le protocole espota.
Le sonoff redémarre. Attendre :)
Normalement il reviens avec son nouveau firmware sans avoir perdu la config.
(Normalement)
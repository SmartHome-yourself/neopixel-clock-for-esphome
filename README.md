# esphome-neopixel-uhr
Neopixel RGB-LED Uhr mit LED-Matrix-Display


## Funktionen
Die Uhr gleicht die Uhrzeit mit dem Home Assistant Server ab und hält die Uhrzeit über eine RTC.  
Die LED-Matrix zeigt das aktuelle Datum an.  
Über einen Serviceaufruf der durch das einbinden der Uhr in Home Assistant zur Verfügung gestellt wird können Statusmeldungen auf der LED-Matrix ausgegeben werden. Die Texte werden, sobald sie zu lang für das Display sind, automatisch als durchlaufender Text angezeigt. 


Um einen Text von Home Assistant aus auf der Uhr auszugeben, sähe ein Serviceaufruf wie folgt aus:
```
service: esphome.neopixel_uhr_write_text
data:
  text: info text
```


## Projekt Code
Im ESPHome Projekt müssen nur die Substitutions angegeben und das Package geladen werden.

```
substitutions:
  # devicename should be the same like your yaml-filename
  devicename: shys-neopixel-uhr
  upper_devicename: "Neopixel Uhr"

  wifi_ssid: !secret wifi_ssid
  wifi_password: !secret wifi_password
  
  # get your new encryption key under: https://esphome.io/components/api.html
  api_encryption_key: "+xGZsEOk6f+w1+8/m2cQBVRBZXBTBwh85Ivxl+ODUco="
  
  # change yout ota password
  ota_password: "09ddd653496c905385d373fa18b6c5a2"
  
# load clock project
packages:
  neopixel_uhr_package: github://SmartHome-yourself/esphome-neopixel-uhr/neopixel-uhr.yaml@main
```

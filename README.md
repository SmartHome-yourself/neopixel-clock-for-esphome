# esphome-neopixel-uhr
Neopixel RGB-LED Uhr mit LED-Matrix-Display



## Funktionen
Die Uhr gleicht die Uhrzeit mit dem Home Assistant Server ab und hält die Uhrzeit über eine RTC.  
Die LED-Matrix zeigt das aktuelle Datum an.  
Über einen Serviceaufruf der durch das einbinden der Uhr in Home Assistant zur Verfügung gestellt wird können Statusmeldungen auf der LED-Matrix ausgegeben werden. Die Texte werden, sobald sie zu lang für das Display sind, automatisch als durchlaufender Text angezeigt. 



## Projekt Code
Im ESPHome Projekt müssen nur die Substitutions angegeben und das Package geladen werden.

```
substitutions:
  # Der devicename muss dem Dateinamen der YAML-Datei entsprechen
  devicename: shys-neopixel-uhr
  
  # Der friendly_name ist der Anzeige-Name und frei wählbar
  friendly_name: "Neopixel Uhr"

  # WLAN Zugangsdaten
  wifi_ssid: !secret wifi_ssid
  wifi_password: !secret wifi_password

  # Verfügbare Animationen:
  # - Uhr1
  # - Uhr2
  uhr_animation: "Uhr2"
  
  # Minimale Helligkeit der LEDs
  minimum_brightness: "30"
  
# Neopixel-Uhr als Package laden
packages:
  neopixel_uhr_package: github://SmartHome-yourself/esphome-neopixel-uhr/neopixel-uhr.yaml@main
```

Wer jetzt noch seine eigenen Sicherheitsschlüssel für die API-Verschlüsselung und/oder OTA verwenden möchte kann diese wie gewohnt einfach angeben und somit den Standard überschreiben:
```
# Generiere einen eigenen encryption key unter: https://esphome.io/components/api.html
api:
  encryption:
    key: "+xGZsEOk6f+w1+8/m2cQBVRBZXBTBwh85Ivxl+ODUco="

ota:
  password: "HierDeinOTA-PW"
```

## Service
Um einen Text von Home Assistant aus auf der Uhr auszugeben, sieht ein Serviceaufruf wie folgt aus:
```
service: esphome.neopixel_uhr_write_text
data:
  text: info text
```
_Dabei entspricht im Service-Namen das "neopixel_uhr" dem Geräte-Namen welcher unter **upper_devicename** in den Subscriptions angegeben wurde._
  
  


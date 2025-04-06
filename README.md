# LED Controller: Schaltplatine für WLED

## Disclaimer

Using this software and hardware is the users responsibility as it is not bug free.
Therefore contributors of this repo are not reliable for anything
including but not limited to spontaneous combustion of the entire led strip, the house and the inevitable heat death of the universe.

Also see: [LICENSE](./LICENSE)

## Features

- 3 PWM Ausgänge zum Steuern von 12 V RGB Kanälen
- Steuerung durch WIFI (einwahl in WLAN möglich oder Erstellen eines eigenen Accesspoints)
- 6 weitere GPIO Pins, z.B. für weitere Buttons,…
- RX/TX Verbindungen (Flashen des ESP32)

## Zusätzliche Features

- 8 PWM Ausgänge als Datenleitungen für individuell addressierbare LEDs
  - Signal auf 5 V
  - Mögliche LED - Strips (nicht vollständig)
    - WS2812
    - WS2805

## Pins

| ESP Pin Name | Board Output | Usage |
| ---------------:| ---------------:| ---------------:|
| TXD0 | J  7 | GPIO1, U0TXD, CLK_OUT3, EMAC_RXD2 |
| RXD0 | J  8 | GPIO3, U0RXD, CLK_OUT2 |
| IO 18 | LED-Out | MOSFET Transisotr 12 V |
| IO 19 | LED-Out | MOSFET Transisotr 12 V |
| IO 21 | LED-Out | MOSFET Transisotr 12 V |
| IO  2 | J  5 | MOSFET Transistor  5 V |
| IO 15 | J 11 | MOSFET Transistor  5 V |
| IO 13 | J 12 | MOSFET Transistor  5 V |
| IO 12 | J 13 | MOSFET Transistor  5 V |
| IO 14 | J 14 | MOSFET Transistor  5 V |
| IO 27 | J 15 | MOSFET Transistor  5 V |
| IO 26 | J 16 | MOSFET Transistor  5 V |
| IO 25 | J 17 | MOSFET Transistor  5 V |
| SENSOR_VN | J 4 | GPIO39, ADC1_CH3, RTC_GPIO3 |
| SENSOR_VP | J 5 | GPIO36, ADC1_CH0, RTC_GPIO0 |
| - | J  9 | Ground |
|  - | J 10 | Power 3.3 V |
|  - | J  2| Power  12 V |

Für mehr Details siehe das Datasheet des Controllers: [Datasheet](./Datasheets/ESP32/esp32-wroom-32_datasheet_en.pdf))

## Probleme mit v01

- sehr hohe Last auf Ground
  - diese Leiterbahnen sollten breiter und idealerweise kürzer sein
- zentraler Ground von ESP32 nicht wirklich lötbar
  - hier richtige Löcher, damit man auf der Rückseite mit dem Lötkolben auch hinkommt
- Pads von Spanungsregulierer anpassen
  - verhindern von Verbindungen von 12 V und 3.3 V beim Löten
- anpassen der Löchergrößen um Pins einfacher durchsteckbar zu machen
- fehlender Pin für 5 V
- Verbindung von Dir mit 5 V, damit Richtung stimmt
- mehr Pins für GND and 12 V
- weitere Pins für freie IO Ports
- Benennung und Beschriftung der Pins
- verbinde benutzbare Pins, nicht (nicht 17-22, da diese intern vom ESP32 benutzt werden, und nicht verbunden sind)

## Flashen des ESP32

(Nur für einen neuen Controller notwendig, alle weiteren Updates können OTA erfolgen)

Verbinden von RX/TX mit Flipper, oder anderem Board.
Flipper oder alternatives Board als UART-USB-Bridge verwenden.
In WLED folgenden Command ausführen.
Davor den Boot-Button am Controller drücken,
um diesen in den Boot-Modus zu versetzen.

´´´bash
pio run -e esp32dev -t upload
´´´
Nach erfolgreichem Flashen den ESP32 mit dem Reset-Button resetten.

## Links

### WLED

- [WLED-Knowlege base](https://kno.wled.ge)
- [WLED-Github](https://github.com/WLED/WLED)
- [WLED-MM](https://github.com/MoonModules/WLED-MM): More advanced WLED with additional / experimental features

### LED-FX (Audio-Reactive)

- [LED-FX-Github](https://github.com/LedFx/LedFx)
- [LED-FX-Documentation](https://docs.ledfx.app/en/latest/installing.html)

# Schaltplatine Flur für WLED

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

| IO Pin ESP | Board Output | Usage |
| ---------------:| ---------------:| ---------------:|
| IO  1 | J  7 | IO Port / TX |
| IO  3 | J  8 | IO Port / RX |
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
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
|    | J | IO Port |
| - | J  9 | Ground |
|  - | J 10 | Power 3.3 V |
|  - | J  2| Power  12 V |

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

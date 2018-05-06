# NodeMCU-BME280-MQTT-Energy-Saving

This sketch publishes temperature humidity and barometric pressure data from a bme280 device to a MQTT topic.
It also publish the battery voltage but you have to install a voltage divider. 
(see  https://en.wikipedia.org/wiki/Voltage_divider if needed).
 

        Vin <---o
              __|_
             |    |
             | R1 |
             |____|
                |                                       R2
                o-------> Vout --> A0         Vout = --------- x Vin
              __|_                                   (R1 + R2)
             |    |
             | R2 |                           Vout MUST BE < 1 V !!!
             |____|
                |                       (I choose R1 = 470 k and R2 = 100 k
               _|_                    but feel free to choose your own values!)
               /// Gnd
                
 
This sketch goes in deep sleep mode once the data has been sent to the MQTT topic and wakes up periodically.
(configure SLEEP_DELAY_IN_SECONDS accordingly).
 
Hookup guide:
 
 - connect D0 pin to RST pin in order to enable the ESP8266 to wake up periodically
   (only after uploading the sketch!)
 - connect the Vout of your voltage divider to NodeMCU A0
 - connect the bme280:
     BME280 GND --> NodeMCU GND
     BME280 3.3V --> NodeMCU 3V3
     BME280 SDA --> NodeMCU D3
     BME280 SCL --> NodeMCU D2
     
 This sketch is the result of the compilation of some diyers and arduinoers. Thanks to them!
 And of course it is in public domain.

 Enjoy!

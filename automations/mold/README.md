# Mold Prevention
Relative humidity is strongly influenced by room temperature. A room at 7 °C with 70% humidity contains less actual moisture than a room at 20 °C with 50% humidity. To determine the need for ventilation more reliably, this automation uses **absolute humidity** instead of relative humidity.

You could calculate absolute humidity manually, but this setup uses the HACS plugin **[Thermal Comfort](https://github.com/dolezsa/thermal_comfort/)**. It provides various useful entities such as absolute humidity, dew point, freezing point, and several comfort indicators.

This automation relies on absolute humidity and the dew point. One *Thermal Comfort* device is created for outdoor data, and additional *Thermal Comfort* devices are created for each room.

The automation sets the Boolean for a room to **true** when:
- the outdoor temperature is below the dew point  
- the absolute humidity in the room is at least **3.5 g/m³** higher than the outdoor absolute humidity

If these conditions are not met, the Boolean is set to **false**

## Used hygrometers
I'm using the Aqara temperature and humidity sensors.
They might mot be the most accurate sensors, but they are cheap and I think the'll suffice for my use case.
I've integrated them directly into Home Assistant by using the Zigbee2MQTT integration.

## Source
An explanation of the relations between relative humidity and temperature, and why it might not be the best indicator, can be found here:
[YouTube - Mit absoluter Luftfeuchte: Home Assistant meldet: "Bitte lüften" mit Sonoff ZigBee-Hygrometer](https://youtu.be/gX_Q9Af9T5Y?si=-VY07BZAX4g6V9AD)

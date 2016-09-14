# WiFi Radio Thermostat

## MIG Interface for Radio Thermostat with WiFi USNAP Module.

This interface provides the same REST interface that ZWave Thermostats 
uses, as far as I can tell. This means you should be able
to use any thermostat widget that works with ZQave, including the default.

The module address is assigned as the last part of the IP address, so a 
thermostat at address 192.168.1.14 will be RadioThermostat 14.

If you do not want to have to recreate the module every time a different
address is assigned, you have two options:
1. Use a static IP address on the thermostat itself
2. Have your router assign the same address every time based on the MAC
   address

I am open to suggestions, requests and bug reports. You can keep gratuitous 
criticisms to yourself :)




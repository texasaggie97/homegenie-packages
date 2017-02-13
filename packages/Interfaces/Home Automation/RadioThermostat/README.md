# WiFi Radio Thermostat

## MIG Interface for Radio Thermostat with WiFi USNAP Module.

This interface provides the same REST interface that ZWave Thermostats 
uses. This means you should be able to use any thermostat widget that 
works with ZWave, including the default.

Once installed, you will need to enable the RadioThermostat interface by
going to Configure -> Settings -> RadioThermostat Options -> Enable

There is a separate program supplied that polls the thermostat for updated
informatio at specific intervals. This must be enabled for each thermostat
after adding the module.

The module address is assigned as the last part of the IP address, so a 
thermostat at address 192.168.1.14 will be RadioThermostat 14.

There are some additional api endpoints beyond the Z-Wave endpoints. 
They are:
* \<homegenieserver\>/api/HomeAutomation.RadioThermostat/\<ModuleAddress\>/Thermostat.StartQuery
   * This will start a background query to update HomeGenie with the current status of the thermostat
   * This is used in the thermostat poll program
* \<homegenieserver\>/api/HomeAutomation.RadioThermostat/\<ModuleAddress\>/Thermostat.GetCacheValid
   * Certain operations require the state of the thermostat in HG be up to date
   * This will return the current timeout that is used before triggering an update in minutes (default 3 minutes)
* \<homegenieserver\>/api/HomeAutomation.RadioThermostat/\<ModuleAddress\>/Thermostat.SetCacheValid/<value>
   * Certain operations require the state of the thermostat in HG be up to date
   * This will set the current timeout that is used before triggering an update in minutes (default 3 minutes)
* \<homegenieserver\>/api/HomeAutomation.RadioThermostat/\<ModuleAddress\>/Thermostat.SetPointSet/Agnostic/<value>
   * The radio thermostat has different setpoints based on operating mode such as 'Heating' or 'Cooling'.
   * When using .../Thermostat.SetPointSet/Heating/ or .../Thermostat.SetPointSet/Cooling/, the operating mode must match.
   * 'Agnostic', on the otherhand, reads the current mode and uses that to set the setpoint
* \<homegenieserver\>/api/HomeAutomation.RadioThermostat/\<ModuleAddress\>/Thermostat.GetModel
   * Returns the current thermostat model

If you do not want to have to recreate the module every time a different
address is assigned, you have two options:
1. Use a static IP address on the thermostat itself
2. Have your router assign the same address every time based on the MAC address

I am open to suggestions, requests and bug reports. You can keep gratuitous 
criticisms to yourself :)




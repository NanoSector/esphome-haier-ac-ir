# ESPHome Haier AC IR remote control component

This implementation of the ESPHome component to control HVAC with IR channel.

Base implementation of the protocol can be found here: [https://github.com/crankyoldgit/IRremoteESP8266](https://github.com/crankyoldgit/IRremoteESP8266)

## Supported AC remotes

This repository is developed against a Haier AS35TADHRA-1 with V9014557 KA9 HTD remote control.
It is derived from [rozh1/esphome-haier-ac-ir](https://github.com/rozh1/esphome-haier-ac-ir) which is developed against a different
set of air conditioners.

Under the hood it uses the HAIER_AC176 platform as provided by the IRremoteESP8266 library which supports many more Haier ACs.

## How to use

1. Add sensor configuration. It can be a connected temperature sensor or home assistant provided sensor. For example:

```
sensor:
  # External temperature sensor from Home Assistant 
  - platform: homeassistant
    id: current_temperature
    entity_id: ${temperature_sensor}
```

2. Add climate component, set platform as `haier_ac176`, set `sensor_id` and `pin` number for IR LED. 

```
climate:
  - platform: haier_ac176
    sensor_id: current_temperature # Sensor ID with the current temperature
    pin: 3 # Pin with IR led
    name: "AC Haier"
```
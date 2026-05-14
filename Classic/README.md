# SlimmeLezer
## Current version of the SlimmeLezer

![SlimmeLezer](./img/SlimmeLezer.png)

### Important pin-out

Uart:
```yaml
uart:
  baud_rate: 115200
  rx_pin: D7
  rx_buffer_size: 1700
```

Uart for older systems like dsmr 2 and 3:
```yaml
uart:
  baud_rate: 9600
  data_bits: 7
  parity: NONE
  stop_bits: 1
  rx_pin: D7
  rx_buffer_size: 1700
```

Note that dsmr 2 and 3 doesn's support crc check and must be disabled:
```yaml
dsmr:
  crc_check: false
```

Button (used for factory reset)
```yaml
switch:
  - platform: factory_reset
    name: Restart with Factory Default Settings
    id: resetbutton
    internal: true

binary_sensor:
  - platform: gpio
    name: "Reset switch GPIO5"
    pin: 
      number: GPIO5
      mode:
        input: true
        pullup: false
    on_press: 
      then:
        - logger.log: "Reset button pressed"
        - switch.turn_on: resetbutton
```

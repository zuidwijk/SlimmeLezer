# SlimmeLezer-Pro
SlimmeLezer Pro with ESP32-C3 and W5500 Ethernet
![SlimmeLezer Pro](/img/SlimmeLezer-Pro.png)

## The new successor for the SlimmeLezer
A powerfull small compact redesign with allmost the same measurements: 26,25 x 61,75 mm 
- ESP32 C3
- Ethernet (W5500)
- Passthrough for second P1 device
- Power and statusled

### Important pin-out

Ethernet:
```YAML
ethernet:
  type: W5500
  clk_pin: GPIO06
  mosi_pin: GPIO04
  miso_pin: GPIO05
  cs_pin: GPIO07
  interrupt_pin: GPIO02
  reset_pin: GPIO10
  clock_speed: 25MHz
```
Uart:
```YAML
uart:
  - id: p1_uart
    rx_pin:
      number: 20
      inverted: true
    baud_rate: 115200
    rx_buffer_size: 1700
  - id: p1_bridge_uart
    tx_pin:
      number: 21
    baud_rate: 115200
```
Button (for flashing and factory reset)
```YAML
binary_sensor:
  - platform: gpio
    name: "Reset switch GPIO9"
    id: reset_button
    pin: 
      number: GPIO09
      mode:
        input: true
        pullup: true
```
Status LED
```YAML
status_led:
  pin:
    number: GPIO08
    inverted: true
    id: led
```

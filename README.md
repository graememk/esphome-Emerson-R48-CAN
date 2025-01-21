# esphome-Emerson-R48-CAN
esphome implementation of the emerson/vertiv CANBUS communication in esphome

Using Lilygo T-CAN485 board

Something that tripped me up initially with the lilygo board is that the CAN or the RS485 chip has to be enabled for it to work

Sleeper85 was very helpful with these intital configs for it
https://github.com/Xinyuan-LilyGO/T-CAN485/issues/16#issuecomment-2595962388
```
# +--------------------------------------+
# | LilyGo T-CAN485 related config       |
# +--------------------------------------+

output:
  # MAX13487E SHDN (enable RS485 chip)
  - platform: gpio
    id: RS485_SE
    pin:
      number: 19
      inverted: true # set HIGH level
  # MAX13487E RE (enable RS485 autodirection)
  - platform: gpio
    id: RS485_EN
    pin:
      number: 17
      inverted: true # set HIGH level
  # RS485 and CAN Boost power supply
  - platform: gpio
    id: CGQ_EN
    pin:
      number: 16
      inverted: true # set HIGH level
  # SN65HVD231DR RS PIN (CAN high speed mode)
  - platform: gpio
    id: CAN_SE
    pin:
      number: 23
      inverted: false # set LOW level
```
Thanks go to this forum post, Without it, I wouldnt have been able to do it
https://endless-sphere.com/sphere/threads/emerson-vertiv-r48-series-can-programming.114785/

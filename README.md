# 1.53" ST77916 QSPI with ESP32-D0WDQ6

<img src="./devboard.jpg" alt="drawing" width="300"/>

---

### Dependencies
- ESP IDF v5.1.6
- espressif/esp_lcd_st77916 v1.0.1

---

### Hardware
- ESP32-D0WDQ6

- 1.53" ST77916 Quad SPI
---

This is a simple project based on the espressif example [spi_lcd_touch](https://github.com/espressif/esp-idf/tree/master/examples/peripherals/lcd/spi_lcd_touch) (without the touch part) that uses the 1.53" display ST77916 in Quad SPI Mode with the espressif component [ESP LCD ST77916](https://components.espressif.com/components/espressif/esp_lcd_st77916/versions/1.0.1/readme).

The display that I used can be found in this [AliExpres link](https://pt.aliexpress.com/item/1005009627590639.html). It's a 1.53" 360x360 pixels with Quad SPI interface.

With the default code from the espressif component library the display **will not work**. It needs a specific init commands for this 1.53" version.

Using the initialization code `st77916_150_init_operations` from [Arduino_GFX](https://github.com/moononournation/Arduino_GFX/blob/master/src/display/Arduino_ST77916.h#L51) library, I was able to get the display working correctly.

---

### Wiring
| Display    | ESP32 |
|------------|-------|
| GND        | GND   |
| VCC        | 5v    |
| SCL        | 18    |
| SDA (IO 0) | 19    |
| IO 1       | 23    |
| IO 2       | 21    |
| IO 3       | 22    |
| RST        | 4     |
| CS         | 5     |
| BL         | 17    |
| TE         | -     |

### Issues

Besides the initialization code, I had a issue with the development board that I used in this test, the Lolin32 Lite.

The GPIO21(VSPIHD) was not routed to a pin in the board. I had to bodge a wire directly to the IC pad.

<img src="./bodge.jpg" alt="drawing" width="500"/>

# 40-pin header pinout

Numbers below are **physical header pin numbers**. `GPIO` refers to the ESP32-S3 GPIO number, not a Raspberry Pi BCM number. The table is intended to be read from the connector's pin 1 marker; it does not assume a particular viewing direction of the underside of the PCB.

| Pin | Signal | Typical use | Pin | Signal | Typical use |
| ---: | --- | --- | ---: | --- | --- |
| 1 | 3V3 | 3.3 V rail | 2 | 5V | 5 V rail |
| 3 | GPIO5 | I2C SDA | 4 | 5V | 5 V rail |
| 5 | GPIO6 | I2C SCL | 6 | GND | Ground |
| 7 | GPIO16 | I2S MCLK | 8 | GPIO43 | UART0 TX |
| 9 | GND | Ground | 10 | GPIO44 | UART0 RX |
| 11 | GPIO1 | General GPIO | 12 | GPIO8 | I2S BCLK |
| 13 | GPIO2 | General GPIO | 14 | GND | Ground |
| 15 | GPIO21 | General GPIO | 16 | GPIO41 | General GPIO |
| 17 | 3V3 | 3.3 V rail | 18 | GPIO40 | General GPIO |
| 19 | GPIO11 | SPI MOSI | 20 | GND | Ground |
| 21 | GPIO13 | SPI MISO | 22 | GPIO39 | General GPIO |
| 23 | GPIO12 | SPI CLK | 24 | GPIO10 | SPI CS0 |
| 25 | GND | Ground | 26 | GPIO0 | BOOT strap / GPIO |
| 27 | GPIO17 | ID SDA / GPIO | 28 | GPIO47 | ID SCL / GPIO |
| 29 | GPIO4 | General GPIO | 30 | GND | Ground |
| 31 | GPIO14 | General GPIO | 32 | GPIO18 | General GPIO |
| 33 | GPIO38 | General GPIO | 34 | GND | Ground |
| 35 | GPIO7 | I2S LRCLK | 36 | GPIO42 | General GPIO |
| 37 | GPIO3 | Boot strap / GPIO | 38 | GPIO15 | I2S DIN |
| 39 | GND | Ground | 40 | GPIO9 | I2S DOUT |

`I2S DIN` and `I2S DOUT` are named from the ZeroCore S3 / ESP32 side: DIN is input to the ESP32 and DOUT is output from it. GPIO16/MCLK is present on the header; whether it is driven depends on the firmware and attached audio device. Pins 27/28 occupy the Raspberry Pi HAT ID positions but are connected to ESP32 GPIO17/47; they are not a Raspberry Pi ID bus unless the firmware and connected hardware implement that behavior.

All GPIO use **3.3 V logic** and are not 5 V tolerant. The 3V3 pins are the regulated 3.3 V rail, not 5 V inputs. Keep GPIO0 and GPIO3 free of loads that could disturb boot. Check the [functional block diagram](block-diagram.md) for the power and data paths.

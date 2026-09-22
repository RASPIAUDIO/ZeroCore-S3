# Functional block diagram

```mermaid
flowchart LR
    USB[USB-C<br/>5 V + USB 2.0 data] --> PWR[5 V input and protection]
    PWR --> RAIL[5 V board/header rail]
    RAIL --> REG[3.3 V regulator]
    REG --> ESP[ESP32-S3-WROOM-1U<br/>16 MB flash / 8 MB PSRAM]
    USB -- USB data --> ESP
    ANT[External antenna] --- ESP
    BOOT[BOOT / IO0 and RESET] --> ESP
    ESP -- I2C, I2S, SPI, UART, GPIO --> HDR[40-pin header]
    RAIL --> HDR
    REG --> HDR
    HDR -. optional connection .-> DSP[Voice DSP+ or other 3.3 V-compatible hardware]
    ESP -. Wi-Fi / BLE .-> HA[Home Assistant and local network]
```

The ESP32-S3 handles connectivity and the application running on the controller. In the Voice DSP+ satellite, microphone processing, acoustic algorithms and speaker amplification are on the separate Voice DSP+ board. Home Assistant runs elsewhere on the network.

USB-C supplies a conventional 5 V input; this board does not negotiate USB Power Delivery. The 5 V header pins share the board's 5 V power domain. Review the supply arrangement before connecting another powered board: do not assume two independent 5 V sources can be paralleled safely. The block diagram explains function, not individual component connections or a current rating.

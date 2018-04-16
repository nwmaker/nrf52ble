# nRF52 BLE

## setup
- [x] use Nordic SDK nRF5 v15.0.0
- [x] use armgcc
- [x] use [nRF52832](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF52832)
- [x] use S132

## custom BLE

### 1 use the template from SDK 

copy and modify nRF5_SDK_15.0.0_a53641a/examples/ble_peripheral/ble_app_template

### 2 create the custom service

create a 128-bit UUID [here](https://www.uuidgenerator.net/version4)
```
ab74b505-909a-4b23-8634-8b86c7effe72
```
convert this 8-4-4-4-12 big-endian to little endian for the ARM code.

flash the S132 v5.0.0 SoftDevice and then flash our application.


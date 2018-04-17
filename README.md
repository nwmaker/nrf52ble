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

modify the code

flash the S132 v5.0.0 SoftDevice and then flash our application.

use nRF connect to scan for the services.

### 3 add a custom characteristic to the custom service

After flashing the App, use nRF Connect to check.

### 4 handle events from the SoftDevice

Start to handle both connect and disconnect events from the SoftDevice

### 5 handle the write event from the SoftDevice

Check ble_gatts_evt_write_t const *p_evt_write. It has a data field which can be used to do something.





## reference
[custom BLE service](https://github.com/bjornspockeli/custom_ble_service_example)

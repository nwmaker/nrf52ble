# nRF52 BLE

## Setup
- [x] use Nordic SDK nRF5 v15.0.0
- [x] use armgcc
- [x] use [nRF52832](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF52832)
- [x] use S132 v6.0.0 (BLE stack for both central and periperal)
- [x] use nRF52 DK
- [x] use JLink
- [x] test with nRF Connect app

## BLE custom service

### use the template from SDK 

copy and modify nRF5_SDK_15.0.0_a53641a/examples/ble_peripheral/ble_app_template

### create the custom service

create a 128-bit UUID [here](https://www.uuidgenerator.net/version4)
```
ab74b505-909a-4b23-8634-8b86c7effe72
```
convert this 8-4-4-4-12 big-endian to little endian for the ARM code.

modify the code

flash the S132 v5.0.0 SoftDevice and then flash our application.

use nRF connect to scan for the services.

### add a custom characteristic value to the custom service

After flashing the App, use nRF Connect to check.

### handle the standard events from the SoftDevice

Start to handle both connect and disconnect events from the SoftDevice

### handle the write event from the SoftDevice

Check ble_gatts_evt_write_t const *p_evt_write. It has a data field which can be used to do something.
```
struct ble_gatts_evt_write_t {
  uint16_t handle;
  ble_uuid_t uuid;
  uint8_t op;
  uint8_t auth_required;
  uint16_t offset;
  uint16_t len;
  uint8_t data[1];
}
```

### pass the custom service events to the app

Add custom service events and its handler. when the BLE_GAP_EVT_CONNECTED is received from the SoftDevice, pass it to on_connect() in ble_cus.c. There it is converted to BLE_CUS_EVT_CONNECTED.

### notify the custom characteristic value changes with a timer

Timer drive the value change. The change is sent out by the notification.

## Reference
* [NordicSemi online doc](https://infocenter.nordicsemi.com)
* [custom BLE service](https://github.com/bjornspockeli/custom_ble_service_example)

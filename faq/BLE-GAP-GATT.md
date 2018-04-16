# BLE

## GAP vs GATT

### Generic Access Profile

For BLE devices to communicate with the outside world, it has to broadcast itself and be able to connect or be connected to form the network.

Both broadcasting and connecting mechanisms fall in GAP (Generic Access Profile). As to broadcasting, there are two roles: broadcaster or observer. When it comes to connecting, there are two roles too: peripheral or central. The peripheral device advertises its presence so that the central could initiate the connection by sending the connection request. After being connected, the peripheral stops broadcasting and the central is responsible to read or write to the peripherals. After connection, either the central or the peripheral could terminate the connection. During the connection, only the central can modify the connection parameters. But the peripheral could ask the central to do this.  

### Generic Attribute Profile

GATT profile defines a hierarchical data structure that is exposed by the BLE devices. It is built on the top of the Attribute Protocol (ATT).

GATT: Profile: Service: Characteristic: Propertie, Value and Descriptor.

The roles here are client and server. The client sends a request to the GATT server. It reads and/or writes attributes found in the server. The server stores the attributes and makes them available to the clients.

### Summary
 
GAP and GATT roles are essentially independent of one another. Peripheral or central devices can BOTH act as a server or client, depending on how data is flowing.

## Ref
[BLE](https://punchthrough.com/bean/docs/guides/everything-else/how-gap-and-gatt-work/)

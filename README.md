# depaula-contrib-ethip

A Node-RED depaula's prototype node to interact with UR20-FBC-EIP Weidmueller device with Ethernet/IP protocol.
Based on the awesome work of [plc/depaula_eip].


## Installing

You can install this node directly from the "Manage Palette" menu in the Node-RED interface. There are no external dependencies or compilation steps.

Alternatively, run the following command in your Node-RED user directory - typically `~/.node-red` on Linux or `%HOMEPATH%\.nodered` on Windows

        npm install depaula-contrib-ethip


## Usage

Just drop a `depaula_eip in` node to read and watch addresses of the device, or a `depaula_eip out` node to write values to the device. Both of them need a `depaula_eip endpoint`, where you can configure the address of the device (IP Address, port, and routing), the cycle time and timeout values, and the list of addresses available on the device.


### Addressing

The addresses follow the same syntax of what would be used on RSLogix, so for example `B3:0/0` addresses the bit 0 of byte 0 in the file B3, and `F8:1` points to the float 1 at the file F8.


### About routing

The configuration of routing follows a very special syntax for now

    0x01,0x00,0x01,0x00
      |    |    |    |
      |    |    |    +-- 0: The slot (position)
      |    |    +------- 1: Route over the backplane
      |    +------------ Reserved, always zero
      +----------------- 1: Number of words (1 = 2 bytes) of the routing section

You most likely just want to change the last number to the slot of the device when connecting 


## Wishlist
- Validate addresses
- Improve routing configuration


## Bugs and enhancements
Please share your ideas on my email


## License

Copyright 2016-2017 Smart-Tech, [Apache 2.0 license](LICENSE).

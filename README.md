# Xbee
Repository for notes and code for communicating with Xbee

### Setup RPi 3 for Serial Communication
Raspberry Pi does not have the GPIO (UART) pins available for serial communication by default. You need to disable the shell/kernel use of the serial port and enable it for GPIO with the following instructions:

* `sudo raspi-config`
* Interfacing Options
* Serial
* Disable for kernel/shell
* Enable for GPIO
* Reboot

One rebooted, you can use `ls -l /dev` to view the ports and you should see one that says `serial0 --> ttyS0`. Now, serial0 can be used as an alias because previous raspberry pi's did not have ttyS0 because they didn't have a Bluetooth module and simply used ttyAMA0 instead. You can reference the alias as `/dev/serial0`

### Wiring XBEE to RPi 3
Having the XBEE share the same power rails and ground as the other components caused fairly large voltage dropouts. When wiring the XBEE to the RPi 3, and expecting to power other components with 3.3v, your best bet is to provide the XBEE with its own 3.3v and GND pin.

### Arduino to XBEE Communication 1
The first type of communication available from Arduino to XBEE is through the Serial Port. Once serial is received, it is forwarded to the coordinating XBEE in the network. This allows the Arduino to read inputs, perform processing, and pass a custom data frame to the XBEE.

### Arduino to XBEE Communication 2
The second type is for the Arduino to read an input, perform processing, and then set its DO/AO pin to a value. The XBEE is connected to the output pin, which means the XBEE can read the signal and forward anormal data frame to the coordinator. If the coordinator is only expected/programmed to read data frames, then this option is the most enticing.

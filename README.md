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




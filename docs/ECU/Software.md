# Software

## Setup

- Download & install the [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)
- Clone the [main-ECU](https://github.com/TUfast-motoelectric/main-ECU) and checkout the master branch
- Import the project via **Import**->**STM32CubeMX/STM32CubeIDE Project**->`<Select the cloned repository>`
- Compile & upload the code via the IDE

### Windows/macOS

Probably works as is

### Linux

Linux might not recognize the ST-Link because of a permissions issue. You can test this via the [st](https://github.com/stlink-org/stlink) package. If

```shell
st-info --probe
```

also doesn't detect the ST-Link, you might have to adjust the stlink rules:

```shell
sudo tee /etc/udev/rules.d/path-to-rules.rules << 'EOF'
SUBSYSTEM=="usb", ATTR{idVendor}=="0483", MODE="0666" # This is the USB Device:
EOF

sudo udevadm control --reload-rules
sudo udevadm trigger
```

(or if using fish):

```fish
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="0483", MODE="0666"' | sudo tee /etc/udev/rules.d/path-to-rules.rules

sudo udevadm control --reload-rules
sudo udevadm trigger
```

Unplug & replug the board
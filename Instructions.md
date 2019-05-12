# Installation Instructions

## Install a Bootloader


### 1. Configure AVRDude and connect GPIO Pins

Follow instructions from https://www.fission3d.com/guides/flash-bootloader-and-install-firmware-with-raspberry-pi

### 2. Test the Programmer Connection

```
sudo avrdude -p atmega1284p -C ~/avrdude_gpio.conf -c pi_1 –v
```

### 3. Flash the Sanguino bootloader

```
wget https://github.com/Lauszus/Sanguino/releases/download/1.0.3/Sanguino-1.0.3.zip
unzip Sanguino-1.0.3.zip
sudo avrdude -p atmega1284p -C ~/avrdude_gpio.conf -c pi_1 -v -U flash:w:Sanguino/bootloaders/optiboot/optiboot_atmega1284p.hex:i
```

### Now you have a Bootloadable Firmware that you can upload firmware directly over USB


## Build Marlin

### 1. Install PlatformIO

```
brew install platformio
```

### 2. Build Marlin and Upload Firmware

```
platformio run --environment=sanguino_atmega1284p
```

### 3. Upload the Firmware

```
platformio run --environment=sanguino_atmega1284p --target=upload
```

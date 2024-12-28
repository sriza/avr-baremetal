all:
	rm -r build || true
	mkdir build
	avr-gcc -mmcu=atmega2560 -DF_CPU=16000000UL -o build/main.elf main.c
	avr-objcopy -O ihex build/main.elf build/main.hex
	avr-size --format=avr --mcu=atmega2560 build/main.hex

flash: all
	avrdude -v -p m2560 -U flash:w:./build/main.hex -c usbasp -P usb

fuse:
	avrdude -p m2560 -c usbasp -U lfuse:w:0xFF:m -U hfuse:w:0xD8:m -U efuse:w:0xFD:m

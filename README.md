#build
sudo make
sudo make install

#activate
add to /boot/config.txt
dtoverlay=rpi-i2s-dac-adc

sudo modprobe rpi-i2s-dac-adc
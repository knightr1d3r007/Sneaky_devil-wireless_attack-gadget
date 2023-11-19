# OpenWRT-dropbox-mini-router


In order to bring life to this little project, a bit a basic soldering skills are required to upgrade the current eeprom SPI (flash chip) on the "A5-v11_3G_mini_router". Currently in 2023, this device can be obtained from ebay or aliexpress for around $8.






# REQUIREMENTS:



1.-We'll upgrade the mini router to 16MB with the chip "W25Q128". It can be found for a couple of bucks on aliexpress
https://www.aliexpress.us/item/3256804269088009.html

2.- The programer flasher ch341a with an clip adapter, which is very inexpensive and its supported for the awesome tool flashroom.
https://www.ebay.com/itm/285027193020

3.-An iron and solder

4.-A PC running linux


# BEFORE ANYTHING (just in case):



We need to grab a copy of your original flash chip. We will not needed it for this project, but better safe than sorry. So, desolder/remove the flash chip from the mini router and connect it to the clip adapter from the ch341a programmer and run the command:


1.- This command will detect the flash chip (and its number) you removed from the A5-V11 mini router:

sudo apt install flashrom

sudo flashrom -p ch341a_spi 


2.- This commnad copy the chip's content to a file

sudo flashrom -p ch341a_spi -c <detected flash chip> -r original-fullflashchip-backup.bin 


# NEXT STEPS:

1.- First, we need to create a blank canvas (named 'padded.bin') of 16MB for the new flash chip.
running the following command:

 dd if=/dev/zero bs=1M count=16 of=16MBpadded.bin


2.- We will need a new Uboot for our OpenWRT-dropbox-mini-router. 

Get it from this site https://disk.yandex.com/d/ubSsjNZU34Xk2L and choose the file/image called 'Uboot_usb_256_03.img'


3.- Flash it into the new 16MB SPI. So, grab the "W25Q128" chip you bought. 
Connect it to the Programmer Clip and flash the file 'Uboot_usb_256_03.img' with the following command:  

dd if=Uboot_usb_256_03.img conv=notrunc of=16MBpadded.bin





## to be continued




exit

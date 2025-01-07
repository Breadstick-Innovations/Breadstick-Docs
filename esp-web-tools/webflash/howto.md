upload the firmware from the repo with the -v flag
`pio run -v -t upload`

use the output just before the upload proccess to get the files for the below code

`esptool --chip esp32 merge_bin \
  -o merged-firmware.bin \
  --flash_mode dio \
  --flash_freq 40m \
  --flash_size 4MB \
  0x1000 bootloader.bin \
  0x8000 partitions.bin \
  0xe000 boot.bin \
  0x10000 your_app.bin
`

for example:
`python "C:\Users\codyj\.platformio\packages\tool-esptoolpy@1.30100.210531\esptool.py" 
--chip esp32 merge_bin -o merged-firmware.bin --flash_mode dio --flash_freq 80m --flash_size 8MB 
0x1000 C:\Users\codyj\.platformio\packages\framework-arduinoespressif32\tools\sdk\bin\bootloader_qio_80m.bin 
0x8000 C:\Users\codyj\Documents\Github\Repos-BreadstickInnovatons\WLED15\.pio\build\esp32dev_nougatquad\partitions.bin 
0xe000 C:\Users\codyj\.platformio\packages\framework-arduinoespressif32\tools\partitions\boot_app0.bin 
0x10000 .pio\build\esp32dev_nougatquad\firmware.bin `

paste (as 1 line) into platformio terminal to create the merged-firmware.bin

move that file to appropriate folder in this repo and create manifest file. 

-cj Jan 6, 2025


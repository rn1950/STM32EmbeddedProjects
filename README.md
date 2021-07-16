This is a repo for all my projects using the Nucleo H743ZI2 Development Board

HAL Documentation: https://www.st.com/resource/en/user_manual/dm00392525-description-of-stm32h7-hal-and-lowlayer-drivers-stmicroelectronics.pdf

In order to start the GDB server on the Segger Jlink

```
JLinkGDBServer -device STM32H743ZI
```

In order to start GDB server on the host machine, add some break points and debug:

https://wiki.segger.com/J-Link_GDB_Server

```
gdb-multiarch
file ~/STM32..... path to .elf file
target remote localhost:2331
monitor reset
break main.c
break main.c:55
p var_name
continue
```

Project: Test

* Code taken from : https://medium.com/@rlamarrr/introduction-to-stm32cube-blinking-an-led-61469168f9e4
* Modified to have two LED's blink
* LED pins found from MBED site: https://os.mbed.com/platforms/ST-Nucleo-H743ZI2/

Project: IntroToADC

Project: IntroToDAC

* Look on pg. 14 for the conversion formulas. We know we want the output to be a certain value, so we solve for DOR https://www.st.com/resource/en/application_note/cd00259245-audio-and-waveform-generation-using-the-dac-in-stm32-products-stmicroelectronics.pdf

Pieces needed to configure (chronological order don't straight copy paste)
'''
//Set already is using cube auto config
DAC_HandleTypeDef hdac1;
static void MX_DAC1_Init(void);
MX_DAC1_Init();

//We need to put
HAL_DAC_Start(&hdac1, DAC_CHANNEL_1);
HAL_DAC_SetValue(&hdac1, DAC_CHANNEL_1, DAC_ALIGN_12B_R, var);
'''

Project LowPassFilter


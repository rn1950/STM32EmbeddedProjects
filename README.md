This is a repo for all my projects using the Nucleo H743ZI2 Development Board

In order to start the GDB server on the Segger Jlink

```
JLinkGDBServer -device STM32H743ZI
```

In order to start GDB server on the host machine, add some break points and debug:

```
gdb-multiarch
file ~/STM32..... path to .elf file
target remote localhost:2331
monitor reset
load
break main.c
break main.c:55
continue
```

Project: Test

* Code taken from : https://medium.com/@rlamarrr/introduction-to-stm32cube-blinking-an-led-61469168f9e4
* Modified to have two LED's blink
* LED pins found from MBED site: https://os.mbed.com/platforms/ST-Nucleo-H743ZI2/

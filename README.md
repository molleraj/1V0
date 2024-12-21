# 1V0
1V0  (Pronounced "Ivo".)

Presented is a new programming language/virtual machine for ATTiny85, Arduino UNO/MEGA2560/DUE, ESP8266, Java MIDP 1.0/2.0 (CLDC 1.1) enabled phones, of assembler-like nature and operating on floating point (or fixed point) numbers as its exclusive data type, and with implementations in C and Java for the command line. The aim is a most portable "small mainframe in early 1940s to 1960s style" that can practically run on nearly any ever so feeble device. It shall fill the niche where BASIC interpreters are "too big" or not comfortable enough to use. Where practicable, it runs from (at least emulated) EEPROM.

YouTube:  https://youtu.be/dZ4dWOTq1ac

GitHub:  https://github.com/KedalionDaimon/1V0

The Java files without date are the midlets, whereby IVO.jar is the MIDP2.0/CLDC1.1 midlet and IVOnano.jar is the MIDP1.0 midlet which should run on the most ancient Java-enabled mobiles.

Regarding how to use it, check the PDF documentation and the Youtube video.

"To start as quickly as possible", run on your preferred desktop OS (should be fine with Linux, Windows, Mac, and various BSDs):

java -jar IVO_Java.jar

If you prefer to compile in C, practically any C compiler should work, but e.g. in GCC just do:

gcc -o 1V0 1V0_20200709.c  -lm -Warray-bounds -Wstrict-aliasing

The "reference implementation" is the C version.

2024-12-14:

The so far most portable variant "1V0 Tzetanka IV" has been ported to the ZX Spectrum - see the files 1V0TzIV220zx_20241213a.c and ivo_tz_4.tap, compiled with the following command using z88dk: zcc +zx -clib=new -create-app 1V0TzIV220zx_20241213a.c -o ivo -create-app ; the manual is 1V0TzIV_ZXSpectrum.txt.


For CP/M, to compile, use:

ack -mcpm -o IVOPX8.COM 1V0TzIV220zx_20241213a_mini.c

and for the Epson PX-8 "Geneva", which can only operate a subset of the above due to space constraints, use:

ack -mcpm -o IVOCPM.COM 1V0TzIV220zx_20241213a.c

(Might need to explicitly use Ctrl-M,Ctrl-J for "Enter".)

(How to transfer via RS232 to the Epson PX-8 Geneva from Linux:

Set up the port on:

sudo stty -F /dev/ttyUSB0 300 cs8 -parenb -cstopb -echo -ixon raw

possibly also:

picocom --baud 300 --parity n --databits 8 --stopbits 1 --flow n --receive-cmd "rz --vv" --send-cmd "sz" --emap delbs --imap del
bs,crcrlf /dev/ttyUSB0

Ctrl-A,Ctrl-Q

On the Epson PX8: for receipt, use term, and record (while displaying):

dd if=IVOPX8.COM bs=1 | pv -L 20 | dd of=/dev/ttyUSB0 status=progress

where pv slows down the transfer rate to 20 characters per second.)




Nino Ivanov

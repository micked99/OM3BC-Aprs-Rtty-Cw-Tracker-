# OM3BC-Aprs-Rtty-Cw-Tracker-
OM3BC Aprs-Rtty-Cw Tracker 
OM3BC tracker info
Some extended information about the OM3BC tracker found here: www.om3bc.com/docs/payload/payload_en
![nQnfMv6](https://user-images.githubusercontent.com/9722781/172041488-3ce025c8-4d81-4125-87fd-9c55f7e753b2.jpg)
![IMG_20200208_191239](https://user-images.githubusercontent.com/9722781/172041491-35db30a9-cf1e-4c13-9caa-79874d13a028.jpg)
Some extended information about the OM3BC tracker found here: www.om3bc.com/docs/payload/payload_en
My aim of the Eagle files is to make an as simple to build, cheap and light tracker as possible, a fully assambled board should weigh in on about 1 - 1.3gram,
a fully assambled board with solar cells and antenna about 3.5gram

Im using 6 of the smallest avalible (19x39mm) solar cells in series to power the board, it makes it run from and to 15-19° solar angle depending on Gps used

After more then 25 launches over the years and probably more then 10 pcb revisions I have come to this final? design, the intention of this page is to ease the building and configuring the OM3BC APRS / RTTY / CW tracker.

The rar file below contains all files mentioned in this small writeup

There are two different firmware versions depending on what Gps module you intend to use:

fw7.5 should be used with Ublox Max modules, I have so far only tested the Max7q and Max7c both working well,
the low voltage "c" version getting a bit longer "runtime" due to its lower voltage demands, Max 6 & 8 should work just as well.

fw14 should be used with ATGM336 Gps which is a "new" cheap module that can be found for around $3 on Aliexpress,
there is no flightmode that needs to be set on this module, it have been tested to over 32000m at the time of this write up.

You will also find Eagle pcb files in the rar for two types of PIC ic footprints.

I have tested both the L version and LF version of the PIC but could not see any advantages using the low voltage (LF) version of the ic

All versions of the si4x6x I have tried have worked well, so far I have tested SI4060, 4463 and 4063.

THE MOST important setting to get reliable startup of the board is to enable the Watch Dog Timer (WDT) you set all as 1:s as in the below picture.
To do this you press the "Configuration:" in the PICkit3 before you program the board.
![!!1 9V Bor wdt2min14s](https://user-images.githubusercontent.com/9722781/172041526-16f2c3bf-27b8-4b18-90c1-1a13f12fed36.jpg)
You can read about the fuses in the pic18f26k22.pdf (rar)

Schematic
![XS](https://user-images.githubusercontent.com/9722781/172041538-1f26c8e8-0b61-4fbd-bb52-eb9813ab6522.jpg)

Settings Im using:
MYC SA6BSS-9
DEVIATION 425
POUT 8 (pout 100 using 4060 // pout 8 = 25mW on a 4x63)
APRS on
HOLD 2
TAIL on 2
INTEMP yes REF 19199985
UBLOX on (=atgm336)
TTEXT RTTY 434.5/100b7n2 Temp:\W Gps:\B
UNPROTO APRS V wide0-0 // = to not use digipeaters, leave unchanged if you want to use digipeaters
RFRQ 434500000 // putting the rtty up in ism band

Im using Termite terminal to setup the board, this as well as well as the PICkit3 is in the rar, termite also supports macros so you dont have to enter every setting everytime you setup a new board.

When you configure the board you have to use a rs232 programmer, the only one so far that works reliably is this type, look for it on ebay or aliexpress,
should cost arround 3-5$, note the DC jack, electrolytic caps and LEDs
The voltage out from this is 5V, to reduce this you can put 2 diods in series on the VCC to lower the voltage to more reasonable levels, or preferably a 3.3V LDO.

![s-l1600](https://user-images.githubusercontent.com/9722781/172041557-9f7765cf-b990-4f4b-91af-dc7aa672cd56.jpg)

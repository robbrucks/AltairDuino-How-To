# Basics of How to use the Altair Duino

**Note:** This document assumes you have already successfully connected using some type of serial terminal.

The Altair Duino comes with many built-in programs.

The included programs are stored in the following areas on the AltairDuino:
  * Built-in ROM: Not true ROM, but rather programs that have been hard-coded inside the Arduino code
    * Binary Programs: these start running immediately after loading
    * BASIC Programs: these require a version of BASIC to be loaded and running before they are loaded

## Processor Hard-Reset
After you have powered on the Altair, your first step should be to hard-reset the system. This is 
because the processor starts up in a random state. The hard reset sets the program counter to zero
and sets processor settings to an initialized state.
* The following procedure performs a hard-reset on the system

       Hold the STOP switch up and press the RESET switch up

* **You should always perform a hard reset immediately after powering on the Altair**

## Built-in Binary programs
A sample set of binary programs has been pre-installed on the Arduino for running on the Altair.
Some of these programs use the LEDs and switches on the Altair front panel as the user interface while some
require a serial terminal as a user interface. 

### Print the list of built-in Binary programs
* This procedure prints the list of built-in binary programs you can run that are already installed in ROM.

       Hold the STOP switch up and press the RESET switch up
       Set switches A15 thru A0 to down
       Press the AUX1 (the left one) down

* This prints the following menu:

       00000000) [print this directory]
       00000001) Calculator
       00000010) Kill-the-Bit
       00000011) Pong (LEDs)
       00000100) Pong (Terminal)
       00000101) 4k Basic
       00000110) 16k ROM Basic
       00000111) MITS Programming System II
       00001000) Disk boot ROM
       00001001) ALTAIR Turnkey Monitor
       00001010) Music ('Daisy')
       00001011) CPU Diagnostic
       00001100) CPU Exerciser
       00001101) Music system
       00001110) Hard disk boot ROM
       00001111) Multi-boot loader ROM
       01xxxxxx) [Read Intel HEX data from primary host interface]
       10nnnnnn) [load memory page, nnnnnn=file number]
       11nnnnnn) [save memory page, nnnnnn=file number]

### Run a built-in ROM-Based Binary programs

       Hold the STOP switch up and press the RESET switch up
       Set switches A15 thru A8 down
       Set switches A7 thru A0 to correspond to binary program number above (0=down, 1=up)
       Press AUX1 down

## List the built-in ROM-Based BASIC Programs

       Hold STOP and press RESET up
       Set switches A15 thru A8 off (down)
       Set switches A7 thru A0 to `00 000 110`
       Press AUX1 down
       Press `ENTER` at the `MEMORY SIZE?` prompt
       Type the letter `O` (for an Okidata printer) and press `ENTER` at the `LINEPRINTER?` prompt
       Set switches A15 to A0 off (down)
       Press AUX2 down

* This prints a list of available ROM-Based BASIC Programs 

      0  "00000001) [this directory]"
      1  "00000001) 23-match"
      2  "00000010) amazing"
      3  "00000011) baccarat"
      4  "00000100) baseball"
      5  "00000101) basketbl"
      6  "00000110) battle"
      7  "00000111) birthday"
      8  "00001000) blackjack"
      9  "00001001) bombard"
      10 "00001010) budget"
      11 "00001011) chase"
      12 "00001100) checkers"
      13 "00001101) chess"
      14 "00001110) climates"
      15 "00001111) cloud-9"
      16 "00010000) craps"
      17 "00010001) crazy-8"
      18 "00010010) cube"
      19 "00010011) evenwin"
      20 "00010100) flipflop"
      21 "00010101) football"
      22 "00010110) galaxy"
      23 "00010111) hamurabi"
      24 "00011000) hangman"
      25 "00011001) histogram"
      26 "00011010) isprime"
      27 "00011011) king"
      28 "00011100) lander"
      29 "00011101) life"
      30 "00011110) mastermind"
      31 "00011111) orbit"
      32 "00100000) pizza"
      33 "00100001) poker"
      34 "00100010) power"
      35 "00100011) powers"
      36 "00100100) qubic"
      37 "00100101) rock-paper-scissors"
      38 "00100110) rose"
      39 "00100111) seawar"
      40 "00101000) sieve"
      41 "00101001) sin"
      42 "00101010) square"
      43 "00101011) swarms"
      44 "00101100) tic-tac-toe"
      45 "00101101) towers"
      46 "00101110) word-puzzle"
      47 "00101111) wumpus"

* When you execute this while Basic is running, the list is read in by the Basic interpreter as a program.  You will need to clear the program memory by issuing a `NEW` command to Basic. This tells it that you are starting a new program and to clear the program memory.

## Run a built-in ROM-Based BASIC Program
**NOTE:** Some BASIC programs will not run in 4k Basic due to their size, but all should be able to run in 16k ROM Basic. So this example uses 16k ROM Basic.
* Load the 16k ROM Basic Binary Program

      Hold STOP and press RESET up
      Set switches A15 thru A8 off (down)
      Set switches A7 thru A0 to `00 000 110`  (the code for 16k Basic)
      Press AUX1 down
      Press `ENTER` at the `MEMORY SIZE?` prompt
      Type the letter `O` and press `ENTER` at the `LINEPRINTER?` prompt

* List the BASIC Programs available in ROM
      Set switches A15 to A0 off (down)
      Press AUX2 down to list the programs

**NOTE:** The program list is read in by BASIC as a program. You will need to delete this program from memory before loading another program by executing the `NEW` command in BASIC, otherwise they will be merged together and will not work properly.

* Load a BASIC Program (For this example I chose "Wumpus")

      Type `NEW` and press `ENTER` to clear the progrm memory
      Leave switches A15 thru A8 off (down)
      Set switches A7 thru A0 to the binary number for the program, in this case `00 101 111`  (the code for Wumpus)
      Press AUX2 down to load the program into memory; you will see the program typed into Basic on your terminal screen
      Type `RUN` and press `ENTER` to run Wumpus
       
## Virtual disk files on the SD card
* You can mount virtual disk drive files stored on the SD card, boot from them, and even create new ones.
* Unmounting a drive is optional, when you mount the drive with a new disk file any currently mounted disk file is automatically unmounted first.

### Floppy drives
* Setting switches A15 thru A12 to 0001 tell Altair that you want to manipulate floppy drives

#### Listing virtual floppy disk files on the SD card
* Set switches A15 thru A0 down
* Set switch A12 up
* Press AUX2 down

The following list will be displayed on the terminal

    ---------------------------------------------
    Available disks images:
    ---------------------------------------------
    00 000 001) DISK01.DSK: CP/M (63k)
    00 000 010) DISK02.DSK: ALTAIR DOS 1.0
    00 000 011) DISK03.DSK: ALTAIR Disk Basic
    00 000 100) DISK04.DSK: ALTAIR Disk Basic programs
    00 000 101) DISK05.DSK: Games (CP/M programs)
    00 000 110) DISK06.DSK: SuperCalc II (CP/M program)
    00 000 111) DISK07.DSK: WordStar (CP/M program)
    00 001 000) DISK08.DSK: Zork I & II (CP/M games)
    00 001 001) DISK09.DSK: Time Sharing Basic V1.1
    00 001 010) DISK0A.DSK: Time Sharing Basic V2
    00 001 011) DISK0B.DSK: Time Sharing Basic V2 programs
    00 001 100) DISK0C.DSK: Altair Mini-Disk Basic
    00 001 101) DISK0D.DSK: Altair Mini-Disk Basic programs
    00 001 110) DISK0E.DSK: Altair Mini-Disk DOS
    00 001 111) DISK0F.DSK: Altair Mini-Disk DOS programs
    00 010 000) DISK10.DSK: Hitchhikers Guide to the Galaxy
    00 010 001) DISK11.DSK: Planetfall
    00 010 010) DISK12.DSK: Colossal Cave Adventure
    00 010 011) DISK13.DSK: CP/M 2.2b (modern version)
    00 010 100) DISK14.DSK: ALTAIR Mini-Disk DOS Fortran
                          (not bootable - mount in drive 1)
    00 010 101) DISK15.DSK: Zork III (CP/M game)
    ---------------------------------------------
    These images were put together by Mike Douglas.
    See README.TXT for more information.

#### Mounting floppy drives
The switches A15 thru A0 are used as follows when mounting or unmounting a floppy disk image:
* A15 thru A12 are set to 0001 to designate that a **floppy drive** image is to be mounted or unmounted
* A11 thru A8 are set to the 4 bit number representing virtual floppy drives 0 thru 15 (Drive letters "A:" thru "P:")
* A7 thru A0 are set to the 8 bit number representing the floppy image to mount
  * The 8-bit disk number corresponds to the hex xx in the DISKxx.DSK files on the SD card.
  * For example, setting 00001010 selects floppy disk image "DISK0A.DSK" (00001010 in binary equals 0A in hex)
* Press the AUX2 switch down
* A message similar to this is displayed on the terminal:

      [mounted disk image 'DISK0A.DSK: Time Sharing Basic V2' in drive 0]

#### **UN**Mounting floppy drives
The switches A15 thru A0 are used as follows when mounting or unmounting a floppy disk image:
* A15 thru A12 are set to 0001 to designate that a **floppy drive** image is to be mounted or unmounted
* A11 thru A8 are set to the 4 bit number representing virtual floppy drives 0 thru 15 (Drive letters "A:" thru "P:")
* A7 thru A0 are ignored
* Press the AUX2 switch **UP**
* A message similar to this is displayed on the terminal:

      [unmounted drive 0]

#### Booting from a mounted floppy
* Altair will only boot from the floppy mounted on virtual floppy drive 0 (drive letter "A:")
* Mount the bootable floppy in drive 0 (see above)
* Use the following switch settings to boot from floppy
  * Switches A15 thru A8 are ignored
  * Set switches A7 thru A0 down
  * Set switch A3 up
  * Press switch AUX1 down

### Hard Drives
* Setting switches A15 thru A12 to 0011 tell Altair that you want to manipulate hard drives

#### Listing virtual hard disk files on the SD card
* Set switches A15 thru A0 down
* Set switches A13 and A12 up
* Press AUX2 down

The following list will be displayed on the terminal

    ---------------------------------------------

    Available hard disk images:
    ---------------------------------------------
    0001) HDSK01.DSK: Altair Hard Disk BASIC
    0010) HDSK02.DSK: Altair Accounting System
    0011) HDSK03.DSK: Mike Douglas' 88-HDSK CP/M

    ---------------------------------------------

    These images were put together by Mike Douglas.

    See README.TXT for more information.

#### Mounting hard drives
You can mount up to four hard drive images as "**platters**" on disk unit 1 (the only unit available)
The switches A15 thru A0 are used as follows when mounting a hard disk image:
* A15 thru A12 are set to 0011 to designate that a **hard drive** image is to be mounted or unmounted
* A11 and A10 are set to 00 (selects hard disk unit 1)
* A9 and A8 are set to the 2 bit number representing the desired disk platter (0 thru 3)
* A7 thru A0 are set to the 8 bit number representing the hard disk image to mount
  * The 8-bit disk number corresponds to the hex xx in the HDSKxx.DSK files on the SD card.
  * For example, setting 00000010 will load hard disk image "HDSK02.DSK" (00000010 in binary equals 02 in hex)
* Press the AUX2 switch down
* A message similar to this is displayed on the terminal:

      [mounted hard disk image 'HDSK02.DSK: Altair Accounting System' in platter 0 of unit 1]

#### **UN**Mounting hard drives
The switches A15 thru A0 are used as follows when unmounting a hard disk image:
* A15 thru A12 are set to 0011 to designate that a **hard drive** image is to be mounted or unmounted
* A11 and A10 are set to 00 (selects hard disk unit 1)
* A9 and A8 are set to the 2 bit number representing the desired disk platter (0 thru 3)
* A7 thru A0 are ignored
* Press the AUX2 switch **UP**
* A message similar to this is displayed on the terminal:

      [unmounted platter 0 of unit 1]

#### Booting from a mounted hard drive
* Altair will only boot from the hard drive mounted on platter 0 of unit 1 (drive letter "A:")
* Mount the bootable floppy in drive 0 (see above)
* Use the following switch settings to boot from floppy
  * Set switches A15 thru A8 down
  * Set switches A7 thru A0 to 00001110
  * Press switch AUX1 down


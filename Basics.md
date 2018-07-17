# Basics of How to use the Altair Duino

**Note:** This document assumes you have already successfully connected using some type of serial terminal.

The Altair Duino comes with a number of built-in programs.
* Binary Programs: these start running immediately after loading
* BASIC Programs: these require a version of BASIC to be loaded and running before they can be loaded

## Processor Hard-Reset
After you have powered on the Altair, your first step should be to hard-reset the system. This is 
because the processor starts up in a random state. The hard reset sets the program counter to zero
and sets processor settings to an initialized state.
* The following procedure performs a hard-reset on the system

       Hold the STOP switch up and press the RESET switch up, then release

* **You should always perform a hard reset immediately after powering on the Altair**

## Built-in Binary programs
A sample set of binary programs has been pre-installed on the Arduino for running on the Altair.
Some of these programs use the LEDs and switches on the Altair front panel as the user interface, while most
require a serial terminal as a user interface. 

### Print the list of built-in Binary programs
* This procedure prints the list of built-in binary programs you can run that are already installed in ROM.

       Hold the STOP switch up and press the RESET switch up
       Set switches A15 thru A0 to down
       Press the AUX1 (the left one) down

* This will print the following menu:

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

* The zeros and ones represent the binary code to set on switches A7 through A0 to select the program to load and run.
* The "Calculator", "Kill-the-Bit", and "Pong (LEDs)" programs use the front display panel as the interface, the rest require using a serial terminal interface.
* The last three programs listed are special-use programs for reading hex data into memory, and to save memory to a file, or to load memory from a file.

### Run a built-in ROM-Based Binary program

      Hold the STOP switch up and press the RESET switch up
      Set switches A15 thru A8 to zero (down)
      Set switches A7 thru A0 to correspond to binary program number listed above (0=down, 1=up)
      Press AUX1 down (the left AUX switch)

## Built-in BASIC Programs
* Only a handful of the included programs will run under 4k Basic, most require 16k Basic to be used.
* A BASIC interpreter is required to be loaded and running before these programs can be loaded.

### List the built-in ROM-Based BASIC Programs
* Load the 16k ROM Basic Binary Program

       Hold the STOP switch up and press the RESET switch up
       Set switches A15 thru A8 to zero (down)
       Set switches A7 thru A0 to `00 000 110`
       Press AUX1 down
       Press `ENTER` at the `MEMORY SIZE?` prompt
       Type the letter `O` (for an Okidata printer) and press `ENTER` at the `LINEPRINTER?` prompt
       You are now running 16k Basic

* List the BASIC Programs available in ROM

       Set switches A15 to A0 to zero (down)
       Press AUX2 down to list the available programs

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


### Run a built-in ROM-Based BASIC Program
**NOTE:** Some BASIC programs will not run in 4k Basic due to their size, but all should be able to run in 16k ROM Basic. So this example uses 16k ROM Basic.
**NOTE:** When you display the program list while Basic is running, **the list will be read in by the Basic interpreter as a program**.  You will need to clear the program memory by issuing a `NEW` command to Basic. This tells it that you are starting a new program and to clear the program memory.

* Load a BASIC Program (For this example I chose "Wumpus")

      Type `NEW` and press `ENTER` to clear the progrm memory
      Set switches A15 thru A8 to zero (down)
      Set switches A7 thru A0 to the binary number for the program, in this example `00 101 111` for Wumpus
      Press AUX2 down to load the program into memory; you will see the program typed into Basic on your terminal screen
      Type `RUN` and press `ENTER` to run Wumpus
       

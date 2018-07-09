# Altair Duino How-To

**Note:** This document assumes you have successfully connected a serial terminal.

## Hard Processor Reset

       Hold STOP and press RESET up

## Print Menu of Builtin ROM-Based Programs

       Hold STOP and press RESET up
       Set A15 thru A0 down
       Press AUX1 down

* Prints the following menu:

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

## Run a Builtin ROM-Based Program

       Hold STOP and press RESET up
       Set switches A15 thru A8 off (down)
       Set switches A7 thru A0 to correspond to program number
       Press AUX1 down

## List Builtin ROM-Based BASIC Programs
* Some Basic programs will not run in 4k Basic due to their size, but all will run in 16k ROM Basic. So this example uses 16k ROM Basic.

       Hold STOP and press RESET up
       Set switches A15 thru A8 off (down)
       Set switches A7 thru A0 to `00 000 110`
       Press AUX1 down
       Press `ENTER` at the `MEMORY SIZE?` prompt
       Type the letter `O` and press `ENTER` at the `LINEPRINTER?` prompt
       Set switches A15 to A0 off (down)
       Press AUX2 down

* Prints this list of available ROM-Based BASIC Programs 

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

## Run a Builtin ROM-Based BASIC Program
* Some Basic programs will not run in 4k Basic due to their size, but all will run in 16k ROM Basic. So this example uses 16k ROM Basic.

       Hold STOP and press RESET up
       Set switches A15 thru A8 off (down)
       Set switches A7 thru A0 to `00 000 110`
       Press AUX1 down
       Press `ENTER` at the `MEMORY SIZE?` prompt
       Type the letter `O` and press `ENTER` at the `LINEPRINTER?` prompt
       Set switches A15 to A0 off (down)
       Press AUX2 down to list the programs

**NOTE:** The list is read in by BASIC as a program. You need to delete it before loading another program by executing the `NEW` command, otherwise they will be merged together.

* This example is loading and running "Wumpus":

       Type `NEW` and press `ENTER` to clear memory
       Leave switches A15 thru A8 off (down)
       Set switches A7 thru A0 to `00 101 111`
       Press AUX2 down to load the program
       Type `RUN` and press `ENTER` to run Wumpus
       


# Floppy Drives on the Altair
* There are many floppy drive images included on the SD card for the AltairDuino.
* Due to the method of referencing of files on the SD card, there is a limit of 255 floppy drive images on the SD card.

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


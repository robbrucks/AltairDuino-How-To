# Floppy Drives on the Altair
* There are many floppy images included on the SD card for the AltairDuino.
* The Altair is configured to emulate 4 floppy drives, 0 to 3, but you can modify the Arduino software to emulate up to 16 floopy drives.
* For most disk operating systems on the Altair, you reference the floppy drives as follows in the OS:
  * Drive 0 is "A:"
  * Drive 1 is "B:"
  * Drive 2 is "C:"
  * Drive 3 is "D:"
* You can mount virtual disk drive files stored on the SD card, boot from them, and even create new ones.

## Virtual disk files on the SD card
* Floppy image files on the SD card are named "DISKxx.DSK", where "xx" is a HEX number between 01 and FF (00 is reserved).
* Due to the method used to name floppy image files on the SD card, there is a limit of 255 floppy drive images on the SD card.
* You can create a new image by referencing a non-existent image file. The emulator will create the floppy image file as soon as it writes to it.
* Attempting to mount disk 00 causes the contents of DISKDIR.TXT to be listed to the serial terminal.
* You can mount the same disk image to multiple drives, although this may cause confusion for the OS.
* Unmounting an image before mounting a different one is optional. When you mount the drive with a new image file any currently mounted image
file is automatically unmounted first.

## Manipulating Floppy drives
* Setting switches A15 thru A12 to 0001 instruct Altair that you wish to mount or unmount floppy drives
* Switches A11 thru A8 are used to select the floppy drive unit for mounting or unmounting
  * 0000 = Drive 0 (A:)
  * 0001 = Drive 1 (B:)
  * 0010 = Drive 2 (C:)
  * 0011 = Drive 3 (D:)
* Switches A7 thru A0 are used to select the floppy image to mount (ignored for unmounting)
* Pressing the **AUX2 switch DOWN mounts** the selected image onto the specified drive unit
* Pressing the **AUX2 switch UP unmounts** any mounted image from the specified drive unit

## Listing virtual floppy disk files on the SD card
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

## Mounting images on floppy drives
The switches A15 thru A0 are used as follows when mounting or unmounting a floppy disk image:
* A15 thru A12 are set to 0001 to designate that a **floppy drive** image is to be mounted or unmounted
* A11 thru A8 are set to the 4 bit number representing virtual floppy drives 0 thru 15 (Drive letters "A:" thru "P:")
* A7 thru A0 are set to the 8 bit number representing the floppy image to mount
  * The 8-bit disk number corresponds to the hex xx in the DISKxx.DSK files on the SD card.
  * For example, setting 00001010 selects floppy disk image "DISK0A.DSK" (00001010 in binary equals 0A in hex)
* Press the AUX2 switch down
* A message similar to this is displayed on the terminal:

      [mounted disk image 'DISK0A.DSK: Time Sharing Basic V2' in drive 0]

## **UN**Mounting images from floppy drives
The switches A15 thru A0 are used as follows when mounting or unmounting a floppy disk image:
* A15 thru A12 are set to 0001 to designate that a **floppy drive** image is to be mounted or unmounted
* A11 thru A8 are set to the 4 bit number representing virtual floppy drives 0 thru 15 (Drive letters "A:" thru "P:")
* A7 thru A0 are ignored
* Press the AUX2 switch **UP**
* A message similar to this is displayed on the terminal:

      [unmounted drive 0]

## Booting from a mounted floppy
* Altair will only boot from the floppy mounted on virtual floppy drive 0 (drive letter "A:")
* Mount the bootable floppy in drive 0 (see above)
* Be sure to set switches A15 thru A12 to down before booting
* Use the following switch settings to boot from floppy
  * Switches A15 thru A1 set to 0 (down)
  * Set switch A3 up (sets the Disk Boot ROM)
  * Press switch AUX1 down


# Apple II Crypto

A very basic program to encrpt/decrypt any file, using a secret phrase EORed with the file to encrpt/decrypt.
It is written in assembly language only (Merlin). It uses MLI ProDOS calls for disk access.
Applesoft is not required.

## Features

* Works with ProDOS 8 (not tested on GS)
* User can change PREFIX
* User can encrpt or decrypt any file
* The program adapts itself to 40 ou 80 col. mode.

The last feature was intersting to realise. The non obvious thing (for me) is that the character sets (normal and atl), does not behave wether you are in 40 ou 80 column mode.

Note : if file A is encrypted to file B, and file B is encrypted to file C, then file A = file C, because of EOR.

Encrypt adds ".K" at the end of file name.
Decrypt adds ".D" at the end of file name.

## Requirements to compile and run

Here is my configuration:

* Visual Studio Code with 2 extensions :

-> [Merlin32 : 6502 code hightliting](marketplace.visualstudio.com/items?itemName=olivier-guinart.merlin32)

-> [Code-runner :  running batch file with right-clic.](marketplace.visualstudio.com/items?itemName=formulahendry.code-runner)

* [Merlin32 cross compiler](brutaldeluxe.fr/products/crossdevtools/merlin)

* [Applewin : pple IIe emulator](github.com/AppleWin/AppleWin)

* [Applecommander ; disk image utility](applecommander.sourceforge.net)

* [Ciderpress ; disk image utility](a2ciderpress.com)

Note :
DoMerlin.bat puts all things together. It needs a path to Merlin32 directory, to Applewin, and to Applecommander.
DoMerlin.bat is to be placed in project directory.
It compile source (*.s) with Merlin32, copy 6502 binary to a disk image (containg ProDOS), and launch Applewin with this disk in S1,D1.

k80A2.s is ready to be compiled on a genuine Apple II, with Merlin 8.
It can be imported in a disk image using Ciderpress, then used on an Apple II (c in my case).
I use Floppy emu [www.bigmessowires.com/floppy-emu] wich is really great, congratulation to Big Mess O'Wire !!!!

## Todo

File name length should be verified. This can be imporant since encrypting adds ".K" (or ".D" when decrypting) to the file name (so length = length +2).

Lower part of screen should be limited in a window, to avoid the all screen scrolling.

Port to Mouse Graphics Toolkit, for a fancier look, and more functions.

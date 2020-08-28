# RC2014
<p>MODEM utility for CP/M on RC2014</p>
<p><b>Installing MODEM</b></p>
<ol>
<li>Clock 1 should be set to 3.6864 MHz. This is to ensure that the timing loops in the provided MODEM program result in the proper delay times. This setting also results in a console BAUD rate of 57.6 K Baud. Clock 2 should be set to 0.3072 MHz for a BAUD rate of 4800.</li>
<li>Set jumpers on the VT132 card (if used) to disconnect the port B serial lines from the backplane so that it can be serviced by a Windows computer with an FTDI cable. If not using the VT132, simply configure the B port terminal or program for 4800 BAUD.</li>
<li>Download the MODEM.ASM file to your Windows PC and open it in Notepad.</li>
<li>Do not insert the VT132 board into the backplane at this time. Connect the FTDI cable to port A on the serial card (observe correct pin alignment) and configure Teraterm for 57600 BAUD with a 1ms delay on characters and a 100 ms delay on lines. If you're unfamiliar with Teraterm, you need to connect the FTDI cable between the RC2014 and your PC's USB port first (black wire goes to the Ground pin on Port A. Make sure the cable driver gets installed and observe the COM port number). Start Teraterm and you should be presented with a connection dialog. Select the lower radio button and pick the COM port from the list. Next, select the Setup, Serial port menu options and set the BAUD rate and any delays before clicking OK.</li>
<li>Switch on the RC2014 and you should observe the "Press [SPACE] to activate console" message. Check BAUD rate setting if not.</li>
<li>Press the CAPS LOCK key on the keyboard and then, with focus on Teraterm, press space followed by "X" followed by "Y" to boot CP/M</li>
<li>You should now be at the CP/M "A>" prompt. Type "C:ED MODEM.ASM" (don't include the quotation marks) and return.</li>
<li>You should now have the ED "*" prompt. Press "I" and return.</li>
<li>You should now have a line number 1 prompt. Highlight the contents of the Notepad window and press CTRL-C to copy to the clipboard. On Teraterm, select the Edit, Paste menu options (do not use CTRL-V). You should now have a small dialog box showing the first few lines of the MODEM.ASM file.</li>
<li>Click OK. You should now see the MODEM.ASM file begin to type into the ED session. When typing stops, you should see line number 562 if everything transferred successfully.</li>
<li>Press CTRL-Z. You should now be back at the ED "*" prompt.</li>
<li>Press "E" and return. You should be back at the CP/M "A>" prompt.</li>
<li>Type "C:ASM MODEM". Do not include the ".ASM" portion of the file name.</li>
<li>Assembly should complete with no errors. If errors occur, re-check your system and connections to ensure communication is not dropping characters or picking up noise. Repeat the procedure if necessary to get a clean assembly.</li>
<li>Type "C:LOAD MODEM". You should now have MODEM.COM in your A: directory. You can now erase the .BAK, .PRN and .HEX files to save space.</li>
</ol>
<p>At this point, you can shut down the RC2014 and prepare for the next phase of the operation:</p>
<p><b>Transferring Files</b></p>
<ol>
<li>Move the FTDI cable from port A to port B observing correct pin alignment.</li>
<li>Insert the VT132 card into the RC2014 backplane. If not using the VT132, connect a second FTDI cable to Port A and the computer running the console terminal program.</li>
<li>Configure the VT132, or the terminal on port A, to 57600 BAUD with no delays. Configure Teraterm on port B to 4800 baud with no delays. Port A is now the Console port and B is the MODEM port.</li>
<li>Download the desired .COM CP/M program file to your PC. Let's assume for example you wish to add MBASIC.COM to your A: drive. Download MBASIC.COM from one of the repository websites and make note of its location.</li>
<li>Switch on the RC2014 and boot CP/M as before using the VT132 or console terminal.</li>
<li>On the Teraterm menu, select File, Transfer, XMODEM, Send. Select the MBASIC.COM file but do not click OK.</li>
<li>On the console, type "MODEM R MBASIC.COM" but don't press return.</li>
<li>Click OK on the Teraterm dialog and then press return on the console.</li>
<li>After a moment you will see a TIMEOUT message and then file transfer should begin with a count of sectors. The process will end with the TRANSFER COMPLETE message.</li>
<li>You should now have MBASIC.COM on your A: drive.</li>
</ol>
<p>This process can also be used in reverse to move files from CP/M to your PC. Just enter "MODEM S [filename.typ]" on the console and select File, Transfer, XMODEM, Receive on Teraterm. Press return on the console first, then click OK on Teraterm. Always start the sending program first, then the receiver.</p>

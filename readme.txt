******************************************************************************
**********************CSE522-Real Time Embedded Systems**********************
*****************************Assignment-2***************************************


Name - Raunak
ASU ID - 1217240245

Description : 

In this assignment, we have developed a device driver which measures distances using the hcsr04 sensor and stores them in the buffer, we are taking measurement based on the number of devices selected and displaying the measurement values with the help of the zephyr shell command.



******************************************************************************
*******************Steps to compile and execute the code*********************



1. Copy the  RTES-Raunak_02.zip file in the zephyr/samples directory.

2. Unzip the RTES-Raunak_02.zip in the zephyr/samples directory.

3. apply the patch hcsr04.patch to the zephyr source directory using,

	patch -p1 -i hcsr04.patch

4. start the terminal go to zephyr folder and set the environment by the following commands,

	(i)   source zephyr-env.sh
	(ii)  export ZEPHYR_TOOLCHAIN_VARIANT=zephyr
	(iii) export ZEPHYR_SDK_INSTALL_DIR=Zephyr SDK installation directory
	
5. Go to zephyr/samples/HCSR_app folder

6. Create a folder named build using mkdir build command.

7. Go inside the folder build using cd build command.

8. Set the cmake environment using the following command,

	cmake -DBOARD=galileo ..
	
9. Then type the following command to make the binary,

	make
	
10. Now from the zephyr directory created inside build copy the zephyr.strip file to the kernel folder of SD card.

11. Now, assuming you sd card is prepared with bootia32.efi file and config file. Insert your sd card to the galileo board.

12. Now boot from SD card and load the zephyr kernel.

13. Now connect the ftdi cable and do chmod 777 tty/USB0.

14. start putty, set serial communication to 115200 and tty/USB0 and load.

15. Load the zephyr kernel, led with full brightness will be on.

16. To slect the number of devices type the folllowing command,

	HCSR select n,  where n=1 means HCSR0, n=2 means HCSR1 and n=3 means HCSR0 and HCSR1.
	
17. To start the measurement and store in the bufffer type the following command,

	HCSR start n, where n is the number of samples
	
18. To observe the buffer values type the following command,

	HCSR dump n1 n2,  where n1 and n2 represents the range of buffer values for which we want the measurement.
	
19. To clear the buffer type the following command,

	HCSR clear
	
	
*******************************************************************************
******************************Sample Output**********************************



uart:~$ HCSR select 3
uart:~$ HCSR start 8
uart:~$ HCSR dump 1 7
Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 24222372

Device: HCSR1, Distance: 143, Timestamp(Elapsed Time) in us: 24230756

Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 24771097

Device: HCSR1, Distance: 143, Timestamp(Elapsed Time) in us: 24779502

Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 25319825

Device: HCSR1, Distance: 144, Timestamp(Elapsed Time) in us: 25328269

Device: HCSR0, Distance: 340, Timestamp(Elapsed Time) in us: 25868604

Device: HCSR1, Distance: 158, Timestamp(Elapsed Time) in us: 25877832

Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 26417301

Device: HCSR1, Distance: 139, Timestamp(Elapsed Time) in us: 26425465

Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 26966005

Device: HCSR1, Distance: 176, Timestamp(Elapsed Time) in us: 26976327

Device: HCSR0, Distance: 339, Timestamp(Elapsed Time) in us: 27524732

Device: HCSR1, Distance: 141, Timestamp(Elapsed Time) in us: 27532980

uart:~$ HCSR clear
uart:~$ HCSR dump 1 7
Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR0, Distance: 0, Timestamp(Elapsed Time) in us: 0

Device: HCSR1, Distance: 0, Timestamp(Elapsed Time) in us: 0



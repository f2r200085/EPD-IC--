AIO (All In One)
================

Install
-------

1.  If you `first use` AIO, please key in below command.
    
    1.   `make install`
    
2.  Please check you have `init.uc` and `LUT.uc`, if you no have this two file, AIO can’t initiation it.
    
3.  Please put the picture file in the picture folder. (the picture file must be a \*.bmp file)
    
4.  If you want to know Raspberry Pi GPIO pin define, please ley in below command.
    
    1.   `make pin`
    
5.  Create AIO execution file, please key in below command.
    
    1.   `make`
    

GPIO PIN Setting
----------
1. All GPIO pins depend on the `config.ini` file. Please set and check if the pin settings are correct when you use it for the first time.
2. Brief introduction to ini files.
	1. Keys (properties): The basic element contained in an INI file is the key or property.
			name=value
	2. Sections: Keys may, but need not, be grouped into arbitrarily named sections. 
			[section]
			a=a
			b=b
	3. Comments: Semicolons (;) at the beginning of the line indicate a comment. Comment lines are ignored.
			; comment text
3. If you want to see the raspberry pi GPIO pin assignment.
	1. Enter the following command.
			make pin

AIO Method
----------

- In the AIO, it have fourteen mode and twenty four opration method.
	-**Method**
	
		busy 		-- Check IC busy pin.
		vcom 		-- Measure vcom and setting VDCS.
		tsc 	 	-- Temperature Sensing.
		delay    	-- One millisecond(1mS) delay.
		init 		-- EPD initiation and reset IC.
		reg  		-- Change IC to register mode.
		otp  		-- Change IC to OTP mode
		drf  		-- Display image, kwr mode.
		pdrf 		-- Non TRES setting display image, kwr mode.
		lut	  	-- Loading LUT file.(SPI)
		file_init	-- TBD.
		vcion		-- GPIO.2(BCM.27) pin set output and value is HIGH.
		vcioff   	-- GPIO.2(BCM.27) pin set output and value is LOW.
		fst  		-- Flash CSB pin, value is LOW.
		fsp	  	-- Flash CSB pin, value is HIGH.
		pg	   	-- Flash page program.
		pf	   	-- Flash file program.
		fdrf 		-- Display image, 4bit mode.
		kwdrf		-- Display image, kw mode
		pkwdrf   	-- Non TRES setting display image, kw mode.
		i2_st		-- IIC start.
		i2_sp		-- IIC stop.
		i2_addw  	-- IIC address, write mode.
		i2_addr  	-- IIC address, read mode.
		tmJ		-- Return end symbol(Abbreviation for "toomuch Jhan")

	-**Mode**
	
		cmd	  	-- SPI Command mode
		dat  		-- SPI Data mode
		img	  	-- Image mode (For UC IC used.)
		get	  	-- SPI get mode
		fw	  	-- Write file to save.(SPI)
		fr	  	-- Read file input to the IC.(SPI)
		fwn	 	-- Write file to save but no index.(SPI)
		crc	 	-- Cyclic redundancy check.
		ftx	 	-- Flash mode, TX.(SPI)
		frx		 -- Flash mode, RX.(SPI)
		ffw	 	-- Flash mode, read file input to the flash.(SPI)
		ffwn		-- Flahs mode, Write file to save and no index.(SPI)
		i2_w		-- IIC write data.
		i2_r		-- IIC read data.
   
   
AIO Method
----------
- Explain how to use

	* 	Under the AIO(GUI)folder and execute the following command
		1. `sudo ./main " The command you want to operate  "`
		2. `sudo ./main " power on and power off " -> sudo ./main cmd 04 busy 02 buys`

    *   Power on and Power off
        1.   `cmd 04 busy 02 busy`

    *   Change to white border and Display image
        1.   `cmd 50 dat 57 cmd 04 busy 12 busy 02 busy`

    *   Setting image and display
        1.   `img "image name" drf`
		2. 	`"drf" can chage the pdrf, kwdrf, pkwdrf or fdrf`

    *   Measure vcom and setting VDCS.
        1.   `vcom`'
		2. `also you can change to the tsc, ..., etc.`

    *   Write OTP data 2048
        1.   `cmd a2 fw 2048`
        2.   `"2048" You can change the number of reads`
		3.	 `"fw" can chage to the non index file format -> fwn`
    
	*   Read AIO script file
        1.   `cmd fr "file name"`

    *   I2C Basic format write data
		1.	 `Start + Address|Write + "Index + Data" + Stop`
        2.   `i2_st i2_addw i2_w "Multiple data like: 00 01 02" i2_sp`
		
	*	I2C Basic format read data
		1. 	 `Start + Address|Read + "Index + Data" + Stop`
		2.	 `i2_st i2_addr i2_r 15 i2_sp`
		3. `"15" can change the number of reads`

    *   I2C Basic format write data
		1.	 `Start + Address|Write + "Index + Data" + Stop`
        2.   `i2_st i2_addw i2_w "Multiple data like: 00 01 02" i2_sp`

----------
Author: FuCheng.Jhan
Date: 2021/09/22

----------


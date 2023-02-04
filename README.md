**By using the information in this repo you agree to the following disclaimer:** The author of this information assumes no liability for damage or injury caused by using these instructions or any product created using methods or instructions herein. Building and using this controller requires technical knowledge and experience with electrical circuits and components. If you are unsure about any aspect of this project it is strongly recommended that you seek assistance from a knowledgeable individual or consult relevant resources before proceeding.

# 12 or 24 Channel PWM Dimming Controller for LED Power Supplies

This guide provides information to build a <a href="https://www.home-assistant.io/">Home Assistant</a> compatible light dimmer that will work with most <a href="https://led.meanwell.com/productSeries.aspx">Meanwell LED drivers (aka LED power supplies or ballasts)</a> using just a few electronic parts.  This should work with other manufacturer LED drivers which use 3-in-1 dimming and/or PWM dimming, so long as the driver provides source current on the dim circuit.  I think this can also be modified to work with 0-10v DC additive dimming by connecting a 10v power source to the signal board, but I haven't tried it.  Feel free to reach out to me if you have any questions about that.

## Background
The popularity of high powered DIY LED grow lights, as well as the relative market explosion of commercially available LED grow lights has resulted in an increase of high powered LED power supplies being used in homes and indoor gardens.  Most of these lights offer some form of dimming, many of them with thier own dimming knobs or option to connect a manufacturer specific dimming controller.  Just like with many other types of products, having your own easy-to-build and cost-effective option  that works with Home Assistant is a huge improvement in functionality, as you can set different lighting profiles for different stages of growth, and build automatic lighting rules based off things like room temperature, motion detection if a person is in the room and more..    



an alternative dimming control method that gives you the ability to adjust and control the brightness of all of your LEDs from an easy to use interface without breaking the bank.  This has created a opportunity for smart control systems to improve the functionality of these lighting systems. Lighting control systems currently available for high powered LED fixtures have any or all of the following drawbacks: do not allow for control of many fixtures without buying multiple control units, are expensive and/or are limited in function.  This project solves those issues by creating a cost effective controller with 12 or 24 separately controllable channels, each channel being able to control one or more LED fixtures/power suppllies.  

## Benefits
The most basic improvement seen by adding a completely customizable smart lighting control system such as this one would be allowing the remote brightness adjustment of many lights from a smartphone or PC.  More advanced uses include setting up smart rules to do things like reduce overall brightness of grow lights and shut off harmful UV LEDs when motion/contact sensor detects a person in the area, lowering light brightness to automatically compensate for high temperature spikes in the event of cooling system failures or inadequacies,  programming custom light spectrum profiles for grow lights with multiple color channels, sunrise/sunset emulation by ramping up and down light color/intensity and more.  Even though these examples highlighted uses in a indoor garden environment, it can be applied for decor and other lighting applications.

## Pre-requisites
- [Home Assistant](https://www.home-assistant.io/) server with [ESPHome](https://esphome.io/) installed
- LED power supply(s) (aka drivers or ballasts) that support **0-10v PWM** dimming such as MeanWell's line of high powered LED drivers.  If you arent sure if your LED driver supports **0-10v PWM** dimming, the best place(s) to check are the driver's datasheet, or if that isn't available, contact the manufacturer of your LED driver directly by phone or email and ask them "does my grow light / LED driver support 0-10v PWM dimming?".  Manufacturers are often quite helpful if you give them a chance.   **Ensure you are clear that you are looking for or asking about 0-10v PWM dimming, not 0-10v analog dimming.**  
- Ability to solder pin headers onto a printed circuit board.  
- Basic ability to work with wire strippers, pliers and glur guns.  
- Basic experience working with and connecting ESP32/ESP8266 devices to breakout boards.  

## Tools Required
Although having top-of-the-line tools makes the job easier, I mostly rely on economical options for my toolkit. While working with budget tools may not always be optimal, they are adequate for small and occasional projects and have served me well.  
- [Soldering iron](https://www.amazon.ca/s?k=Soldering+iron) ([brass wool](https://www.amazon.ca/s?k=brass+wool+soldering) recommended instead of using a wet solder sponge).  
- [Wire stripper](https://www.amazon.ca/s?k=wire+stripper)  
- [Multimeter](https://www.amazon.ca/s?k=Multimeter&rh=n%3A3006902011%2Cp_36%3A12035760011&dc&ds=v1%3AVJ07OZbfZbPTVCeOY0%2FOTVw2%2FDdTF6NoXoZ9MvBP20c&qid=1675112740&rnid=12035759011&ref=sr_nr_p_36_1) (for testing connections)  
- [Hot glue gun](https://www.amazon.ca/s?k=Hot+glue+gun) (for securing components in case)  

## Parts for the build
- [ESP32](https://www.google.com/search?q=ESP32+development+boards) or [ESP8266](https://www.google.com/search?q=ESP8266+development+boards) development board with [SPI pins](https://www.google.com/search?q=spi+pins)    
This is the brain of our controller setup. It has built-in Wi-Fi and can easily connect to your Home Assistant server using the ESPHome plugin. And the best part? You can use a cheap option like the [Wemos D1 Mini ESP8266](https://www.google.com/search?q=wemos+mini+d1) we will be using in this project.  
    <img src="/images/esp8266%20wemos%20d1%20mini.jpg" height="150">  

- [Adafruit TLC5947 **24-Channel** 12-bit PWM LED Driver](https://www.adafruit.com/product/1429)  
or [Adafruit TLC59711 **12-Channel** 16-bit PWM LED Driver](https://www.adafruit.com/product/3995)   
These boards are capable of generating some serious PWM signals, all the way up to 30V! The PWM voltage it generates is determined by the input voltage, which is why we're using a 10V power supply.  
    <img src="/images/Adafruit%2024%20channel%20PWM%20LED%20driver.jpg" height="150"> <img src="/images/Adafruit%2012%20channel%20PWM%20LED%20driver.jpg" height="150">  

- 2x [Break-Away 0.1" 2x20-pin Strip Dual Male Headers](https://www.google.com/search?q=Break-Away+0.1%22+2x20-pin+Strip+Dual+Male+Header) or 8 3x2 pin headers  
You will solder these terminal pin headers onto the PWM board. This is where the positive (+) and negative (-) DIM wire leads from your LED Driver will connect.  
    <img src="/images/Break-Away%200.1-inch%202x20-pin%20Strip%20Dual%20Male%20Header.jpg" height="150">  
    
- _terminal blocks_
- _project box_

# To be added:
## Assembly Instructions
## Software Configuration
## Usage

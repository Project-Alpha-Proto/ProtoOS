# ProtoOS
Protogen Operating System for Project Alpha Version 1 - only data files!

## A small introduction to how this repository is used:
This branch contains all the data files for starting your first Proto! It's a collection mainly for myself to organize my code and data on a central space where other people can watch my collection grow. 
Additionally I'd like everyone to get a starting point for their own project. So enjoy my stuff, but please don't redistribute it. This here contains hours over hours of work done by me and friends, so sharing is appreciated, but please be fair and keep it clean :)

## Working with the repo
### What you'll need for your Proto:
- a Raspberry Pi (3B tested)
- an SD Card (8+ GB) with Raspbian Desktop installed
- the [Adafruit RGB Matrix Bonnet](https://www.adafruit.com/product/3211) or the [Adafruit RGB Matrix HAT for Raspberry Pi](https://www.adafruit.com/product/2345)
- 2x 3mm (P3) 64x32px LED Matrix displays, for example [these ones](https://www.adafruit.com/product/2279)
- a power connector for your Raspberry Pi (usually not included)
- a 5V power supply for your Bonnet or HAT! This is not included and needs a 5,5mm/2,1mm barrel connector!
- the JtingF Protogen kit found [here](https://www.etsy.com/listing/1006039713/cm1-protogen-kit-no-electronics-slafdm), alternatively you can print your own, the files can be found [here](https://www.patreon.com/JtingF)
- a small screwdriver

### Preparing your Raspberry Pi
Before you can start showing stuff on your screen, you'll have to prepare your Raspberry Pi. Grab your Bonnet, align the pins like in the picture shown on the Adafruit website and push it very carefully onto your Raspberry Pi.

Now grab your display! You'll need to get your screwdriver ready too. Turn your RasPi like shown in the Picture on the Adafruit website. You'll now connect the display power cable: The red cable goes into the left hole of the connector and the black cable into the right hole. (Red means plus, Black means minus) Close the screws tightly! When you can hold your Raspberry Pi just with the two cables, it's tight enough. Now connect the other sides to the displays. It just goes in one way so you can't make anything wrong. Now do the same with the wide data connector. Just plug it in the Bonnet and the other sides into your displays, making a chain starting with the Bonnet, then the first display, then the second etc. Last but not least, make sure you have everything connected, like all the power supplies (you need both!), the HDMI cable and you have your SD card in your RasPi.
Awesome! You have everything done you need to do. Now let's start the coding!

### Setting up your Raspberry Pi
You'll now get a step by step explanation what you'll need to do software-wise. 
1. Boot your Raspberry Pi into desktop
2. Set up your Internet Connection on the RasPi
3. Open the Terminal
4. Make updates typing these commands one after another:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo rpi-update
reboot
```
This will check for updates and download everything needed and then reboot. After the reboot, open your Terminal again

5. Make a new directory for your stuff naming it Proto
6. Open your new directory in your file browser
7. Rightclick and select "Open Terminal here"
8. Type "git clone https://github.com/Project-Alpha-Proto/ProtoOS" and execute it
9. The complete software should now download to this directory including a directory named "ProtoOS" - thats the thing you need!
10. Make another directory for the LED library
11. Now do (7) and (8) again but instead clone the hzeller library found here: https://github.com/hzeller/rpi-rgb-led-matrix

## Testing your displays
We're ready to test your displays now. For that you need to go into the hzeller library files you just downloaded and open your terminal in /rpi-rgb-led-matrix.

You now have to compile the files first before you can actually execute them. That's because the code is in C which the Raspberry cannot natively run. Compiling the files can be done with

```
make -C examples-api-use
```

Now you just have to wait a litte bit and when the compiling is finished, you can go to your directory and start a test program with
```
cd examples-api-used
sudo ./minimal-example
```
When the displays show something now, they work and we can move to our next step:
### Actually using the displays right
You may have noticed, that your displays aren't showing what they should show. Thats because we didn't set them up correctly. We can use a few methods for that. The easiest one is giving extra parameters with "--(parameter name)".
First things first: There are a lot of parameters in the hzeller library. We only need to take a look at a few of them. The most interesting ones are --led-cols, --led-rows and --led-chain.
I'll explain what they do in a minute. But now lets actually do it the right way:

Exit your program by typing the combination Ctrl+C - like you would copy something on Windows.

Type the following in your Terminal window and execute it to see magic!
```
sudo ./minimal-example --led-cols=64 --led-rows=32 --led-chain=2
```
Bingo! You have now two functioning displays! (Hopefully)

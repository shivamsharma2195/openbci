# openbci
use processing 4.0 for openbcigui in app

openbci gui development

the provided ControlPanel.pde file should be replaced with the original file to access all the serial ports in open bci gui


few keywords to simulate any hardware data in open bci using cyton are

keyword from bci                      device response  to bci                                         purpose of response
"v"                                   "0xA0 0xB0 $$$"                                                 providing ADC and Accelerometer device id
"d"                                   ---not known-----                                               understanding the device getting connected
"c"                                   "no daisy to attach!8$$$"                                       selecting channel 8 or 16 by daisy not available or available respectively
"b"                                   ---start sending data stream continuously---                    data stream
"s"                                   ---stop sending data stream---  
"x"                                   --- full explanation below ---                                  setting gain


all the keywords are receieved on Rx[0] buffer then in the case of Rx[0] = "x" and Rx[8] = "X" then it means we need to send gain so for this our device response should be "Success: Channel set for '(Rx[1]-48)'$$$" this will set the gain of openbci gui.



for data stream data format must be in 8 channel so it should be bit by bit
"0xA0" - startbit
"0x01" - sample no 0-255
"0xC1" - MSB of channel1 data
"0xC1" - second bit of channel1 data
"0xC1" - third bit of channel1 data
"0xC2" - MSB of channel2 data
"0xC2" - second bit of channel2 data
"0xC2" - third bit of channel2 data
"0xC3" - MSB of channel3 data
"0xC3" - second bit of channel3 data
"0xC3" - third bit of channel3 data
"0xC4" - MSB of channel4 data
"0xC4" - second bit of channel4 data
"0xC4" - third bit of channel4 data
"0xC5" - MSB of channel5 data
"0xC5" - second bit of channel5 data
"0xC5" - third bit of channel5 data
"0xC6" - MSB of channel6 data
"0xC6" - second bit of channel6 data
"0xC6" - third bit of channel6 data
"0xC7" - MSB of channel7 data
"0xC7" - second bit of channel7 data
"0xC7" - third bit of channel7 data
"0xC8" - MSB of channel8 data
"0xC8" - second bit of channel8 data
"0xC8" - third bit of channel8 data
"0x00" - AccelX1 data
"0x00" - AccelX2 data
"0x00" - AccelY1 data
"0x00" - AccelY2 data
"0x00" - AccelZ1 data
"0x00" - AccelZ2 data
"0xC0" - end bit
      
    

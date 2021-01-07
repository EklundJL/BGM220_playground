# BGM220_playground
Working code examples for BGM220 Explorer Kit Board

## 1) ADC

  *Modified Silabs code for another board which expected input on PC4,
  not accessible on the Explorer Kit board, so I changed to PC0.*
  
  "...The ADC reads GPIO pins PC4
   (P25 on BRD4001 J102) as input. "
 
 *Here is where the change went-*
 
    // Configure Input sources for single ended conversion
    //initSingleInput.posInput = iadcPosInputPortCPin4;  NO PIN C4 on Explorer
    initSingleInput.posInput = iadcPosInputPortCPin0;
  
  *Later I also included Port C pin 1 (besides original Port B pin 1)
  notifying when conversion occurring.  On a 'scope, pulse is about 100 ns wide, 
  every 13 us (77kHz).*
  
     // Configure PB1 as output, will indicate when conversions are being performed
    GPIO_PinModeSet(gpioPortB, 1, gpioModePushPull, 0);
    GPIO_PinModeSet(gpioPortC, 1, gpioModePushPull, 0); //JAE

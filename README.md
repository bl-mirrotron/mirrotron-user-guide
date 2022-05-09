# The Mirrotron RFQ Low Level RF System  
The Low Level RF (LLRF) System is a modular system based on the Red-Pitaya Stemlab 125-14 reconfigurable instrument platform. A modular approach was chosen for design simplicity and future upgrades. Likewise, the Red-Pitaya Stemlab 125-14 was chosen for its ease of use. A block diagram is shown in [Figure 1](#figure-1). The LLRF system comprises of four modules:  
- [RF Frequency Source](#rf-frequency-source)
- [Four Quadrant IQ Phase Detector](#four-quadrant-iq-phase-detector)
- [Four Channel Timing System](#four-channel-timing-system)
- [IQ Monitor System](#iq-monitor-system)  

![llrf block diagam](images/LlrfFPDiagram.png)  
##### Figure 1 #####  
*Block diagram of LLRF*

![llr](images/llrf.jpg)
##### Figure 2 #####
*Photo of LLRF modules*  

## RF Frequency Source
[(go to top)](#the-mirrotron-rfq-low-level-rf-system)  
The function of the RF frequency source is to provide pulsed 200 MHz RF with frequency and amplitude control. In addition it provides a local oscillator signal to the Phase Detector module and in return receives a frequency error signal from the Phase detector. The block diagram of the frequency source is shown in Figure 3.
![rf-source diagam](images/LLRF-Freq-Source.png)  
##### Figure 3 #####
*RF Frequency Source Block Diagram*  

![rf-source dsp](images/mirrotron-rf-src.png)  
##### Figure 4 #####
*RF Frequency Source DSP Code*  

![rf-source impl](images/freq-src.jpg)  
##### Figure 5 #####
*RF Frequency Source Implementation*  

## Four Quadrant IQ Phase Detector
[(go to top)](#the-mirrotron-rfq-low-level-rf-system)  
Stuff to write  
![phase-detector diagam](images/LLRF-Phase-Detector.png)  
##### Figure 6 #####
*Phase Detector Block Diagram*  

![phase-detector dsp](images/mirrotron-phase-detector.png)  
##### Figure 7 #####
*Phase Detector DSP Code*  

![phase-detector impl](images/phase-detector.jpg)  
##### Figure 8 #####
*Phase Detector Implementation*  

## Four Channel Timing System
[(go to top)](#the-mirrotron-rfq-low-level-rf-system)  
Stuff to write  
![timing-system dsp](images/mirrotron-timing.png)  
##### Figure 9 #####
*Timing System DSP Code*  

![timing-system impl](images/timer.jpg)  
##### Figure 10 #####
*Timing System Implementation*  

## IQ Monitor System
[(go to top)](#the-mirrotron-rfq-low-level-rf-system)  
Stuff to write  

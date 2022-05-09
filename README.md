# The Mirrotron RFQ Low Level RF System
## Contents
* [Overview](#overview)
    - [Block diagram of LLRF](#figure-1)
    - [LLRF modules Implementation](#figure-2)
* [RF Frequency Source](#rf-frequency-source)
    - [RF Frequency Source Block Diagram](#figure-3)
    - [RF Frequency Source DSP Code](#figure-4)
    - [RF Frequency Source Implementation](#figure-5)
* [Four Quadrant IQ Phase Detector](#four-quadrant-iq-phase-detector)
    - [Phase Detector Block Diagram](#figure-6)  
    - [Phase Detector DSP Code](#figure-7)  
    - [Phase Detector Implementation](#figure-8)  
* [Four Channel Timing System](#four-channel-timing-system)
    - [Timing System DSP Code](#figure-9)  
    - [Timing System Implementation](#figure-10)  
* [IQ Monitor System](#iq-monitor-system)

## Overview
[(table of contents)](#contents)  
The Low Level RF (LLRF) System is a modular system based on the Red-Pitaya Stemlab 125-14 reconfigurable instrument platform. A modular approach was chosen for design simplicity and future upgrades. Likewise, the Red-Pitaya Stemlab 125-14 was chosen for its ease of use. A block diagram is shown in [Figure 1](#figure-1). The LLRF system comprises of four modules:  
- [RF Frequency Source](#rf-frequency-source)
- [Four Quadrant IQ Phase Detector](#four-quadrant-iq-phase-detector)
- [Four Channel Timing System](#four-channel-timing-system)
- [IQ Monitor System](#iq-monitor-system)  

##### Figure 1 #####  
*Block diagram of LLRF*
![llrf block diagam](images/LlrfFPDiagram.png)  

##### Figure 2 #####
*LLRF modules Implementation*  
![llr](images/llrf.jpg)

## RF Frequency Source
[(table of contents)](#contents)  
The function of the RF frequency source is to provide pulsed 200 MHz RF with frequency and amplitude control. In addition it provides a local oscillator signal to the Phase Detector module and in return receives a frequency error signal from the Phase detector. The block diagram of the frequency source is shown in Figure 3.
##### Figure 3 #####
*RF Frequency Source Block Diagram*  
![rf-source diagam](images/LLRF-Freq-Source.png)  

##### Figure 4 #####
*RF Frequency Source DSP Code*  
![rf-source dsp](images/mirrotron-rf-src.png)  

##### Figure 5 #####
*RF Frequency Source Implementation*  
![rf-source impl](images/freq-src.jpg)  

## Four Quadrant IQ Phase Detector
[(table of contents)](#contents)  
Stuff to write  
##### Figure 6 #####
*Phase Detector Block Diagram*  
![phase-detector diagam](images/LLRF-Phase-Detector.png)  

##### Figure 7 #####
*Phase Detector DSP Code*  
![phase-detector dsp](images/mirrotron-phase-detector.png)  

##### Figure 8 #####
*Phase Detector Implementation*  
![phase-detector impl](images/phase-detector.jpg)  

## Four Channel Timing System
[(table of contents)](#contents)  
Stuff to write  
##### Figure 9 #####
*Timing System DSP Code*  
![timing-system dsp](images/mirrotron-timing.png)  

##### Figure 10 #####
*Timing System Implementation*  
![timing-system impl](images/timer.jpg)  

## IQ Monitor System
[(table of contents)](#contents)  
Stuff to write  

# The Mirrotron RFQ Low Level RF System  
The Low Level RF (LLRF) System is a modular system based on the Red-Pitaya Stemlab 125-14 reconfigurable instrument platform. A modular approach was chosen for design simplicity and future upgrades. Likewise, the Red-Pitaya Stemlab 125-14 was chosen for its ease of use. The LLRF system comprises of four modules:  
- [RF Frequency Source](#rf-frequency-source)
- Four Quadrant I-Q Phase Detector
- Four channel timing System
- Monitor System  

A block diagram is shown in Figure 1
![llrf block diagam](images/LlrfFPDiagram.png)  
*Figure 1. Block diagram of LLRF*
![llr](images/llrf.jpg)
*Figure 2. Photo of LLRF modules*
## RF Frequency Source
[top](#the-mirrotron-rfq-low-level-rf-system)
The function of the RF frequency source is to provide pulsed 200 MHz RF with frequency and amplitude control. In addition it provides a local oscillator signal to the Phase Detector module and in return receives a frequency error signal from the Phase detector. The block diagram of the frequency source is shown in Figure 3.

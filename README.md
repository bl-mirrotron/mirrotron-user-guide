# The Mirrotron RFQ Control System Users' Guide
## Table of Contents
* [Overview](#overview)
* [System Login](#system-login)
  - [Read-only roles](#read-only-roles)
  - [Setting privilege roles](#setting-privilege-roles)
* [Web Applications](#web-applications)
  - [Application Index Page](#application-index-page)
  - [Bridge Control App](#bridge-control-app)
    - [Alarms](#alarms)
    - [RFQ Startup Steps](#rfq-startup-steps)
  * [Machine Permit App](#machine-permit-app)
  * [Alarm Scanner App](#alarm-scanner-app)
  * [Post Mortem App](#post-mortem-app)
* [Figures](#figures)

## Overview
([contents](#table-of-contents))<br>
The [control system for the Mirrotron RFQ](https://www.bl-mirrotron.com/) uses the [Blinky-Lite<sup>TM</sup>](https://www.bl-mc.se/) control platform. This document is an overview of how to use the custom applications for the Mirrotron RFQ. For portability, reliability, and security all Blinky-Lite<sup>TM</sup> user applications are web apps. The Mirrotron RFQ web apps are located at the app [page](https://www.bl-mirrotron.com/apps).

## System Login
([contents](#table-of-contents))<br>
For security, Blinky-Lite<sup>TM</sup> requires an [https](https://www.cloudflare.com/learning/ssl/what-is-https/) connection. Any attempt at using an http connection will be redirected to an https connection.

You must first obtain a login from your system administrator to access the control system. Blinky-Lite<sup>TM</sup> uses role-based access with Jason Web Token(JWT) technology for logging into the system. The user is assigned a role to protect the system from the user making inadvertent settings.

### Read-only roles
([contents](#table-of-contents))<br>
For read only access, the user must have the following roles:
* reading
* ping
* readDatabase
* renew
* appView
* coreView

### Setting privilege roles
([contents](#table-of-contents))<br>
For read only access, the user must have the following roles:
* reading
* setting
* rsetting (for using the RESTful interface)
* ping
* readDatabase
* renew
* appView
* coreView
* writeDatabase

The login JWT has an expiration timer that is set in the user profile by the system administrator. The timer can be extended in the User card found at the bottom of most of the applications as shown in [Figure 1](#figure-1). In addition login JWT expires when the user closes the browser session.

## Web Applications
([contents](#table-of-contents))<br>

### Application Index Page
([contents](#table-of-contents))<br>
Upon entry to the application [link](https://www.bl-mirrotron.com/apps), the main application index page is displayed as shown in [Figure 1](#figure-1). Most of the applications are for trouble-shooting. The main application for turn-key operations is the Bridge Control app.

### Bridge Control App
([contents](#table-of-contents))<br>
#### Alarms
([contents](#table-of-contents))<br>
Upon startup, the Bridge Control will look as shown in [Figure 2](#figure-2). If the RFQ is off but all water systems, vacuum systems are running, and power amplifier is running, there will be a green permit LED in the status card. All alarm LEDs on the right hand page of the status card should be green. Alarm LEDs have the following color scheme.

| Alarm Color |Alarm|
|---|:---:|
|<span style="color:magenta">Magenta</span>|below the LOLO limit|
|<span style="color:blue">Blue</span>|below the LOW limit|
|<span style="color:green">Green</span>|OK|
|<span style="color:yellow">Yellow</span>|above the HIGH limit|
|<span style="color:red">Red</span>|above the HIHI limit|

If any alarm is outside the LOLO or HIHI limit, the machine permit will not be enabled. There will be a discussion later on the steps to be followed if there machine permit is off.

#### RFQ Startup Steps
([contents](#table-of-contents))<br>
* **Turn on LLRF**
  - The LLRF On/Off is the main activator for the machine protection system. If the machine permit has dropped, the LLRF will turn off and stay turned off until the user turns it back on. The next step is to turn on the LLRF in the Control card as shown in [Figure 3](#figure-3).
* **Turn on RF power amplifier**
  - With the LLRF on, the RF power amplifier is ready to be turned on. (In fact the RF power amplifier can be turned on before turning on the LLRF). Turn on the power amp button in the Control card as shown in [Figure 4](#figure-4).
  - The amplifier will take some time to turn on (~15secs). While the amplifier is turning on, the Power Amp On LED in the Status card will remain gray until the power amplifier is ready and the Power Amp On LED in the Status card will turn green as shown in [Figure 5](#figure-5).
* **Turn on RF power**
  - One the Power Amp On LED in the Status card turns green, press on the RF Power On button on the Control card. Once the RF Power On LED on the Status card turns green, you should see traces appear on Scope Plot Card as shown in [Figure 6](#figure-6).
  - The forward and reverse power traces are shown in brown and gold. The forward power should be close (but not exactly) to the requested power shown in the Status and Control cards. The forward and reverse power sampled in the middle of the pulse is shown in the Status card. If the reverse power should be less than 10% of the forward power. If there reverse power is large, there could be an issue with the phase lock which will be discussed later.
  - The cavity voltage normalized to the power coupler are the blue traces. These traces are sampled in the middle of the pulse by the LLRF and report a cavity phase. This phase is used for the phase lock system which keeps the cavity in tune.
*  **Adjusting RFQ Parameters**
  - The requested power, repetition rate, and pulse length can be adjusted from the Control card. However, there are limits on how much these parameters can be adjusted. The range of these parameters can be seen by clicking the parameter alarm LED on the right hand side of the app. For example, the alarm range of the repetition rate is shown in [Figure 7](#figure-7). If an entry is outside the LOLO-HIHI alarm range , the machine permit will drop.
    - The app will prohibit making setting changes outside the LOLO-HIHI alarm range. However, if the alarm range is changed so that the current setting lies outside the new alarm range, the machine permit will drop.

### Machine Permit App
([contents](#table-of-contents))<br>
The Bridge Control app gives a quick overview to RFQ operations. However, there are hundreds of parameters in the control system that need to be at the correct value for the RFQ to operate appropriately. If any one of these critical parameters goes outside its LOLO-HIHI alarm range, the permit will drop and the LLRF will be inhibited. For example, [Figure 8](#figure-8) shows a machine permit drop when the pulse repetition rate has been set too low. What system pulled the machine permit can be seen on the Machine Permit app as shown in [Figure 9](#figure-9) in which it is clear that the timing system pulled the permit.

### Alarm Scanner App
([contents](#table-of-contents))<br>
The specific parameters that are in alarm and the type of alarm can be detailed in the Alarm Scanner App. The alarms are grouped into *Alarms* which are parameters that are outside the LOLO-HIHI limits and *Warnings* which are parameters outside the LOW-HIGH limits. Alarms will pull the Machine permit, warnings will not. For the example in which the pulse repetition rate has been set too low, a view of the alarms are shown in [Figure 10](#figure-10).

### Post Mortem App
([contents](#table-of-contents))<br>
As discussed in the [Machine Permit app](#machine-permit-app) section When the Machine permit is pulled the LLRF will be inhibited. The LLRF will stay inhibited until it is turned back on again, even if the critical parameter goes back inside its LOLO-HIHI alarm range. This often happens during a vacuum pressure spike. For example, [Figure 11](#figure-11) shows the machine permit being cleared when the pulse repetition rate has been set inside allowed range. The machine permit is clear but the LLRF is still off. So now the user does not know why the Machine permit was pulled.

To find out which parameter caused a machine permit drop, the [Blinky-Lite<sup>TM</sup>](https://www.bl-mc.se/) control platform provides a Post-Mortem application as shown in [Figure 12](#figure-12). When the Machine permit transitions from good to bad (an abort), the control system sends out a broadcast to all the sub-systems ([Blinky-Lite<sup>TM</sup>](https://www.bl-mc.se/) trays) to save their current state in timestamped archive database. The Machine Permit app shows a list of all the machine permit aborts. The user can then select one of the Machine permit abort events to see what parameters pulled the Machine permit as shown in [Figure 13](#figure-13) in which the machine permit abort was caused by setting the repetition rate too low.

## Figures
([contents](#table-of-contents))<br>
### Figure list
|Figure|Caption|
|------|-------|
[Figure 1](#figure-1) | Application Index Page
[Figure 2](#figure-2) | Bridge Control App at startup
[Figure 3](#figure-3) | Bridge Control App with LLRF on
[Figure 4](#figure-4) | Bridge Control App with RF power amp startup
[Figure 5](#figure-5) | Bridge Control App with RF power amp ready
[Figure 6](#figure-6) | Bridge Control App with RF power on
[Figure 7](#figure-7) | Repetition Rate Alarm Range
[Figure 8](#figure-8) | Machine Permit Abort
[Figure 9](#figure-9) | Machine Permit App
[Figure 10](#figure-10) | Alarm Scanner App
[Figure 11](#figure-11) | Bridge Control App with the machine permit cleared
[Figure 12](#figure-12) | Post Mortem app
[Figure 13](#figure-13) | Post Mortem app with alarm list

##### Figure 1 #####
*Application Index Page* <br>
([Application index page ](#application-index-page) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/AppIndexPage.png"/></div>

##### Figure 2 #####
*Bridge Control App at startup*<br>
([Bridge control app](#bridge-control-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConStarting.png"/></div>

##### Figure 3 #####
*Bridge Control App with LLRF on*<br>
([RFQ startup steps](#rfq-startup-steps) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConDDSOn.png"/></div>

##### Figure 4 #####
*Bridge Control App with RF power amp startup*<br>
([RFQ startup steps](#rfq-startup-steps) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRFAmpStartingUp.png"/></div>

##### Figure 5 #####
*Bridge Control App with RF power amp ready*<br>
([RFQ startup steps](#rfq-startup-steps) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConPAReady.png"/></div>

##### Figure 6 #####
*Bridge Control App with RF power on*<br>
([RFQ startup steps](#rfq-startup-steps) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRFOn.png"/></div>

##### Figure 7 #####
*Repetition Rate Alarm Range*<br>
([RFQ startup steps](#rfq-startup-steps) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRepRateAlarmRange.png"/></div>

##### Figure 8 #####
*Machine Permit Abort*<br>
([Machine permit app](#machine-permit-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConPermitDrop.png"/></div>

##### Figure 9 #####
*Machine Permit App*<br>
([Machine permit app](#machine-permit-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/MachinePermitTimingError.png"/></div>

##### Figure 10 #####
*Alarm Scanner App*<br>
([Alarm Scanner App](#alarm-scanner-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/AlarmScannerRepRatePermit.png"/></div>

##### Figure 11 #####
*Bridge Control App with the machine permit cleared*<br>
([Post Mortem App](#post-mortem-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConPermitClearedRFOff.png"/></div>

##### Figure 12 #####
*Post Mortem app*<br>
([Post Mortem App](#post-mortem-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/PostMortemAbortList.png"/></div>

##### Figure 13 #####
*Post Mortem app with alarm list*<br>
([Post Mortem App](#post-mortem-app) or [contents](#table-of-contents) or [Figures](#figures))
<div style="width:100%;text-align:center;"><img src="doc/PostMortemAlarmList.png"/></div>

# The Mirrotron RFQ Control System Users' Guide
## Overview
The [control system for the Mirrotron RFQ](https://www.bl-mirrotron.com/) uses the [Blinky-Lite<sup>TM</sup>](https://www.bl-mc.se/) control platform. This document is an overview of how to use the custom applications for the Mirrotron RFQ. For portability, reliability, and security all Blinky-Lite<sup>TM</sup> user applications are web apps. The Mirrotron RFQ web apps are located at the app [page](https://www.bl-mirrotron.com/apps).
## System Login
For security, Blinky-Lite<sup>TM</sup> requires an [https](https://www.cloudflare.com/learning/ssl/what-is-https/) connection. Any attempt at using an http connection will be redirected to an https connection.

You must first obtain a login from your system administrator to access the control system. Blinky-Lite<sup>TM</sup> uses role-based access with Jason Web Token(JWT) technology for logging into the system. The user is assigned a role to protect the system from the user making inadvertent settings.
### Read-only roles
For read only access, the user must have the following roles:
* reading
* ping
* readDatabase
* renew
* appView
* coreView

### Setting privilege roles
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

### Application Index Page

Upon entry to the application [link](https://www.bl-mirrotron.com/apps), the main application index page is displayed as shown in [Figure 1](#figure-1). Most of the applications are for trouble-shooting. The main application for turn-key operations is the Bridge Control app.

### Bridge Control App

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


##### Figure 1 #####
*Application Index Page* ([back](#application-index-page))
<div style="width:100%;text-align:center;"><img src="doc/AppIndexPage.png"/></div>

##### Figure 2 #####
*Bridge Control App at startup* ([back](#bridge-control-app))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConStarting.png"/></div>

##### Figure 3 #####
*Bridge Control App with LLRF on* ([back](#rfq-startup-steps))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConDDSOn.png"/></div>

##### Figure 4 #####
*Bridge Control App with RF power amp startup* ([back](#rfq-startup-steps))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRFAmpStartingUp.png"/></div>

##### Figure 5 #####
*Bridge Control App with RF power amp ready* ([back](#rfq-startup-steps))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConPAReady.png"/></div>

##### Figure 6 #####
*Bridge Control App with RF power on* ([back](#rfq-startup-steps))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRFOn.png"/></div>

##### Figure 6 #####
*Repetition Rate Alarm Range* ([back](#rfq-startup-steps))
<div style="width:100%;text-align:center;"><img src="doc/BridgeConRepRateAlarmRange.png"/></div>

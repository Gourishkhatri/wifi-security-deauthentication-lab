\# Wi-Fi Security Investigation Notes



\## Project



Wi-Fi Security — Deauthentication Attack Simulation



\## Case Information



Case ID: WIFI-001

Analyst: Gourish Khatri

Environment: Controlled / Authorized Training Analysis

Tool: Wireshark

Capture: 01\_80211\_network\_join.pcap



---



\## Objective



The objective of this laboratory is to analyze IEEE 802.11 wireless management frames and understand the relationship between authentication, association, normal wireless traffic, and deauthentication events.



---



\## Capture Overview



Total packets in capture: 1180



The capture contains IEEE 802.11 wireless management and data traffic.



The following frame types were specifically analyzed:



\- Authentication

\- Association Request

\- Association Response

\- Deauthentication



---



\## Authentication Analysis



Display filter:



&nbsp;   wlan.fc.type\_subtype == 0x0b



Two authentication frames were identified.



\### Frame 715



Time: 44.545208 seconds



Source:

00:16:bc:3d:aa:57



Destination:

00:01:e3:41:bd:6e



Authentication Algorithm:

Open System (0)



Authentication Sequence:

0x0001



Status:

Successful (0x0000)



\### Frame 717



Time: 44.546099 seconds



Source:

00:01:e3:41:bd:6e



Destination:

00:16:bc:3d:aa:57



Authentication Algorithm:

Open System (0)



Authentication Sequence:

0x0002



Status:

Successful (0x0000)



\### Observation



The capture shows a successful two-frame Open System authentication exchange between the wireless station and the BSS.



---



\## Association Analysis



Display filters:



&nbsp;   wlan.fc.type\_subtype == 0x00



&nbsp;   wlan.fc.type\_subtype == 0x01



\### Frame 719 — Association Request



Time: 44.547196 seconds



Source:

00:16:bc:3d:aa:57



Destination / BSSID:

00:01:e3:41:bd:6e



SSID:

martinet3



Sequence Number:

14



Capabilities Information:

0x0411



Listen Interval:

0x000a



\### Frame 721 — Association Response



Time: 44.548462 seconds



Source / BSSID:

00:01:e3:41:bd:6e



Destination:

00:16:bc:3d:aa:57



Status:

Successful (0x0000)



Association ID:

0x0004



Sequence Number:

439



\### Observation



The capture shows a successful association request and response following the authentication exchange.



---



\## Deauthentication Analysis



Display filter:



&nbsp;   wlan.fc.type\_subtype == 0x0c



One matching deauthentication frame was identified.



\### Frame 1106



Time:

58.884717 seconds



Source / Transmitter:

00:16:bc:3d:aa:57



Destination / Receiver:

00:01:e3:41:bd:6e



BSS ID:

00:01:e3:41:bd:6e



Frame Type:

Deauthentication



Subtype:

0x000c



Sequence Number:

72



Reason Code:

0x0003



Wireshark interpretation:

Deauthenticated because sending STA is leaving (or has left) the BSS.



---



\## Surrounding Traffic



Frames immediately surrounding frame 1106 include 802.11 acknowledgement and other wireless traffic.



Frame 1105:

Acknowledgement



Frame 1106:

Deauthentication



Frame 1107:

Acknowledgement



The capture also contains normal data and null-function traffic associated with the same wireless station before the deauthentication event.



---



\## Investigation Assessment



The capture confirms the presence of an IEEE 802.11 deauthentication frame.



The observed reason code is 0x0003, indicating that the sending station is leaving or has left the BSS.



The available evidence does not by itself establish that the deauthentication event was a malicious attack.



No conclusion of unauthorized activity is made from this capture alone.



---



\## Evidence-Based Conclusion



The laboratory successfully demonstrated identification and analysis of:



1\. Open System authentication

2\. Successful association

3\. Normal 802.11 traffic

4\. A deauthentication event

5\. Deauthentication reason code analysis



The exercise demonstrates how Wireshark can be used to investigate wireless management frames and interpret their fields in a controlled cybersecurity training environment.



---



\## Disclaimer



This analysis uses an authorized/sample wireless capture for cybersecurity education and defensive analysis.



No unauthorized wireless network or device was targeted.


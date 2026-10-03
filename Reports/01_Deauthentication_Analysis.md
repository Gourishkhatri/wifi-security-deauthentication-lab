\# Wi-Fi Deauthentication Frame Analysis Report



\## 1. Executive Summary



This report documents a controlled analysis of an IEEE 802.11 wireless packet capture using Wireshark.



The investigation focused on identifying authentication, association, and deauthentication management frames and examining the fields associated with the observed deauthentication event.



One deauthentication frame was identified in the capture. Its reason code was 0x0003, which Wireshark interprets as the sending station leaving or having left the BSS.



The evidence does not establish that the observed event was a malicious deauthentication attack.



---



\## 2. Investigation Information



| Field | Value |

|---|---|

| Case ID | WIFI-001 |

| Analyst | Gourish Khatri |

| Tool | Wireshark |

| Capture | 01\_80211\_network\_join.pcap |

| Environment | Controlled / Authorized Training Analysis |

| Total Packets | 1180 |



---



\## 3. Investigation Objective



The objectives of this investigation were:



\- Identify IEEE 802.11 management frames.

\- Analyze authentication exchanges.

\- Analyze association request and response frames.

\- Identify deauthentication frames.

\- Examine the deauthentication reason code.

\- Analyze traffic surrounding the observed event.

\- Document findings using evidence-based observations.



---



\## 4. Methodology



The packet capture was opened in Wireshark and analyzed using IEEE 802.11 display filters.



The following filters were used:



\### Authentication



&nbsp;   wlan.fc.type\_subtype == 0x0b



\### Association Request



&nbsp;   wlan.fc.type\_subtype == 0x00



\### Association Response



&nbsp;   wlan.fc.type\_subtype == 0x01



\### Deauthentication



&nbsp;   wlan.fc.type\_subtype == 0x0c



The relevant packets were selected and their IEEE 802.11 fields were examined in the packet details pane.



---



\## 5. Authentication Findings



\### Frame 715



Timestamp: 44.545208 seconds



Source:

00:16:bc:3d:aa:57



Destination:

00:01:e3:41:bd:6e



Authentication Algorithm:

Open System (0)



Authentication Sequence:

0x0001



Status Code:

Successful (0x0000)



\### Frame 717



Timestamp: 44.546099 seconds



Source:

00:01:e3:41:bd:6e



Destination:

00:16:bc:3d:aa:57



Authentication Algorithm:

Open System (0)



Authentication Sequence:

0x0002



Status Code:

Successful (0x0000)



\### Finding



The capture contains a successful two-frame Open System authentication exchange.



---



\## 6. Association Findings



\### Frame 719 — Association Request



Timestamp: 44.547196 seconds



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



Timestamp: 44.548462 seconds



Source / BSSID:

00:01:e3:41:bd:6e



Destination:

00:16:bc:3d:aa:57



Status Code:

Successful (0x0000)



Association ID:

0x0004



Sequence Number:

439



\### Finding



The station successfully completed the association exchange after authentication.



---



\## 7. Deauthentication Event



\### Frame 1106



Timestamp:

58.884717 seconds



Frame Type:

Deauthentication



Subtype:

0x000c



Source / Transmitter:

00:16:bc:3d:aa:57



Destination / Receiver:

00:01:e3:41:bd:6e



BSS ID:

00:01:e3:41:bd:6e



Sequence Number:

72



\### Reason Code



0x0003



Wireshark interpretation:



"Deauthenticated because sending STA is leaving (or has left) the BSS."



---



\## 8. Surrounding Traffic Analysis



The packets immediately surrounding frame 1106 were examined.



Frame 1105:

Acknowledgement



Frame 1106:

Deauthentication



Frame 1107:

Acknowledgement



Additional traffic before the event includes data and null-function 802.11 frames associated with the station.



The capture therefore provides context around the observed deauthentication frame rather than showing the frame in isolation.



---



\## 9. Evidence Assessment



The investigation confirms that a deauthentication management frame exists in the supplied capture.



The reason code is 0x0003 and is interpreted by Wireshark as indicating that the sending station is leaving or has left the BSS.



The evidence reviewed in this laboratory does not establish that the frame represents a malicious deauthentication attack.



A single deauthentication frame, without additional corroborating evidence, should not automatically be classified as an attack.



---



\## 10. Security Relevance



Deauthentication frames are an important part of wireless security monitoring because unexpected or repeated deauthentication events can be relevant during investigation of wireless connectivity disruptions.



For defensive monitoring, analysts can examine:



\- Frequency of deauthentication frames.

\- Source and destination addresses.

\- BSSID relationships.

\- Reason codes.

\- Timing and sequence of events.

\- Repeated patterns involving the same station or BSS.



These indicators should be evaluated together with additional network evidence.



---



\## 11. Evidence Limitations



This investigation is based on a provided/sample 802.11 packet capture.



The capture represents a limited observation window and does not by itself provide complete information about the physical wireless environment.



Therefore, conclusions are limited to the packets and fields visible in the capture.



No claim is made regarding the intent of the sender.



---



\## 12. Conclusion



The laboratory successfully demonstrated wireless packet analysis using Wireshark.



The investigation identified:



1\. Successful Open System authentication.

2\. Successful association with SSID "martinet3".

3\. Normal 802.11 traffic associated with the station.

4\. One deauthentication frame.

5\. Deauthentication reason code 0x0003.

6\. Surrounding acknowledgement and wireless traffic.



The exercise demonstrates how IEEE 802.11 management frames can be filtered, examined, and documented during a wireless security investigation.



---



\## 13. Tools



\- Wireshark

\- IEEE 802.11 packet capture

\- Windows

\- Display filters



---



\## 14. Ethical and Safety Statement



This project is intended exclusively for authorized cybersecurity education and defensive analysis.



No unauthorized wireless network, access point, or device was targeted.



The analysis does not include instructions for disrupting wireless networks.


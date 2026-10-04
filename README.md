# 🔎 Investigating Harassment Email Traffic With Wireshark

**Case Study:** Investigating Harassment Email Traffic With Wireshark
**Analyst:** Kafayat Animashawun
**Investigation Type:** Network Forensics • Packet Analysis • Digital Evidence Correlation
**Primary Tool:** Wireshark
**Case:** Nitroba State University - Harassment Investigation

---

## 📌 Case Overview

This repository documents a network-forensics investigation conducted as part of the **SBT-DF204 Computer Forensics Case Studies** assessment.

The investigation concerns a fictional harassment case involving **Nitroba State University**. Lily Tuckrige, a Chemistry 109 teacher, received threatening and harassing communications. The university captured network traffic at the Ethernet boundary in an attempt to identify the system responsible for submitting one of the messages.

The investigation uses a provided network capture (`nitroba.pcap`) and supporting case material to determine:

* 💻 Which client system contacted the relevant web service
* 🌐 Which network request contained the harassment message
* 🔌 Which network interface/device generated the relevant request
* 🍪 Whether browser/session evidence associates that device with a particular account
* 🎓 Whether that account can be associated with a Chemistry 109 student
* 🕒 When the relevant activity occurred
* ⚖️ Whether the available evidence supports attribution to a specific individual
* 🛡️ What limitations prevent a stronger attribution conclusion

The investigation deliberately distinguishes between **network-level evidence**, **device-level evidence**, **account/session evidence**, and **human attribution**.

---

## 🎯 Investigation Objective

The primary objective was to determine whether the available network evidence supports attribution of the harassment message to a Chemistry 109 student.

The investigation examined the relationship between:

```text
🌐 Client IP
      ↓
🖥️ Network Service
      ↓
📨 Harassment HTTP POST
      ↓
🔌 Source MAC Address
      ↓
🍪 Browser / Session Cookie
      ↓
👤 Account Identifier
      ↓
🎓 Chemistry 109 Roster
      ↓
⚖️ Attribution Assessment
```

The investigation does **not** assume that an IP address alone identifies a person.

This distinction is particularly important because the case scenario states that an open/passwordless wireless router was available in the dormitory. Consequently, multiple individuals could potentially use the same network connection.

---

## 📂 Evidence Source

The primary evidence was the publicly provided Nitroba State University network capture:

**Evidence:** `nitroba.pcap`

Supporting case material was provided in the Nitroba investigation slide deck, including contextual information and the Chemistry 109 class roster.

The investigation preserves the original PCAP and maintains derived evidence separately.

---

## 🔐 Evidence Preservation & Integrity

The original PCAP was preserved as a primary evidence item and copied into the structured evidence directory.

### 📄 Primary Evidence

```text
Investigation/Evidence/E01_nitroba.pcap
```

### 📊 PCAP Metadata

| Property               | Value                           |
| ---------------------- | ------------------------------- |
| 📦 File type           | PCAP                            |
| 🔢 PCAP version        | 2.4                             |
| 🔌 Encapsulation       | Ethernet                        |
| ⏱️ Timestamp precision | Microsecond                     |
| 📦 Packet count        | 94,410                          |
| 💾 File size           | 56,180,821 bytes                |
| 📏 Approximate size    | 54 MB                           |
| 🕐 First packet        | 2008-07-21 21:51:07.095278      |
| 🕐 Last packet         | 2008-07-22 02:13:47.046029      |
| ⏳ Capture duration     | Approximately 4h 22m 39.950751s |

### #️⃣ Cryptographic Hashes

**MD5**

```text
9981827f11968773ff815e39f5458ec8
```

**SHA-1**

```text
65656392412add15f93f8585197a8998aaeb50a1
```

**SHA-256**

```text
2b77a9eaefc1d6af163d1ba793c96dbccacb04e6befdf1a0b01f8c67553ec2fb
```

### ✅ Integrity Result

**PASS**

The calculated hashes matched the published hashes for the original case-study PCAP.

Detailed acquisition and integrity documentation:

```text
Investigation/Evidence/E01_Evidence_Acquisition_and_Integrity.txt
```

---

## 🗂️ Repository Structure

The repository preserves both the formally organised investigation evidence and the original working material.

```text
.
├── 📄 README.md
│
├── 📁 Investigation/
│   │
│   ├── 📁 Evidence/
│   │   ├── 📄 E01_Evidence_Acquisition_and_Integrity.txt
│   │   ├── 🗃️ E01_nitroba.pcap
│   │   ├── 🔢 E01_nitroba_pcap_MD5.txt
│   │   ├── 🔢 E01_nitroba_pcap_SHA1.txt
│   │   ├── 🔢 E01_nitroba_pcap_SHA256.txt
│   │   ├── 📄 E02_PCAP_Metadata.txt
│   │   ├── 🗃️ E03_HTTP_POST_secure_submit.pcap
│   │   ├── 🔢 E03_HTTP_POST_secure_submit_SHA256.txt
│   │   └── 📋 evidence_log.txt
│   │
│   ├── 📁 Notes/
│   │   ├── 📝 Investigation_Master_Notes.txt
│   │   └── ⚖️ Q8_Attribution_Assessment.txt
│   │
│   └── 📁 Wireshark-Analysis/
│   ├── ├── 🔎 filters.txt
│       ├── 📦 packet-findings.txt
│       │
│       ├── 🍪 Cookie-Analysis/
│       │   ├── Q5_Device_Account_Association.txt
│       │   └── Q6_Chem109_Roster_Verification.txt
│       │
│       ├── 🌐 HTTP-GET/
│       │   └── Q2_Client_System_Identification.txt
│       │
│       ├── 📨 HTTP-POST/
│       │   └── Q3_Harassment_Message_Correlation.txt
│       │
│       ├── 🔌 MAC-Analysis/
│       │   └── Q4_Device_MAC_Identification.txt
│       │
│       └── 🕒 Timeline/
│           └── Q7_Harassment_Timestamp.txt
│
├── 📁 Screenshots/
│   │
│   ├── 📄 .gitkeep
│   │
│   │   ├── 📄 Acquisition of the Nitroba network traffic capture from the specified Digital Corpora source.png
│   │   ├── 🗃️ Activity Timeline.png
│   │   ├── 🔢 Activity Timeline2.png
│   │   ├── 🔢 Association of the Device With an Individual.png
│   │   ├── 📄 Association of the Device With an Individual2.png
│   │   ├── 🗃️ Correlation of the Client System With the Harassment Message.png
│   │   ├── 🔢 Correlation of the Client System With the Harassment Message2.png
│   │   ├── 🔢 Correlation of the Client System With the Harassment Message3.png
│   │   ├── 🔢 Correlation of the Client System With the Harassment Message4.png
│   │   ├── 📄 Correlation of the Client System With the Harassment Message5.png
│   │   ├── 🗃️ Correlation of the Client System With the Harassment Message6.png
│   │   ├── 🔢 Correlation of the Client System With the Harassment Message7.png
│   │   ├── 📋 Establishment of the Forensic Working Environment.png
│   │   ├── 🗃️ Identification of the Client System Communicating With the Web Service.png
│   │   ├── 🔢 Identification of the Device That Made the Relevant Request.png
│   │   ├── 🔢 Identification of the Device That Made the Relevant Request2.png
│   │   ├── 🔢 Identification of the Device That Made the Relevant Request3.png
│   │   ├── 📄 PCAP Metadata Verification.png
│   │   ├── 🗃️ PCAP capture file.png
│   │   ├── 🔢 SHA-256 hash calculated for the acquired Nitroba PCAP.png
│   │   ├── 📋 Summary of the verified forensic working evidence.png
│   │   ├── 📄 Verification Against the Chemistry 109 Class Roster.png
│   │   ├── 🗃️ Verification of the acquired PCAP filename, location and file size.png
│   │   ├── 🔢 Verification of the forensic case directory.png
│   │   └── 📋 Wireshark identification of client IP 192.168.15.4.png
│
└── 📁 working/
    ├── 🗃️ E03_HTTP_POST_secure_submit.pcap
    └── 🗃️ nitroba.pcap
```

Duplicate working copies have intentionally been retained to preserve the complete investigation workspace.

---

## 🧪 Investigation Methodology

The investigation followed a structured network-forensics workflow:

```text
📥 Evidence Acquisition
        ↓
🔐 Integrity Verification
        ↓
📊 PCAP Metadata Examination
        ↓
🌐 HTTP Service Identification
        ↓
📨 Harassment Submission Identification
        ↓
🔌 Device / MAC Correlation
        ↓
🍪 Browser / Account Correlation
        ↓
🎓 Roster Correlation
        ↓
🕒 Timeline Reconstruction
        ↓
⚖️ Attribution Assessment
```

---

## 🌐 Client System Identification

Wireshark filter:

```text
http.request.method == "GET" && http.host == "www.willselfdestruct.com"
```

### 🔎 Frame 82936

The request identified the client system contacting the relevant web service.

```text
Source:      192.168.15.4
Destination: 69.25.94.22
Host:        www.willselfdestruct.com
Request:     GET /secure/submit
```

This establishes that `192.168.15.4` contacted the relevant web service.

The GET request was **not** treated as the harassment submission itself. The subsequent POST request was examined separately.

📄 Detailed analysis:

```text
Investigation/Wireshark-Analysis/HTTP-GET/Q2_Client_System_Identification.txt
```

---

## 📨 Harassment Message Identification

Wireshark filter:

```text
http.request.method == "POST" && http.host == "www.willselfdestruct.com"
```

### 🔎 Frame 83601

The actual harassment submission was identified in Frame **83601**.

```text
POST /secure/submit HTTP/1.1
```

### 🌐 Network Information

```text
Source IP:        192.168.15.4
Destination IP:   69.25.94.22
Source Port:      36044
Destination Port: 80
```

### 📋 HTTP Information

```text
Content-Type:     application/x-www-form-urlencoded
Content Length:   188 bytes
```

### 📨 Message Details

**Recipient**

```text
lilytuckrige@yahoo.com
```

**Subject**

```text
you can't find us
```

**Message**

```text
and you can't hide from us.

Stop teaching.

Start running
```

This provides direct network evidence that the client at `192.168.15.4` transmitted the identified harassment message to the web service.

📄 Detailed analysis:

```text
Investigation/Wireshark-Analysis/HTTP-POST/Q3_Harassment_Message_Correlation.txt
```

---

## 🔌 Device / MAC Address Identification

Frame **83601** identifies the Ethernet source MAC address:

```text
00:17:f2:e2:c0:ce
```

The relevant relationship is:

```text
🔌 MAC
00:17:f2:e2:c0:ce
        ↓
🌐 IP
192.168.15.4
        ↓
📨 HTTP POST
www.willselfdestruct.com
        ↓
⚠️ Harassment Message
```

Destination MAC:

```text
00:1d:d9:2e:4f:60
```

The source MAC identifies the network interface observed transmitting the relevant frame.

However:

> **A MAC address identifies a network interface/device, not a human being.**

The case scenario states that the dormitory had an open/passwordless wireless router. Multiple individuals could therefore potentially use the same network.

Consequently:

> **The IP address alone cannot establish the identity of the person who sent the message.**

The MAC address strengthens device-level correlation but does not independently establish the physical operator.

📄 Detailed analysis:

```text
Investigation/Wireshark-Analysis/MAC-Analysis/Q4_Device_MAC_Identification.txt
```

---

## 🍪 Browser / Account Correlation

Wireshark filter:

```text
eth.src == 00:17:f2:e2:c0:ce && http.cookie contains "@"
```

### 🔎 Frame 79187

The same device/IP combination was observed in Frame **79187**.

```text
Source MAC:  00:17:f2:e2:c0:ce
Source IP:   192.168.15.4
Destination: 74.125.19.17
```

The relevant browser/session cookie was:

```text
gmailchat=jcoachj@gmail.com/475090
```

This provides a browser/session-level association between the observed device and:

```text
jcoachj@gmail.com
```

The account-associated traffic occurred approximately three minutes before the harassment POST.

### 🔗 Correlation

```text
🔌 Same MAC
      +
🌐 Same IP
      +
🍪 Browser Session
      ↓
👤 jcoachj@gmail.com
```

The cookie is significant evidence, but it is not treated as conclusive proof that the account owner physically operated the device at the exact time of the harassment transmission.

📄 Detailed analysis:

```text
Investigation/Wireshark-Analysis/Cookie-Analysis/Q5_Device_Account_Association.txt
```

---

## 🎓 Chemistry 109 Roster Correlation

The case-provided investigation slides contain the Chemistry 109 roster.

**Source:**

```text
Nitroba State University - Harassment Investigation Slides
Slide 13 — "So who did it?"
PDF Page 14
```

The roster includes:

* Lily Tuckrige - Teacher
* Amy Smith
* Burt Greedom
* Tuck Gorge
* Ava Book
* **Johnny Coach**
* Jeremy Ledvkin
* Nancy Colburne
* Tamara Perkins
* Esther Pringle
* Asar Misrad
* Jenny Kant

Johnny Coach is listed as a Chemistry 109 student.

The observed account identifier:

```text
jcoachj@gmail.com
```

is used as the account-level correlation in the investigation.

This correlation is treated as supporting evidence rather than independent proof that Johnny Coach physically operated the device.

📄 Detailed analysis:

```text
Investigation/Wireshark-Analysis/Cookie-Analysis/Q6_Chem109_Roster_Verification.txt
```

---

## 🕒 Timeline Reconstruction

### 📨 Harassment Submission — Frame 83601

**Wireshark local time**

```text
Jul 22, 2008 02:04:24.311700 EDT
```

**UTC**

```text
Jul 22, 2008 06:04:24.311700 UTC
```

**Unix epoch**

```text
1216706664.311700000
```

**Time since first frame**

```text
4:13:17.216422
```

### 🍪 Account Cookie — Frame 79187

**Wireshark local time**

```text
Jul 22, 2008 02:01:06.373943 EDT
```

**UTC**

```text
Jul 22, 2008 06:01:06.373943 UTC
```

**Unix epoch**

```text
1216706466.373943000
```

### ⏱️ Event Relationship

The account-associated cookie event occurred approximately:

```text
3 minutes 17.937757 seconds
```

before the harassment POST.

The captured PCAP timestamp is used as the primary technical time reference.

📄 Detailed timeline:

```text
Investigation/Wireshark-Analysis/Timeline/Q7_Harassment_Timestamp.txt
```

---

## ⚖️ Attribution Assessment

The evidence chain is:

```text
🔎 Frame 83601
        ↓
📨 Harassment HTTP POST
        ↓
🌐 192.168.15.4
        ↓
🔌 00:17:f2:e2:c0:ce
        ↓
🔎 Frame 79187
        ↓
🍪 jcoachj@gmail.com
        ↓
🎓 Case-provided Chemistry 109 roster
        ↓
👤 Johnny Coach
```

### 📊 Confidence Assessment

| Attribution Layer                       | Confidence                                                   |
| --------------------------------------- | ------------------------------------------------------------ |
| 🔌 Device → Harassment submission       | **HIGH**                                                     |
| 🍪 Device → Browser/account             | **HIGH**                                                     |
| 🎓 Account → Chemistry 109 student      | **MODERATE**                                                 |
| 👤 Physical attribution to Johnny Coach | **MODERATE**                                                 |
| ⚖️ Overall                              | **STRONG ASSOCIATION - NOT CONCLUSIVE PHYSICAL ATTRIBUTION** |

---

## 🧾 Final Investigative Conclusion

The available PCAP evidence provides a **strong evidentiary association** between the harassment submission, the observed network device, the browser/session account `jcoachj@gmail.com`, and Johnny Coach, who is listed as a Chemistry 109 student in the case-provided roster.

The relevant HTTP POST in Frame **83601** directly contains the harassment message and originates from:

```text
192.168.15.4
```

The transmission is associated with:

```text
00:17:f2:e2:c0:ce
```

Earlier traffic from the same device/IP combination contains:

```text
gmailchat=jcoachj@gmail.com/475090
```

The case-provided roster lists Johnny Coach as a Chemistry 109 student.

However, the evidence does **not** conclusively establish that Johnny Coach was the physical person operating the device at the exact time of transmission.

### 🛡️ Defensible Position

> **The evidence establishes a strong association between the harassment message, a specific observed network device, the account `jcoachj@gmail.com`, and Johnny Coach as a Chemistry 109 student. However, the PCAP evidence alone is insufficient to establish conclusive physical attribution of the message to Johnny Coach.**

📄 Full attribution assessment:

```text
Investigation/Notes/Q8_Attribution_Assessment.txt
```

---

## 🚧 Investigation Limitations

### 📡 Shared Open Wireless Network

The case scenario indicates that an open/passwordless wireless router was installed in the dormitory.

Multiple individuals could therefore potentially use the same network.

**Shared IP ≠ Individual identity**

---

### 🔌 MAC Address Limitation

The MAC address:

```text
00:17:f2:e2:c0:ce
```

identifies an observed network interface.

It does not prove who was physically operating the device.

---

### 🍪 Browser Cookie Limitation

The cookie:

```text
gmailchat=jcoachj@gmail.com/475090
```

provides browser/session-level evidence.

It does not independently prove who was physically operating the computer at the precise time of the harassment submission.

Possible explanations include:

* The account owner operated the device.
* Another person used the device while the account remained logged in.
* Another person had access to the authenticated browser session.
* The account/session was accessible to someone else.

The PCAP alone cannot resolve these alternatives.

---

## 🔎 Additional Evidence That Could Strengthen Attribution

A stronger attribution conclusion would require independent corroborating evidence.

### 💻 Endpoint Evidence

* OS login records
* User account activity
* Browser history
* Browser cache
* Local cookies
* Download history
* File-system timestamps
* User profile artifacts
* Application execution records

### 🌐 Network Evidence

* DHCP records
* Wireless access-point logs
* Router logs
* Device association records
* Authentication records
* Additional traffic from the device
* Network access-control records

### 🏢 Physical / Administrative Evidence

* Device ownership records
* Dormitory access records
* Witness statements
* Computer usage records
* Additional evidence establishing who had access to the device

Independent evidence of this type could substantially increase confidence in physical attribution.

---

## 📋 Evidence Log

The investigation maintains a dedicated evidence log:

```text
Investigation/Evidence/evidence_log.txt
```

The log records:

* 🆔 Evidence identifiers
* 🔎 Packet/frame numbers
* 📌 Findings
* ⚖️ Evidentiary significance
* 📸 Screenshot references
* 🧠 Analytical conclusions
* 📊 Attribution confidence
* 🚧 Limitations

Major findings are tied to specific Wireshark packet/frame numbers.

---

## 📝 Master Investigation Notes

The complete investigative reasoning is maintained in:

```text
Investigation/Notes/Investigation_Master_Notes.txt
```

The master notes consolidate:

* 🎯 Investigation objective
* 📂 Primary evidence
* 🧪 Investigation approach
* 🌐 Client system identification
* 📨 Harassment message identification
* 🔌 Device/MAC correlation
* 🍪 Browser/account correlation
* 🎓 Chemistry 109 roster correlation
* 🕒 Timeline
* 🔗 Attribution chain
* 📡 Shared-network limitation
* ⚖️ Attribution assessment
* 🚧 Alternative explanations
* 🔎 Additional evidence requirements
* 🧾 Final investigative position

---

## 📑 Question-by-Question Evidence

| Question | Evidence                  | Primary Finding                                             |
| -------- | ------------------------- | ----------------------------------------------------------- |
| 🔐 Q1    | E01 / E02 / hashes        | Evidence acquired, preserved, and integrity verified        |
| 🌐 Q2    | Frame 82936               | Client `192.168.15.4` contacted the web service             |
| 📨 Q3    | Frame 83601               | Client transmitted the identified harassment message        |
| 🔌 Q4    | Frame 83601               | Source MAC `00:17:f2:e2:c0:ce` generated the relevant frame |
| 🍪 Q5    | Frame 79187               | Same device/IP associated with `jcoachj@gmail.com`          |
| 🎓 Q6    | Case slides / PDF page 14 | Johnny Coach is listed on the Chemistry 109 roster          |
| 🕒 Q7    | Frames 83601 / 79187      | Exact timestamps establish the event sequence               |
| ⚖️ Q8    | Combined evidence         | Strong association, but not conclusive physical attribution |

---

## 🗃️ Derived Evidence

A filtered PCAP containing the relevant HTTP POST traffic was created as derived evidence:

```text
Investigation/Evidence/E03_HTTP_POST_secure_submit.pcap
```

### SHA-256

```text
9cf13ace8bd8a88be5acbff63201a4402de4907a5adfb1e0708b1dbcfde4799e
```

The derived PCAP was created from the original capture for focused examination of the relevant HTTP POST traffic.

The original PCAP was retained separately and was not replaced by the derived evidence.

---

## 🧠 Analytical Principles

### 🔐 Evidence Before Assumption

Network observations are documented before attribution conclusions are made.

### 🔗 Correlation Is Not Automatically Identification

A relationship between an IP address, MAC address, account, and person is evaluated at each evidentiary layer.

### 🌐 IP Address ≠ Person

An IP address identifies a network endpoint or assigned address, not necessarily the individual using it.

### 🔌 MAC Address ≠ Person

A MAC address identifies a network interface, not necessarily the human operating the device.

### 🍪 Account ≠ Physical Operator

An authenticated browser session or cookie indicates account/session activity but does not independently establish who was physically present.

### 🧩 Independent Evidence Strengthens Attribution

A stronger attribution requires corroborating evidence beyond a single network capture.

---

## 🔄 Reproducibility

The investigation can be reproduced using the preserved PCAP and documented Wireshark filters.

```text
📂 Open E01_nitroba.pcap
        ↓
🌐 Identify www.willselfdestruct.com traffic
        ↓
🔎 Locate Frame 82936
        ↓
🌐 Identify client 192.168.15.4
        ↓
🔎 Locate Frame 83601
        ↓
📨 Inspect HTTP POST contents
        ↓
🔌 Identify MAC 00:17:f2:e2:c0:ce
        ↓
🔎 Search traffic from the same MAC
        ↓
🍪 Locate Frame 79187
        ↓
👤 Identify jcoachj@gmail.com
        ↓
🎓 Compare with case-provided roster
        ↓
🕒 Build timeline
        ↓
⚖️ Assess attribution and limitations
```

Exact filters are documented in:

```text
Investigation/Wireshark-Analysis/filters.txt
```

---

## 📸 Screenshots & Visual Evidence

Screenshots generated during the Wireshark investigation are maintained separately from the textual analytical records.

Relevant screenshots should provide visual confirmation of:

* 🌐 Client identification
* 📨 Harassment POST
* 🔌 MAC address
* 🍪 Browser/session cookie
* 🎓 Chemistry 109 roster
* 🕒 Relevant timestamps
* ⚖️ Attribution evidence

Each major screenshot should be traceable to:

```text
Packet/Frame → Wireshark Filter → Finding → Evidence Log
```

---

## 🛠️ Tools Used

### 🦈 Wireshark

Used for:

* PCAP examination
* Packet filtering
* HTTP analysis
* Ethernet frame analysis
* MAC address analysis
* Cookie inspection
* Timestamp analysis
* Packet-level evidence correlation

### 🐧 Kali Linux

Used for:

* Evidence file management
* Hash verification
* File metadata inspection
* Investigation organisation
* Git version control

### 🐙 Git / GitHub

Used to maintain a version-controlled copy of the investigation materials and preserve the documented investigative workflow.

---

## 🎓 Skills Demonstrated

This investigation demonstrates practical application of:

* 🔎 Network forensics
* 🦈 Wireshark packet analysis
* 🌐 HTTP traffic analysis
* 🔌 Ethernet frame analysis
* 🆔 MAC address identification
* 🌐 IP address correlation
* 🍪 Browser/session analysis
* 🧩 Cookie analysis
* 🕒 Timeline reconstruction
* 🔐 Evidence preservation
* #️⃣ Cryptographic hashing
* 📋 Evidence logging
* ⚖️ Attribution assessment
* 🚧 Forensic limitation analysis
* 🔗 Git-based investigation documentation

---

## 📊 Investigation Status

| Area                                 | Status     |
| ------------------------------------ | ---------- |
| 📥 Evidence acquisition              | ✅ Complete |
| 🔐 Hash verification                 | ✅ Complete |
| 📊 PCAP metadata                     | ✅ Complete |
| 🌐 Client identification             | ✅ Complete |
| 📨 Harassment message identification | ✅ Complete |
| 🔌 MAC analysis                      | ✅ Complete |
| 🍪 Cookie/account analysis           | ✅ Complete |
| 🎓 Roster verification               | ✅ Complete |
| 🕒 Timeline analysis                 | ✅ Complete |
| ⚖️ Attribution assessment            | ✅ Complete |
| 📋 Evidence log                      | ✅ Complete |
| 📝 Investigation notes               | ✅ Complete |
| 🐙 GitHub repository                 | ✅ Complete |
| 📸 Screenshot documentation          | ✅ Complete |
| 📄 Final report                      | ✅ Complete |

---

## 👩🏾‍💻 Analyst

**Kafayat Animashawun**

**SBT-DF204 — Computer Forensics Case Studies**

**Case Study:** Investigating Harassment Email Traffic With Wireshark

---

## 🛡️ Final Forensic Position

This repository represents the documented forensic investigation of the Nitroba State University harassment-email case.

The analysis demonstrates that packet-level evidence can establish meaningful relationships between network activity, devices, browser sessions, and accounts. It also demonstrates the importance of distinguishing those technical relationships from definitive human attribution.

### ⚖️ Final Conclusion

> **The PCAP provides strong evidence associating the harassment transmission with a specific observed device and a browser/session associated with `jcoachj@gmail.com`, while the case-provided roster identifies Johnny Coach as a Chemistry 109 student. However, the available PCAP evidence alone does not conclusively establish that Johnny Coach was the physical operator who sent the harassment message.**

---

### 🔎 Evidence. Correlation. Context. Attribution.

**A defensible forensic conclusion is one that goes only as far as the evidence allows.**

\# BLESMPForge Pro (v1.0.0)  
\> \*\*Enterprise Bluetooth Low Energy (BLE 5.4) Security Manager Protocol (SMP) Studio, Pairing PDU Dissector, Association Model Matrix & 10-Point Normative Zero-Trust Compliance Auditor\*\*

\[\!\[Bluetooth Core\](https\://img.shields.io/badge/Bluetooth%20Core-v5.4%20Vol%203%20Part%20H%20(SMP)-00E5FF.svg)\](\#)  
\[\!\[Security Standard\](https\://img.shields.io/badge/Security-LE%20Secure%20Connections%20(P--256)-7C4DFF.svg)\](\#)  
\[\!\[Audit Score\](https\://img.shields.io/badge/Normative%20Audit-10%2F10%20PASS-00E676.svg)\](\#)  
\[\!\[Zero Dependency\](https\://img.shields.io/badge/CLI-Python%203.8%2B-FF9100.svg)\](\#)

\---

\#\# Overview  
\*\*BLESMPForge Pro\*\* is an enterprise developer tool designed for firmware engineers, automotive digital key architects, medical device manufacturers, and IoT hardware teams implementing the \*\*Bluetooth Low Energy Security Manager Protocol (Bluetooth Core Specification v5.4, Volume 3, Part H)\*\*.

It prevents critical wireless vulnerabilities—such as the KNOB attack (Key Negotiation of Bluetooth CVE-2019-9506), accidental fallback to unauthenticated Just Works pairing, and Crackle-style legacy Temporary Key cracking—by delivering a zero-dependency web studio, a bit-accurate SMP PDU synthesizer, an association model resolver, and an automated 10-point normative zero-trust compliance auditor.

\#\#\# Core Capabilities  
1\. \*\*Interactive Web Studio\*\*: Real-time SMP PDU builder (\`Pairing Request\`, \`Pairing Response\`, \`Pairing Confirm\`, \`Pairing Random\`, \`Pairing Failed\`, \`Security Request\`) and fixed L2CAP CID \`0x0006\` frame encapsulation.  
2\. \*\*AuthReq Bitmask Decoder\*\*: Decodes bonding flags (\`0x01\`), MITM protection (\`Bit 2\`), LE Secure Connections (\`Bit 3\`), Keypress notifications (\`Bit 4\`), and CT2 Cross-Transport derivation (\`Bit 5\`).  
3\. \*\*Association Model Matrix Resolver\*\*: Evaluates Initiator and Responder IO capabilities (\`DisplayOnly\`, \`DisplayYesNo\`, \`KeyboardOnly\`, \`NoInputNoOutput\`, \`KeyboardDisplay\`), MITM requirements, and OOB flags to determine the exact pairing model: \*\*Numeric Comparison\*\*, \*\*Passkey Entry\*\*, \*\*Out of Band (OOB)\*\*, or \*\*Just Works\*\*.  
4\. \*\*10-Point Normative Zero-Trust Auditor\*\*: Validates Fixed L2CAP CID \`0x0006\` routing, normative key size boundaries (7–16 octets), 128-bit minimum key strength enforcement, LE Secure Connections mode enforcement, MITM requirement flags, and 15-code failure taxonomy compliance.  
5\. \*\*Zero-Dependency Python CLI\*\*: Standalone command-line runner for automated CI/CD pipelines, headless testing, and regression suites (\`pdu\`, \`dissect\`, \`audit\`).  
6\. \*\*Embedded C SDK Exporter\*\*: Generates production C authentication callbacks and security structures for Zephyr RTOS and Nordic Semiconductor nRF Connect SDK.

\---

\#\# Directory Structure  
\`\`\`  
product\_301/  
├── README.md                                  \# Complete product guide and quick start  
├── source-code/  
│   ├── index.html                             \# Multi-tab responsive web studio  
│   ├── smp.css                                \# Modern cybersecurity dark theme  
│   ├── smp-engine.js                          \# Core Bluetooth LE SMP protocol engine  
│   ├── smp-auditor.js                         \# 10-point normative compliance rules  
│   └── app.js                                 \# Interactive Studio controller  
├── build/  
│   ├── blesmp-cli.py                          \# Zero-dependency Python 3 CI/CD CLI runner  
│   └── blesmpforge-pro-v1.0.0.zip             \# Packaged distribution archive  
├── documentation/  
│   ├── ARCHITECTURE.md                        \# Protocol stack and framing spec  
│   ├── USER\_GUIDE.md                          \# Studio and CLI user guide  
│   └── MONETIZATION\_AND\_MARKETING\_PLAYBOOK.md \# Pricing, GTM, and market strategy  
├── screenshots/  
│   └── blesmp-studio-preview.svg              \# Vector architecture & UI mock  
└── test\_blesmp.py                             \# Automated 10-point unit verification suite  
\`\`\`

\---

\#\# Automated Verification & Test Coverage  
BLESMPForge Pro is validated against a 10-test automated verification suite (\`test\_blesmp.py\`):  
\- \[x\] Pairing Request (OpCode 0x01) PDU structure and 7-octet length  
\- \[x\] AuthReq bitmask decoding (Bonding, MITM, Secure Connections, CT2)  
\- \[x\] Association Model resolution (DisplayYesNo vs DisplayYesNo \-\> Numeric Comparison)  
\- \[x\] Association Model resolution fallback to Just Works on NoInputNoOutput  
\- \[x\] Pairing Failed (OpCode 0x05) reason code lookup and PDU framing  
\- \[x\] L2CAP CID 0x0006 fixed channel encapsulation  
\- \[x\] 10-point normative compliance audit on standard SC profile (10/10 PASS)  
\- \[x\] Rejection of weak encryption key size (\< 16 octets in Zero-Trust mode)  
\- \[x\] Rejection of non-SC pairing modes (vulnerability to eavesdropping)  
\- \[x\] SMP PDU dissection roundtrip accuracy

\---

\#\# Quick Start  
\`\`\`bash  
\# Synthesize a Pairing Request packet  
python3 build/blesmp-cli.py pdu \--cmd PAIRING\_REQ \--io 1 \--keysize 16 \--mitm 1 \--sc 1

\# Dissect raw SMP PDU hex stream  
python3 build/blesmp-cli.py dissect \--hex 0101000D100707

\# Run 10-point normative compliance audit  
python3 build/blesmp-cli.py audit

\# Execute unit verification tests  
python3 test\_blesmp.py  
\`\`\`  

---
title: 'Methods'
date: 2024-09-01T21:30:30-04:00
draft: true
---
## Theory
For the process of FIPS-Validated printing, there are two primary scenarios. 
### Scenario A: Network Provides the Transport Encryption
The computer and printer both establish an encrypted connection with the network, and the network enables them to communicate with eachother in an encrypted manner. A technical implementation of this might be something like [802.1AE/MACSec](https://www.juniper.net/documentation/us/en/software/junos/security-services/topics/topic-map/understanding_media_access_control_security_qfx_ex.html)
```mermaid
sequenceDiagram
    autonumber
    participant L as Laptop/PC
    participant N as Network
    participant P as Printer
    L->>N: Encrypted
    N->>P: Encrypted
    P->>P: Queueing (encrypted at rest)
    P->>P: Printing
```

### Scenario B: Transport Encryption is Provided by the Printer
The computer establishes an encrypted channel with the printer directly, over an unencrypted network. Technical implementations of this might include: IPP over HTTPS, IPSec, or a proprietary encrypted printing protocol.
```mermaid
sequenceDiagram
    autonumber
    participant L as Laptop/PC
    participant N as Network
    participant P as Printer
    L->>P: Encrypted
    P->>P: Queueing (encrypted at rest)
    P->>P: Printing
```

This website focuses on Scenario B, but the printers listed here would be good candidates for Scenario A, as the printer still needs to be able to securely store the print jobs at rest.
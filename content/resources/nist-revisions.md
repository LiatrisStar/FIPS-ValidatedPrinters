---
title: 'NIST SP 800-171 Revisions'
date: 2024-08-02T17:42:29-04:00
draft: false
---

## (SC) Systems and Communications Protection
### 3.13.8
In Revision 2:
> Implement cryptographic mechanisms to prevent unauthorized disclosure of CUI during transmission unless otherwise protected by alternative physical safeguards.[^1]

In Revision 3 this changes to:
> Implement cryptographic mechanisms to prevent the unauthorized disclosure of CUI during transmission and while in storage.[^2]

Which removes the option to protect CUI with physical protections instead of cryptography. Now, *all* CUI transmissions and storage require cryptography.



[^1]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171r2.pdf
[^2]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171r3.pdf
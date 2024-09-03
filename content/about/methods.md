---
title: 'Methods'
date: 2024-09-01T21:30:30-04:00
draft: true
---
## Theory
More on the underlying theory can be found [here.](../theory)

## Finding Printers
The FIPS-Validated printer search usually starts (well, let's be honest, it *starts* with a Google search for "FIPS-Validated Printers") with [NIAP](https://www.niap-ccevs.org/), the National Information Assurance Partnership which was established by NIST and NSA. NIAP has lists of Commercial Off-The-Shelf (COTS) products that have undergone testing and have been validated to pass a certain level of security requirements. NIAP calls these security requirements "Protection Profiles" 

### Protection Profiles
The NIAP protection profile for printers and MFPs is [Protection Profile for Hardcopy Devices Version 1.0](https://www.niap-ccevs.org/protectionprofiles/317) (PP_HCD_V1.0) which will be sunset on **10/23/2024**. 
The successor to PP_HCD_V1.0, is [collaborative Protection Profile for Hardcopy Devices Version 1.0E](https://www.niap-ccevs.org/protectionprofiles/483) (CPP_HCD_V1.0E) which will take effect on **10/23/2024** (Hard cutover).

Neither PP_HCD_V1.0 nor CPP_HCD_V1.0E mandates FIPS modules used for cryptography to be validated. 
The NIAP list of printers/MFPs under the "Hardcopy" protection profiles is not authoritative for all FIPS-Validated printers (especially since the profiles don't require FIPS valdiation) but this list is still a good list of pre-vetted products which are concious about security. There seems to be a high correlation between printers on the NIAP's list, and printers which have FIPS-Validated modules installed.

### Determining Validations
I choose a printer from the NIAP list and click on the link for more details. The sidebar has documents related to the certification of the printer including the CC Security Target, the CC Certificate, and the Administrative Guides (specifically the ones that cover secure installation and administration - not always present). 

In each of these documents, search for the following terms:
* FIPS
* CMVP
* CAVP
* Module

For each result, see if there are notes about a CAVP or CMVP certificate number. The CMVP number is the ideal result, but often CAVP can be used as well.

### CAVP
The Cryptographic Algorithm Validation Program ensures the algorithms implemented by a cryptographic module are mathmatically and functionally correct - they ensure the hashing and encrypting is performed properly when the appropriate function is used. The Cryptographic Module Validation Program (CMVP) futhers this testing (and requires CAVP as a prerequisite) by ensuing that the necessary security funtions are used at the appropriate time. Thus, just having a CAVP certificate number does not meet the needs of CMMC and NIST SP 800-171 compliance.

### CMVP
With the CAVP certificate we can often look up the same manufacturer/module implementation name on the [CMVP search tool](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/validated-modules/Search) and find the module that matches the version listed in the documentation and/or the CAVP certificate.

### Ensuring Encryption
Now that we know the module(s) are validated, we need to ensure that the validated module is actually used for print jobs sent to and stored on the printer. This involves reading through the documentation mentioned in [#CAVP](#cavp) as well as any other documentation published by the manufacturer or lab.
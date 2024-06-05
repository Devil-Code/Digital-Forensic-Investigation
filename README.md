# Digital Investigation Report: Saturn University Harassment Case

## Overview

This document details the digital forensic investigation conducted by me as a part of Saturn University's IT Department in response to a complaint by Ignis Lee, a Mathematics Department teacher. Ignis Lee reported receiving harassing emails and suspected a student from his Math 199 class. This report outlines the steps taken, evidence found, and conclusions drawn to identify the suspect. 

*Note: This incidence is fake and intended for educational purposes only. Unauthorized access, distribution, or disclosure is very much legal.*

## Table of Contents
- [Investigation Objectives](#investigation-objectives)
- [Tools Used](#tools-used)
- [Examination Criteria](#examination-criteria)
- [Steps Taken](#steps-taken)
- [Results](#results)
- [Forensic Questions and Answers](#forensic-questions-and-answers)
- [Conclusion](#conclusion)
- [Recommendations](#recommendations)
- [Certifications](#certification)
- [Appendices](#appendices)
- [Contact Information](#contact-information)

## Investigation Objectives

1. **Examine the packet capture (pcap) file containing packet logs.**
2. **Identify harassing messages.**
3. **Determine the IP address and MAC address of the suspect.**
4. **Identify the student who sent the harassing messages.**

## Tools Used

- **Kali Linux OS**
- **MD5 Checksum**: [Online Tool](https://emn178.github.io/online-tools/md5_checksum.html)
- **Wireshark**: Wireshark Foundation

## Examination Criteria

1. **Describe the evidence found during the investigation.**
2. **Detect activities of the suspect to gather more information.**
3. **Identify the suspect involved in the harassment.

## Steps Taken

1. **Creation of a forensic copy of the .pcap file**:
   - Ensured the file remained untampered during the investigation.

2. **Verification of the MD5 checksum**:
   - Verified against the chain of custody with the result `785b9b7260eb061d4f79c8074432bec8`, confirming the file's integrity.

3. **Opening the .pcap file in Wireshark**:
   - Provided a workspace for detailed packet analysis.

4. **Filtering packets containing "anonymouse"**:
   - Command used: `http.host contains "anonymouse"`
   - Identified the harassing message in the HTTP POST request.

5. **Investigation of packet details**:
   - Found the IP addresses and MAC addresses:
     - Source IP: `192.168.137.218`
     - Destination IP: `193.200.150.82`
     - Source MAC: `1c:1b:b5:6d:51:0f`
     - Destination MAC: `0a:5b:d6:62:44:d1`

6. **Filtering packets to find cookies related to the suspect's MAC address**:
   - Command used: `eth.addr == 1c:1b:b5:6d:51:0f && frame contains "Cookie"`
   - Identified the suspect's name from packet `2647`.

7. **Further filtering to gather timestamps and OS information**:
   - Command used: `eth.addr == 1c:1b:b5:6d:51:0f && http`
   - Tracked the suspect's activities across different timestamps:
     - Accessed `kgbook.com` on 28th February 2022 at 19:24:22 GMT.
     - Accessed `anonymouse.com` on 28th February 2022 at 19:25:04 GMT.
     - Re-accessed `kgbook.com` on 28th February 2022 at 19:25:50 GMT.
   - Identified the suspect's OS: Windows NT system Version 10.0 (64-bit).

8. **Documentation of evidence**:
   - Ensured the chain of custody for all collected evidence.

## Results

### MD5 Checksum
- `785b9b7260eb061d4f79c8074432bec8`

### Harassing Email
- **Frame Number**: 3913
- **Text**: Harassing message found.

### MAC Address
- **Source MAC**: `1c:1b:b5:6d:51:0f`
- **Destination MAC**: `0a:5b:d6:62:44:d1`

### Suspect Information
- **Name**: Johnson Crossby (identified in frame 2647)

### Timestamps
- **Kgbook Access**: Frame 2648 at 19:24:22 GMT
- **Anonymouse Access**: Frame 3925 at 19:25:04 GMT
- **Kgbook Access After**: Frame 7554 at 19:25:50 GMT

### Operating System
- **Windows NT system Version 10.0 (64-bit)**

## Forensic Questions and Answers

1. **IP Address accessing anonymouse.com**:
   - `192.168.137.218`

2. **Harassing comments posted?**:
   - Yes, confirmed by the harassing email screenshot.

3. **HTTP POST containing harassment message**:
   - Frame 3913

4. **MAC address of harassment message**:
   - `1c:1b:b5:6d:51:0f`

5. **Effectiveness of IP vs. MAC address**:
   - Both are crucial: IP for tracking source/destination, MAC for identifying specific devices.

6. **Remembering users on websites**:
   - Cookies, browser fingerprinting, session tokens.

7. **Suspect**:
   - Johnson Crossby (frame 2647)

8. **Anonymouse.com usage timestamp**:
   - 28th February 2022 at 19:25:04 GMT (frame 3925)

9. **Skill level of the abuser**:
   - Low: Poor operational security practices.

10. **Identification if using another anonymous email site**:
    - HTTPS encryption makes it difficult with the same method, but IP tracking remains possible.

11. **Future relevance of email forensics**:
    - Likely relevant but will require updated technologies and tools.

## Conclusion

Multiple pieces of evidence confirm Johnson Crossby as the sender of the harassing emails to Ignis Lee:

1. **Packet 3913**: Linked to Johnson Crossby's IP.
2. **Harassing Message**: Sent to Ignis Lee's email.
3. **MAC Address**: Matched across different packets.
4. **Cookies**: Contained Johnson Crossby's name.
5. **Timestamp Analysis**: Consistent activity pattern.
6. **OS Identification**: Windows NT 10.0 (64-bit).

## Recommendations

Further steps include verifying with CCTV footage and witness testimonies to solidify the evidence against Johnson Crossby.

## Certification

I hereby certify that the work presented above was personally performed by me and the opinions and conclusions stated are my own based upon the work that I performed.

**Pritesh Bharat Gandhi**
Signature

## Appendices
- **Appendix A**: Packet Logs
- **Appendix B**: Screenshots of Key Findings
- **Appendix C**: Report of the Complete Investigation

## Contact Information

For any inquiries or issues, please contact:
- **Pritesh Gandhi**
- **Email**: pgandhi1412@gmail.com
- **GitHub**: [GitHubProfile](https://github.com/Devil-Code)

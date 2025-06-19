# Calculates and Verififies LIS01 Low-Level Protocol Frame Checksums



![image-20250314201901833](./README.assets/image-20250314201901833.png) 



The *LIS1-A / ASTM E1381 Frame Checksum Calculator can be used to calculate or verify the checksum of an LIS01 frame.

The LIS02 specification describes the structure and content of messages sent between an instrument and a Laboratory Information System (LIS). These messages are used to send orders, receive results, and exchange information with each other. They can be exchanged in network shared folders, serial communication, and TCP/IP protocols.

Below is an LIS02 Message containing four records: Header (H), Patient (P), Order (O), and End of Message (L).

```
H|\^&|||Mini LIS||||||||LIS2-A|20210309142633<CR>
P|1|PID123456||NID123456|Brown^Bobby^B|White|196501020304|M<CR>
O|1|SID305||ABO|N|20210309142633|||||N||||CENTBLOOD<CR>
L|1|N<CR>
```

LIS01 is a specification for a low-level protocol that enables the exchange of LIS02 messages via serial communication and TCP/IP. The protocol is implemented to allow bidirectional communication, where each system takes turns sending and receiving messages. LIS02 messages are sent one line (called a record) at a time. The LIS01 protocol is not limited to just LIS02 messages; it can send any text-based message that its protocol can support. For LIS02 content, an LIS01 message is defined as one LIS02 record.

Each LIS02 record is sent in an LIS01 frame that starts with an \<STX> and ends with a \<CR>\<LF> sequence. The message (record) sits between the \<STX> and the \<ETX>. Each frame contains a checksum, which is used to validate that the message has not been corrupted in transit. The checksum lies between the  \<ETX> and \<CR>\<LF> sequence.

```
<STX><LIS02 Record><ETX><Two digit hexidecimal Checksum><CR><LF>
```

## References

- [LIS01A2E](https://clsi.org/standards/products/automation-and-informatics/documents/lis01/), Specification for Low-Level Protocol to Transfer Messages Between Clinical Laboratory Instruments and Computer Systems
- [LIS02A2E](https://clsi.org/standards/products/automation-and-informatics/documents/lis02), Specification for Transferring Information Between Clinical Laboratory Instruments and Information Systems
- Hendrickson Group - [Calculating the checksum of an ASTM document](https://www.hendricksongroup.com/code_003.aspx) 
























hcxpcapngtool -o optfile.22000 capturefile-01.cap                                      
hcxpcapngtool 6.3.4-49-g5d85a10 reading from capturefile-01.cap...

summary capture file
--------------------
file name................................: capturefile-01.cap
version (pcap/cap).......................: 2.4 (very basic format without any additional information)
timestamp minimum (timestamp)............: 02.09.2024 23:22:40 (1725319360)
timestamp maximum (timestamp)............: 02.09.2024 23:25:03 (1725319503)
duration of the dump tool (minutes)......: 2
used capture interfaces..................: 1
link layer header type...................: DLT_IEEE802_11 (105) very basic format without any additional information about the quality
endianness (capture system)..............: little endian
packets inside...........................: 21740
ESSID (total unique).....................: 1
BEACON (total)...........................: 1
BEACON on 2.4 GHz channel (from IE_TAG)..: 13 
ACTION (total)...........................: 14
PROBEREQUEST (directed)..................: 3
PROBERESPONSE (total)....................: 21
DEAUTHENTICATION (total).................: 15716
AUTHENTICATION (total)...................: 4
AUTHENTICATION (OPEN SYSTEM).............: 4
ASSOCIATIONREQUEST (total)...............: 2
ASSOCIATIONREQUEST (PSK).................: 2
WPA encrypted............................: 3124
IPv6 (total).............................: 1
ICMPv6...................................: 1
EAPOL messages (total)...................: 7
EAPOL RSN messages.......................: 7
EAPOLTIME gap (measured maximum msec)....: 21
EAPOL ANONCE error corrections (NC)......: not detected
EAPOL M1 messages (total)................: 2
EAPOL M2 messages (total)................: 2
EAPOL M3 messages (total)................: 2
EAPOL M4 messages (total)................: 1
EAPOL M4 messages (zeroed NONCE).........: 1
EAPOL pairs (total)......................: 4
EAPOL pairs (best).......................: 2
EAPOL pairs written to 22000 hash file...: 2 (RC checked)
EAPOL M12E2 (challenge)..................: 1
EAPOL M32E2 (authorized).................: 1
RSN PMKID (useless)......................: 2

Information: limited dump file format detected!
This file format is a very basic format to save captured network data.
It is recommended to use PCAP Next Generation dump file format (or pcapng for short) instead. The PCAP Next Generation dump file format is an attempt to overcome the limitations of the currently widely used (but very limited) libpcap (cap, pcap) format.
https://www.wireshark.org/docs/wsug_html_chunked/AppFiles.html#ChAppFilesCaptureFilesSection
https://github.com/pcapng/pcapng

Information: radiotap header is missing!
Radiotap is a de facto standard for 802.11 frame injection and reception. The radiotap header format is a mechanism to supply additional information about frames, from the driver to userspace applications.
https://www.radiotap.org/

Warning: excessive number of deauthentication/disassociation frames detected!
That can cause that an ACCESS POINT change channel, reset EAPOL TIMER, renew ANONCE and set PMKID to zero. This could prevent to calculate a valid EAPOL MESSAGE PAIR, to get a valid PMKID or to decrypt the traffic.

Information: missing frames!
This dump file does not contain undirected proberequest frames.
An undirected proberequest may contain information about the PSK. It always happens if the capture file was cleaned or it could happen if filter options are used during capturing.
That makes it hard to recover the PSK.

Information: missing frames!
This dump file does not contain enough EAPOL M1 frames.
It always happens if the capture file was cleaned or it could happen if filter options are used during capturing.
That makes it impossible to calculate nonce-error-correction values.


session summary
---------------
processed cap files...................: 1

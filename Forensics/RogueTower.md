## DESCRIPTION
A suspicious cell tower has been detected in the network. Analyze the captured network traffic to identify the rogue tower, find the compromised device, and recover the exfiltrated flag.

HINTS:
- Look for unauthorized test network broadcasts on UDP port 55000
- Find the device that connected to the rogue tower by checking HTTP User-Agent headers
- The encryption key is derived from the victim device's IMSI
- The exfiltrated data is split across multiple HTTP POST requests

## MY PROCESS
We are given a `.pcap` file for this one.

Basing off on the hints given, we will start by looking for the unauthorized test network broadcast and the device that is connected to it.
<img width="1365" height="721" alt="image" src="https://github.com/user-attachments/assets/e40b9343-1462-4e1b-b41c-02ec2a8fe56e" />

We got the device that is connected to the rogue tower! Now we will get the IMSI of the device and the exfiltrated data.

Since we know the CELL ID of the device, we will use that to locate it's IMSI:

<img width="906" height="647" alt="image" src="https://github.com/user-attachments/assets/1321c933-f49e-4463-bf91-41fbc33708c9" />

We found the IMSI and now the exfiltrated data.

Connecting the exfiltrated data together in the HTTP POST, we will have the output of:
`SF5aXHVlc01KB15GBW5WBVRbZkcGRgZEZwBYAwBXUQFbSg==`

Decoding the base64 string results to this:

<img width="1112" height="132" alt="image" src="https://github.com/user-attachments/assets/ee7bebf3-8c4d-40f1-85de-c240e40a6f19" />

Now looking back at the hint `The encryption key is derived from the victim device's IMSI`, we can identify that this was XOR encrypted with the device's IMSI!

This is a process of trial and error since we do not specifically know if ALL digits are used for XOR or a number of specific digits. But after doing trial and error, we the XOR key was the last 8 digit of the device's IMSI.

<img width="1093" height="362" alt="image" src="https://github.com/user-attachments/assets/ef86996b-fcdf-4de4-8e5f-1f8f306912a8" />

Flag found!

FLAG: `picoCTF{r0gu3_c3ll_t0w3r_7a06fd7c}`

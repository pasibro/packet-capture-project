# Packet Capture & Traffic Analysis

## Tool
Wireshark on Kali Linux, capturing on eth0 (VMnet1/Host-only)

## Capture Summary
- 431 total packets captured, 228 matched 'icmp' filter
- Traffic: ICMP echo request/reply between Kali (192.168.153.130) 
  and Metasploitable2 (192.168.153.129)

## Layer Analysis (Packet #333)
| Layer | Field | Value |
|---|---|---|
| Ethernet (L2) | Src/Dst MAC | VMware virtual NICs (00:0c:29 prefix) |
| IP (L3) | Src/Dst IP | 192.168.153.129 → .130 |
| IP (L3) | TTL | 64 |
| ICMP | Type/Code | 0/0 (Echo Reply) |
| ICMP | Identifier | 0x3442 |
| ICMP | Sequence | 116 |

## Key Learning
- Encapsulation: Ethernet frame wraps IP packet wraps ICMP message
- Wireshark auto-correlates request/reply pairs via Identifier + Sequence Number
- This ID+Seq matching is exactly how `ping` calculates round-trip time

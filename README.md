# IOC IP Sets — FireHOL Mirror

Sync automat din [iplists.firehol.org](https://iplists.firehol.org).
**Ultima actualizare:** 2026-08-11 16:10 UTC

## Structură

| Director | Conținut |
|----------|----------|
| `level/` | firehol_level1–4 (threat levels agregate) |
| `bots/` | Botnets, brute-force, spam |
| `scanners/` | Port scanners, SSH/FTP brute-force |
| `proxies/` | Open proxies, TOR exit nodes |
| `malware/` | Malware C2, IPs malițioase |
| `ransomware/` | Ransomware IPs (Feodo, abuse.ch) |
| `coinbl/` | Cryptominer blocklists |

## Format

- `.netset` — CIDR ranges (ex: `1.2.3.0/24`)
- `.ipset` — IP individuale (ex: `1.2.3.4`)

## Sursă

Toate listele provin din [firehol/blocklist-ipsets](https://github.com/firehol/blocklist-ipsets).

## Utilizare în Microsoft Defender (KQL)

```kql
let blocklist = externaldata(ip: string)
    [@"https://raw.githubusercontent.com/ClaudiusDecimius/ioc-ipsets/main/level/firehol_level1.netset"]
    with (format="txt", ignoreFirstRecord=false);
DeviceNetworkEvents
| where RemoteIP in (blocklist)
```

# Malshare SHA256 — Cumulative Feed

Sync automat din [malshare.com](https://malshare.com).
**Ultima actualizare:** 2026-05-07 08:30 UTC
**Total hash-uri:** 52

## Fișier

| Fișier | Conținut |
|--------|----------|
| `hash.txt` | Toate SHA256-urile colectate, fără duplicate, sortat |

## Format

Un SHA256 per linie (64 caractere hex). La fiecare rulare se adaugă
doar hash-urile noi față de versiunea anterioară.

## Utilizare în Microsoft Defender (KQL)

```kql
let sha256_feed = externaldata(hash: string)
    [@"https://raw.githubusercontent.com/ClaudiusDecimius/ioc-ipsets/main/hashes/malshare/hash.txt"]
    with (format="txt", ignoreFirstRecord=false);
DeviceFileEvents
| where SHA256 in (sha256_feed)
| project Timestamp, DeviceName, FileName, FolderPath, SHA256
```

## Sursă

[malshare.com/daily/malshare.current.all.txt](https://malshare.com/daily/malshare.current.all.txt)
Format original: `MD5\tSHA1\tSHA256` — se extrage doar coloana SHA256.

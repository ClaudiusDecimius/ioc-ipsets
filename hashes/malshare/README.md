# Malshare SHA256 — Daily Feed

Sync automat din [malshare.com](https://malshare.com).
**Ultima actualizare:** 2026-04-28 06:19 UTC

## Fișiere

| Fișier | Conținut |
|--------|----------|
| `latest.txt` | SHA256 din ziua curentă (34 hash-uri) |
| `YYYY-MM-DD.txt` | Archive zilnice |

## Format

Un SHA256 per linie (64 caractere hex), deduplicat și sortat.

## Utilizare în Microsoft Defender (KQL)

```kql
let sha256_feed = externaldata(hash: string)
    [@"https://raw.githubusercontent.com/ClaudiusDecimius/ioc-ipsets/main/hashes/malshare/latest.txt"]
    with (format="txt", ignoreFirstRecord=false);
DeviceFileEvents
| where SHA256 in (sha256_feed)
| project Timestamp, DeviceName, FileName, FolderPath, SHA256
```

## Sursă

[malshare.com/daily/malshare.current.all.txt](https://malshare.com/daily/malshare.current.all.txt)
Format original: `MD5\tSHA1\tSHA256` — se extrage doar coloana SHA256.

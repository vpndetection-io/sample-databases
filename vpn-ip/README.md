# VPN IP

IP ranges observed as VPN infrastructure.

| Field | Value |
| --- | --- |
| ID | `vpn_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 14,895,525 entries, 103 MB as CSV and 86.8 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=VPN+IP+Database+evaluation&products=VPN+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip) |
| Docs | [docs.vpndetection.io/database/vpn-ip/vpn-ip](https://docs.vpndetection.io/database/vpn-ip/vpn-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip) |

## Files

- [`vpn_ip_v1.sample.csv`](vpn_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`vpn_ip_v1.sample.csv.gz`](vpn_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`vpn_ip_v1.sample.mmdb`](vpn_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

IP ranges observed as VPN infrastructure.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.7.231` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.7.231` |
| `provider` | `string` | Commercial VPN provider's unique ID. | `psiphon` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `low` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-13` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Commercial VPN provider's unique ID. | `psiphon` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `low` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-13` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=VPN+IP+Database+evaluation&products=VPN+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o vpn_ip_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=vpn_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o vpn_ip_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=vpn_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/vpn-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

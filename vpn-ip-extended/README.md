# VPN IP Extended

VPN IP ranges with provider attribution, confidence and detection method.

| Field | Value |
| --- | --- |
| ID | `vpn_ip_extended_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 16,445,980 entries, 118 MB as CSV and 145 MB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=VPN+IP+Extended+Database+evaluation&products=VPN+IP+Extended+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip-extended) |
| Docs | [docs.vpndetection.io/database/vpn-ip/vpn-ip-extended](https://docs.vpndetection.io/database/vpn-ip/vpn-ip-extended?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip-extended) |

## Files

- [`vpn_ip_extended_v1.sample.csv`](vpn_ip_extended_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`vpn_ip_extended_v1.sample.csv.gz`](vpn_ip_extended_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`vpn_ip_extended_v1.sample.mmdb`](vpn_ip_extended_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

VPN IP ranges with provider attribution, confidence and detection method.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.7.231` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.7.231` |
| `provider` | `string` | Commercial VPN provider's unique ID. Empty when the range is confirmed VPN infrastructure we have not yet attributed to a named operator. | `windscribe` |
| `method` | `string` | How this range was established. Values are listed below. | `scan` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `low` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-20` |

`method` is one of:

| Value | Description |
| --- | --- |
| `scan` | We spoke the VPN protocol to the address ourselves and got a valid server response. |
| `scrape` | The operator published the address through its own API, client or configuration. |
| `registry` | Public registration or naming records attribute the address to the operator. |
| `infer` | The address was extrapolated from confirmed neighbors in the same block. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Commercial VPN provider's unique ID. Empty when the range is confirmed VPN infrastructure we have not yet attributed to a named operator. | `windscribe` |
| `method` | `string` | How this range was established. Values are listed below. | `scan` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `low` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-20` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=VPN+IP+Extended+Database+evaluation&products=VPN+IP+Extended+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip-extended) to test the whole file first. With a licensed API key:

```bash
curl -L -o vpn_ip_extended_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=vpn_ip_extended_v1&format=csvgz&apikey=$APIKEY"
curl -L -o vpn_ip_extended_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=vpn_ip_extended_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/vpn-ip-extended?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=vpn-ip-extended), cut from the latest build.

Back to [all VPNDetection sample databases](../).

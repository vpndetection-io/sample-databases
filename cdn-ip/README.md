# CDN IP

IP ranges operated by content delivery networks.

| Field | Value |
| --- | --- |
| ID | `cdn_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 153,406 entries, 960 KB as CSV and 1.12 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=CDN+IP+Database+evaluation&products=CDN+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=cdn-ip) |
| Docs | [docs.vpndetection.io/database/cdn-ip/cdn-ip](https://docs.vpndetection.io/database/cdn-ip/cdn-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=cdn-ip) |

## Files

- [`cdn_ip_v1.sample.csv`](cdn_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`cdn_ip_v1.sample.csv.gz`](cdn_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`cdn_ip_v1.sample.mmdb`](cdn_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

IP ranges operated by content delivery networks.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `provider` | `string` | CDN provider's unique ID. | `cloudflare` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-17` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | CDN provider's unique ID. | `cloudflare` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-17` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=CDN+IP+Database+evaluation&products=CDN+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=cdn-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o cdn_ip_v1.csv.gz 'https://api.vpndetection.io/api/v1/database/download?id=cdn_ip_v1&format=csvgz&apikey=$APIKEY'
curl -L -o cdn_ip_v1.mmdb 'https://api.vpndetection.io/api/v1/database/download?id=cdn_ip_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://vpndetection.io/databases/cdn-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=cdn-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

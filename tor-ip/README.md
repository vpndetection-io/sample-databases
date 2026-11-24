# Tor IP

Tor node IP ranges.

| Field | Value |
| --- | --- |
| ID | `tor_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 13,509 entries, 110 KB as CSV and 914 KB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.vpndetection.io/database/tor-ip](https://docs.vpndetection.io/database/tor-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip) |

## Files

- [`tor_ip_v1.sample.csv`](tor_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`tor_ip_v1.sample.csv.gz`](tor_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`tor_ip_v1.sample.mmdb`](tor_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Tor node IP ranges.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit VPNDetection with a link to [vpndetection.io](https://vpndetection.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the Tor node IP range. | `1.34.44.234` |
| `end_ip` | `ipaddress` | End IP of the Tor node IP range. | `1.34.44.234` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-24` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-24` |

## The full database

Tor IP is an Open database, free under CC BY-SA 4.0 with a VPNDetection account: [sign up](https://vpndetection.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), then with your API key:

```bash
curl -L -o tor_ip_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=tor_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o tor_ip_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=tor_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/tor-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

# Relay IP

IP ranges of privacy relays, such as iCloud Private Relay, and of enterprise web gateways, such as Zscaler.

| Field | Value |
| --- | --- |
| ID | `relay_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 185,612 entries, 1.20 MB as CSV and 1.15 MB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.vpndetection.io/database/relay-ip/relay-ip](https://docs.vpndetection.io/database/relay-ip/relay-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip) |

## Files

- [`relay_ip_v1.sample.csv`](relay_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`relay_ip_v1.sample.csv.gz`](relay_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`relay_ip_v1.sample.mmdb`](relay_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

IP ranges of privacy relays, such as iCloud Private Relay, and of enterprise web gateways, such as Zscaler. A gateway carries a company's staff traffic at work, so a rule that blocks Relay IP blocks them too.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit VPNDetection with a link to [vpndetection.io](https://vpndetection.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `3.0.6.66` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `3.0.6.66` |
| `provider` | `string` | Relay/proxy provider's unique ID. | `cisco_secure_access` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-20` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Relay/proxy provider's unique ID. | `cisco_secure_access` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-20` |

## The full database

Relay IP is an Open database, free under CC BY-SA 4.0 with a VPNDetection account: [sign up](https://vpndetection.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), then with your API key:

```bash
curl -L -o relay_ip_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=relay_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o relay_ip_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=relay_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/relay-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

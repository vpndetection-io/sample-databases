# Hosting IP

IP ranges belonging to hosting and cloud providers.

| Field | Value |
| --- | --- |
| ID | `hosting_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 483,920 entries, 3.29 MB as CSV and 5.68 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Hosting+IP+Database+evaluation&products=Hosting+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=hosting-ip) |
| Docs | [docs.vpndetection.io/database/hosting-ip/hosting-ip](https://docs.vpndetection.io/database/hosting-ip/hosting-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=hosting-ip) |

## Files

- [`hosting_ip_v1.sample.csv`](hosting_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`hosting_ip_v1.sample.csv.gz`](hosting_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`hosting_ip_v1.sample.mmdb`](hosting_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

IP ranges belonging to hosting and cloud providers.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `provider` | `string` | Hosting provider's unique ID. | `aws` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-16` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Hosting provider's unique ID. | `aws` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-16` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Hosting+IP+Database+evaluation&products=Hosting+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=hosting-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o hosting_ip_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=hosting_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o hosting_ip_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=hosting_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/hosting-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=hosting-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

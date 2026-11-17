# Datacenter Proxy IP 1d

Datacenter-hosted proxy IPs seen in the last 24 hours, with provider attribution.

| Field | Value |
| --- | --- |
| ID | `dcproxy_ip_1d_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 682,213 entries, 1.88 MB as CSV and 693 KB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Datacenter+Proxy+IP+Database+evaluation&products=Datacenter+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-1d) |
| Docs | [docs.vpndetection.io/database/dcproxy-ip/dcproxy-ip-1d](https://docs.vpndetection.io/database/dcproxy-ip/dcproxy-ip-1d?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-1d) |

## Files

- [`dcproxy_ip_1d_v1.sample.csv`](dcproxy_ip_1d_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`dcproxy_ip_1d_v1.sample.csv.gz`](dcproxy_ip_1d_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`dcproxy_ip_1d_v1.sample.mmdb`](dcproxy_ip_1d_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Datacenter-hosted proxy IPs seen in the last 24 hours, with provider attribution.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | IP address a datacenter proxy service sells or runs on. | `1.0.168.65` |
| `provider` | `string` | Datacenter proxy provider's unique ID. | `floppydata` |
| `first_seen` | `date` | First time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `last_seen` | `date` | Last time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `hits` | `integer` | Sightings within this window: one per time it was seen as an exit, or one a day as an address of a proxy server or of a proxy company's own range. | `1` |
| `hits_days_pct` | `float` | Percent of days within this window on which this IP was seen as a datacenter proxy address. | `100` |
| `providers_num` | `integer` | Number of distinct providers attributing this IP within this window. | `1` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Datacenter proxy provider's unique ID. | `floppydata` |
| `first_seen` | `date` | First time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `last_seen` | `date` | Last time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `hits` | `integer` | Sightings within this window: one per time it was seen as an exit, or one a day as an address of a proxy server or of a proxy company's own range. | `1` |
| `hits_days_pct` | `float` | Percent of days within this window on which this IP was seen as a datacenter proxy address. | `100` |
| `providers_num` | `integer` | Number of distinct providers attributing this IP within this window. | `1` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Datacenter+Proxy+IP+Database+evaluation&products=Datacenter+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-1d) to test the whole file first. With a licensed API key:

```bash
curl -L -o dcproxy_ip_1d_v1.csv.gz 'https://api.vpndetection.io/api/v1/database/download?id=dcproxy_ip_1d_v1&format=csvgz&apikey=$APIKEY'
curl -L -o dcproxy_ip_1d_v1.mmdb 'https://api.vpndetection.io/api/v1/database/download?id=dcproxy_ip_1d_v1&format=mmdb&apikey=$APIKEY'
```

It's part of [Datacenter Proxy IP](https://vpndetection.io/databases/datacenter-proxy-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-1d) on vpndetection.io.

Back to [all VPNDetection sample databases](../).

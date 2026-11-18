# Public Proxy IP 1d

Addresses where public proxies listened or their traffic exited in the last 24 hours, each flagged entry, exit or both.

| Field | Value |
| --- | --- |
| ID | `pubproxy_ip_1d_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 16,501 entries, 118 KB as CSV and 877 KB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Public+Proxy+IP+Database+evaluation&products=Public+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=pubproxy-ip-1d) |
| Docs | [docs.vpndetection.io/database/pubproxy-ip/pubproxy-ip-1d](https://docs.vpndetection.io/database/pubproxy-ip/pubproxy-ip-1d?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=pubproxy-ip-1d) |

## Files

- [`pubproxy_ip_1d_v1.sample.csv`](pubproxy_ip_1d_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`pubproxy_ip_1d_v1.sample.csv.gz`](pubproxy_ip_1d_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`pubproxy_ip_1d_v1.sample.mmdb`](pubproxy_ip_1d_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

A public proxy is one anyone can connect through: an HTTP proxy, an HTTP proxy that also tunnels HTTPS connections, or a SOCKS4 or SOCKS5 proxy. Each row is one address seen at either end of a public proxy in the last 24 hours: `exit` if a proxy's traffic left from it, `entry` if a proxy listens on it, or both.

A request through a proxy arrives from the address its traffic leaves from, which is often not the one the proxy listens on, and one proxy can leave from several addresses over time. Each of them is an exit row of its own, so the file is a blocklist as it is.

Use it to spot a signup, login or checkout that arrives through a proxy anyone can use rather than from the person's own connection.

`protocols` are those of the proxies at either end. `num_ports` counts the ports a proxy listens on at the address and `num_proxies` the proxies whose traffic left from it, so each is 0 on a row that is only the other end. `last_usable` is the last day a request through a proxy at the address was answered, empty when none was, and `last_seen` the last day the address was seen at all. An entry with `num_ports` 0 and no `protocols` ran a public proxy whose port isn't known.

The MMDB holds the same rows, a record per address.

Public Proxy IP comes in six windows, 1, 7, 14, 30, 60 and 90 days. A shorter one leaves out the addresses not seen lately.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | IP address a public proxy listened on, or sent its traffic out from, within the last 24 hours. | `1.0.171.213` |
| `exit` | `boolean` | Whether a public proxy's traffic left from this address within the last 24 hours: the address a request through the proxy arrives from. | `true` |
| `entry` | `boolean` | Whether a public proxy listened on this address within the last 24 hours. | `true` |
| `protocols` | `string` | Comma-joined protocols of the proxies listening on or leaving from this address; empty when only the address is known. Values are listed below. | `http,https` |
| `num_ports` | `integer` | Number of distinct ports a public proxy listened on at this address; 0 when it is only an exit, or its port is not known. | `1` |
| `num_proxies` | `integer` | Number of distinct public proxies whose traffic left from this address; 0 when it is only an entry. | `2` |
| `country` | `string` | ISO 3166-1 alpha-2 country code of the IP address. | `TH` |
| `last_seen` | `date` | Last time within the last 24 hours this address was seen at either end of a public proxy. | `2026-11-16` |
| `last_usable` | `date` | Last time within the last 24 hours a request through a public proxy was answered with this address at either end; empty when none was. | `2026-11-16` |

`protocols` is one of:

| Value | Description |
| --- | --- |
| `http` | An HTTP proxy that forwards plain HTTP requests. |
| `https` | An HTTP proxy that also tunnels HTTPS connections (CONNECT). |
| `socks4` | A SOCKS4 proxy. |
| `socks5` | A SOCKS5 proxy. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `exit` | `boolean` | Whether a public proxy's traffic left from this address within the last 24 hours: the address a request through the proxy arrives from ("true" or "false"). | `true` |
| `entry` | `boolean` | Whether a public proxy listened on this address within the last 24 hours ("true" or "false"). | `true` |
| `protocols` | `string` | Comma-joined protocols of the proxies listening on or leaving from this address; empty when only the address is known. Values are listed below. | `http,https` |
| `num_ports` | `integer` | Number of distinct ports a public proxy listened on at this address; 0 when it is only an exit, or its port is not known. | `1` |
| `num_proxies` | `integer` | Number of distinct public proxies whose traffic left from this address; 0 when it is only an entry. | `2` |
| `country` | `string` | ISO 3166-1 alpha-2 country code of the IP address. | `TH` |
| `last_seen` | `date` | Last time within the last 24 hours this address was seen at either end of a public proxy. | `2026-11-16` |
| `last_usable` | `date` | Last time within the last 24 hours a request through a public proxy was answered with this address at either end; empty when none was. | `2026-11-16` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Public+Proxy+IP+Database+evaluation&products=Public+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=pubproxy-ip-1d) to test the whole file first. With a licensed API key:

```bash
curl -L -o pubproxy_ip_1d_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=pubproxy_ip_1d_v1&format=csvgz&apikey=$APIKEY"
curl -L -o pubproxy_ip_1d_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=pubproxy_ip_1d_v1&format=mmdb&apikey=$APIKEY"
```

It's part of [Public Proxy IP](https://vpndetection.io/databases/public-proxy-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=pubproxy-ip-1d) on vpndetection.io.

Back to [all VPNDetection sample databases](../).

# [<img src="https://s3.vpndetection.io/vpndetection-public/brand/mark.svg" alt="VPNDetection" height="28"/>](https://vpndetection.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases) VPNDetection Sample Databases

100 real rows of every VPNDetection database that has a sample, in the formats the full databases ship in, with every field documented. Each sample is cut from that database's own build, so its rows, columns and quoting are the full file's.

## Databases

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [VPN IP](vpn-ip/) | IP ranges observed as VPN infrastructure. | CSV, MMDB | Daily |
| [VPN IP Extended](vpn-ip-extended/) | VPN IP ranges with provider attribution, confidence and detection method. | CSV, MMDB | Daily |
| [Hosting IP](hosting-ip/) | IP ranges belonging to hosting and cloud providers. | CSV, MMDB | Daily |
| [Tor IP](tor-ip/) (Open) | Tor node IP ranges. | CSV, MMDB | Daily |
| [Relay IP](relay-ip/) (Open) | IP ranges of privacy relays, such as iCloud Private Relay, and of enterprise web gateways, such as Zscaler. | CSV, MMDB | Daily |
| [CDN IP](cdn-ip/) | IP ranges operated by content delivery networks. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 1d](dcproxy-ip-1d/) | Datacenter-hosted proxy IPs seen in the last 24 hours, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 7d](dcproxy-ip-7d/) | Datacenter-hosted proxy IPs seen in the last 7 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 14d](dcproxy-ip-14d/) | Datacenter-hosted proxy IPs seen in the last 14 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 30d](dcproxy-ip-30d/) | Datacenter-hosted proxy IPs seen in the last 30 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 60d](dcproxy-ip-60d/) | Datacenter-hosted proxy IPs seen in the last 60 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 90d](dcproxy-ip-90d/) | Datacenter-hosted proxy IPs seen in the last 90 days, with provider attribution. | CSV, MMDB | Daily |
| [Public Proxy IP 1d](pubproxy-ip-1d/) | Addresses where public proxies listened or their traffic exited in the last 24 hours, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 7d](pubproxy-ip-7d/) | Addresses where public proxies listened or their traffic exited in the last 7 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 14d](pubproxy-ip-14d/) | Addresses where public proxies listened or their traffic exited in the last 14 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 30d](pubproxy-ip-30d/) | Addresses where public proxies listened or their traffic exited in the last 30 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 60d](pubproxy-ip-60d/) | Addresses where public proxies listened or their traffic exited in the last 60 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 90d](pubproxy-ip-90d/) | Addresses where public proxies listened or their traffic exited in the last 90 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Bot IP](bot-ip/) | IP ranges bots use, from search and AI crawlers to monitors, scanners and webhook senders, each with its operator, its bots, what they do and whether the operator vouches for the address. | CSV, MMDB | Daily |

## Reading a sample

The CSV is gzipped, with a header row:

```bash
gunzip -c vpn-ip/vpn_ip_v1.sample.csv.gz | head -3
```

The MMDB opens in any MaxMind DB reader through its generic lookup: a GeoIP2 reader's `city()` or `country()` expects MaxMind's own field layout, which ours doesn't follow. In Python, after `pip install maxminddb`:

```python
import maxminddb

with maxminddb.open_database("vpn-ip/vpn_ip_v1.sample.mmdb") as db:
    print(db.get("1.0.7.231"))
```

Both formats hold every value as text: a number or a date is a string, and an empty field is an empty string. The plain `.csv` beside each sample is the same rows ungzipped, which GitHub shows as a table. `datasets.json` lists every sample with its columns and files, for tooling.

## The full databases

Each folder's README has its database's download command. The Open databases are free under CC BY-SA 4.0 with a VPNDetection account; the rest are licensed per database, and an [evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Evaluation+license&utm_source=github&utm_medium=referral&utm_campaign=sample-databases) puts a whole one in your hands to test first.

The samples here are refreshed weekly, and at once when a database's columns change. The database pages at [vpndetection.io/databases](https://vpndetection.io/databases?utm_source=github&utm_medium=referral&utm_campaign=sample-databases) have today's.

## License

The samples are licensed under [CC BY-SA 4.0](LICENSE): credit VPNDetection with a link to [vpndetection.io](https://vpndetection.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases), and share what you build from them under the same license.

## About VPNDetection

[<picture><source media="(prefers-color-scheme: dark)" srcset="https://s3.vpndetection.io/vpndetection-public/brand/logo-dark.svg"><img src="https://s3.vpndetection.io/vpndetection-public/brand/logo.svg" alt="VPNDetection" height="40"/></picture>](https://vpndetection.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases)

VPN Detection API: Accurate anonymity detection identifying VPNs, residential proxies, hosting servers, Tor nodes, CDNs, relays and more.

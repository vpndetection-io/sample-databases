# Bot IP

IP ranges bots use, from search and AI crawlers to monitors, scanners and webhook senders, each with its operator, its bots, what they do and whether the operator vouches for the address.

| Field | Value |
| --- | --- |
| ID | `bot_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 41,660 entries, 331 KB as CSV and 781 KB as MMDB, on 2026-11-21 |
| This sample | 100 rows from the 2026-11-21 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Bot+IP+Database+evaluation&products=Bot+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bot-ip) |
| Docs | [docs.vpndetection.io/database/bot-ip/bot-ip](https://docs.vpndetection.io/database/bot-ip/bot-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bot-ip) |

## Files

- [`bot_ip_v1.sample.csv`](bot_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`bot_ip_v1.sample.csv.gz`](bot_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`bot_ip_v1.sample.mmdb`](bot_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

For letting a verified crawler through bot rules by the operator that vouches for its address, keeping crawler, monitor and link checker traffic out of analytics and ad counts, and catching a client posing as a known bot.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.14.182.182` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.14.182.182` |
| `provider` | `string` | The bot operator's ID in the bot_provider catalog, or for an unverified range the operator its claim named, empty where no operator is known. | `amazon` |
| `agents` | `string` | The bots the range serves, or for an unverified one the bots it claimed to be, as their user agents name them, joined by \|. | `Amzn-User` |
| `categories` | `string` | What those bots do, joined by \|, empty where unknown. | `ai_assistant` |
| `identity` | `string` | How we know the range is a bot's. | `undeclared` |
| `verified_by` | `string` | How a verified range verified, empty for any other identity. | `list` |
| `confidence` | `string` | How sure we are the range is what the row says: high, medium or low. | `medium` |
| `first_seen` | `date` | The first day the range was seen as such. | `2026-11-14` |
| `last_seen` | `date` | The last day the range was seen as such. | `2026-11-19` |

`categories` is one of:

| Value | Description |
| --- | --- |
| `search_engine` | Indexes pages for a web search engine, such as Googlebot and Bingbot. |
| `ai_training` | Collects pages to train AI models, such as GPTBot, ClaudeBot and CCBot. |
| `ai_search` | Indexes pages an AI answer engine searches and cites, such as OAI-SearchBot and PerplexityBot. |
| `ai_assistant` | Fetches a page because a person asked an AI assistant about it, such as ChatGPT-User and Claude-User. |
| `ai_agent` | Browses for a person, opening pages and filling in forms, such as ChatGPT agent and Google-Agent. |
| `seo` | Audits sites and maps their links for SEO tools, such as AhrefsBot and SemrushBot. |
| `ads` | Checks ad landing pages and where ads appear, such as AdsBot-Google and TTD-Content. |
| `preview` | Fetches a page to show its preview when someone shares the link, such as facebookexternalhit and Slackbot. |
| `feed` | Polls feeds for readers and aggregators, such as FeedFetcher-Google and FlipboardRSS. |
| `monitoring` | Checks a site's uptime and speed for its owner, such as UptimeRobot and Pingdom. |
| `archiver` | Saves copies of pages for a web archive, such as archive.org_bot and CCBot. |
| `scanner` | Probes addresses across the whole internet for research and exposure data, such as Censys and Shodan. |
| `link_security` | Opens links to check them for phishing and malware, often for an email security product. |
| `webhook` | Sends event callbacks to the URLs a platform's customers register, such as Stripe and GitHub. |
| `other` | Automation its operator names that no other category fits. |

`identity` is one of:

| Value | Description |
| --- | --- |
| `verified` | The operator vouches for the address: it publishes it, documents the reverse DNS name it carries, or owns the address space a claim to be its bot came from. |
| `declared` | The client names itself as a bot that cannot be verified, in its user agent or in a reverse DNS name its operator does not document. |
| `spoofed` | The client claimed to be a bot whose operator vouches for its addresses, from an address that is not one of them. |
| `undeclared` | The client names itself as a browser, or as nothing, and behaves as automation. |

`verified_by` is one of:

| Value | Description |
| --- | --- |
| `list` | The address is in a list of addresses the operator publishes for its bot. |
| `rdns` | The address's reverse DNS name ends in a suffix the operator documents, and resolves back to the address. |
| `owner` | The address is in the operator's own registered space, and was seen claiming to be its bot. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | The bot operator's ID in the bot_provider catalog, or for an unverified range the operator its claim named, empty where no operator is known. | `amazon` |
| `agents` | `string` | The bots the range serves, or for an unverified one the bots it claimed to be, as their user agents name them, joined by \|. | `Amzn-User` |
| `categories` | `string` | What those bots do, joined by \|, empty where unknown. | `ai_assistant` |
| `identity` | `string` | How we know the range is a bot's. | `undeclared` |
| `verified_by` | `string` | How a verified range verified, empty for any other identity. | `list` |
| `confidence` | `string` | How sure we are the range is what the row says: high, medium or low. | `medium` |
| `first_seen` | `date` | The first day the range was seen as such. | `2026-11-14` |
| `last_seen` | `date` | The last day the range was seen as such. | `2026-11-19` |

## The full database

The full database needs a license: [request an evaluation](https://vpndetection.io/contact?purpose=evaluation&subject=Bot+IP+Database+evaluation&products=Bot+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bot-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o bot_ip_v1.csv.gz "https://api.vpndetection.io/api/v1/database/download?id=bot_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o bot_ip_v1.mmdb "https://api.vpndetection.io/api/v1/database/download?id=bot_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://vpndetection.io/databases/bot-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bot-ip), cut from the latest build.

Back to [all VPNDetection sample databases](../).

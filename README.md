# Welcome to Aurora

> [!NOTE]
>
> Build Serverless configs with cloudflare worker and pages easily

## Features

- [x] Automatically split VLESS, Trojan, and Shadowsocks protocols
- [x] Reverse proxy
- [x] Proxy list cache
- [x] TCP and DoH support
- [x] Websocket CDN and SNI transport
- [x] KV proxy key (country-based proxy)
- [x] Nice and minimalist web interface (in my opinion)
- [x] Dark mode
- [x] Auto-check (ping) accounts
- [x] Fetch accounts in various formats (link, clash, sing-box, etc.)
- [x] Wildcard registration
- [x] Add filters
  - [x] Country `&cc=ID,SG,...`
- [x] Subscription API
  - [x] Country Code `&cc=ID,SG,JP,KR,...`
  - [x] Format `&format=clash` (raw, clash, sfa, bfr, v2ray)
  - [x] Limit `&limit=10`
  - [x] Protocol `&vpn=vless,trojan,ss`
  - [x] Port `&port=443,80`
  - [x] Domain `&domain=zoom.us`
- [x] Knob `Deploy to workers` for instant deployment

### Todo (Not Yet Completed)

- [x] More efficient (Partial) (I hate JavaScript, so I can't be bothered to fix it)  
- [x] Shadowsocks URL Scheme

> This code still needs a lot of work, so please contribute and submit your PRs!

- Must be UUID v4 Variant 2
- Use security `none`
- Use DoH in your VPN application if you can't browse or open websites
- DoH example: `https://8.8.8.8/dns-query`

<br/> 

## Instant Deploy

Click the button below
[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/Diana-Cl/aurora)

<br><br/> 

## Manual

1. Create a Cloudflare account
2. Create a worker
3. Copy the code from [_worker.js](./worker.js) into the Cloudflare worker editor
4. (Optional) Enter your proxy list link into the environment variable `PROXY_BANK_URL`
5. (Optional) Masukkan link target reverse proxy ke environment variable `REVERSE_PROXY_TARGET`
6. Deploy
7. Open `https://domain.workers.dev/sub`

- Example proxy list [proxyList.txt](https://raw.githubusercontent.com/Diana-Cl/aurora/refs/heads/main/proxyList.txt)
- Example reverse proxy [example.com](https://example.com)

<br/> 

## How to Activate API

One of the functions of the API is to allow you to view and add wildcard subdomains to workers.

Here's how to activate it:

1. Go to the editor page of the worker you just created.
2. Fill in the `variables` from lines 4-9 according to the keys you have.
3. Deploy

<br/> 

### Wildcard Activation (Custom Domain)

1. Complete the [API Activation](#cara-aktivasi-api)
2. with your main domain
    - Example: Domain workers
    - `aurora.nscl.com`, means the main domain is `nscl.com`
3. Fill the `serviceName` variable with the name of your workers.
   - Example: Domain workers `aurora.nscl.com`, means the name of the worker is `aurora`
4. Create a custom domain in the workers settings with a combination `serviceName`.`rootDomain`
   - Example: `nautica.foolvpn.me`

<br><br/> 

## Endpoint

- `/` -> Reverse proxy homepage
- `/sub/:page` -> Sub/account list page
- `/api/v1/sub` -> Subscription link, [Queries](#features)

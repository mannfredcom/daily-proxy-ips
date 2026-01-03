# daily-proxy-ips

Daily CSV snapshots of **open proxy exit IPs** (IPv4 + IPv6) for operators who prefer **local lookups** over DNSBL/RBL queries.

**Workflow:** fetch daily → load into local tooling (set / DB / firewall / cache) → query locally during enforcement.

## Why lists instead of DNS?

DNSBL/RBL is often the right answer, but some operators prefer local lists for:

- **Privacy** - per-request lookups can leak what you're checking to upstream resolvers
- **Robustness** - local checks work during DNS incidents, resolver failures, or offline/restricted environments

If real-time signal matters more, use DNSBL/RBL directly. This repo is an **offline alternative**.

## Files

| File | Contents |
|------|----------|
| [`bl-open-proxy-exits-ipv4.csv`](./bl-open-proxy-exits-ipv4.csv) | Open proxy exit IPv4 addresses |
| [`bl-open-proxy-exits-ipv6.csv`](./bl-open-proxy-exits-ipv6.csv) | Open proxy exit IPv6 addresses |

**Format:** one row per exit IP. Column 1 is the canonical IP; additional columns (comments/metadata) may exist. If you only need IPs, use column 1.

## Download

Raw URLs for automation:
```bash
curl -sSfL https://raw.githubusercontent.com/mannfredcom/daily-proxy-ips/main/bl-open-proxy-exits-ipv4.csv -o bl-open-proxy-exits-ipv4.csv
curl -sSfL https://raw.githubusercontent.com/mannfredcom/daily-proxy-ips/main/bl-open-proxy-exits-ipv6.csv -o bl-open-proxy-exits-ipv6.csv
```

## Data source

Derived from the same detection pipeline as [semi-static-proxy-ips](https://github.com/mannfredcom/semi-static-proxy-ips), feeding [DroneBL](https://dronebl.org/) and [EFnetRBL](https://rbl.efnetrbl.org/). Updated **daily**.

## Intended use

Defensive security, abuse mitigation, and network monitoring. **Not** for circumventing safeguards or malicious activity.

## License

MIT. Provided as-is, no warranty. Attribution appreciated.

## Contact

[mannfred.com](https://mannfred.com) · [mannfred@gmail.com](mailto:mannfred@gmail.com)

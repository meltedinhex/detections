# Melted in Hex — Detections

Open detection coverage (YARA, Sigma, KQL) and IOCs for malware campaigns analyzed on
[meltedinhex.com](https://meltedinhex.com).

Each campaign lives in its own folder with a short README, the rules, and a machine-readable
IOC list. Everything here is derived from hands-on analysis and cross-referenced with public
reporting — see the linked write-up in each campaign README for the full reasoning.

> ⚠️ **Defanged where noted.** IOC files use defanged forms (`hxxp`, `[.]`) in human-readable
> docs and plain values in the machine-readable `iocs.csv`/`iocs.json` for tooling. Handle all
> samples and hashes as hostile.

## Campaigns

| Campaign | Family / Wave | Type | Write-up |
|---|---|---|---|
| [`nhmpy-hades-pypi`](./nhmpy-hades-pypi/) | Shai-Hulud-class · Hades wave | PyPI supply-chain credential worm | [Peeling the Sandworm](https://meltedinhex.com/posts/shai-hulud-nhmpy-pypi/) |

## Layout

```
detections/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
└── <campaign>/
    ├── README.md          # context + how to use these rules
    ├── yara/*.yar         # static + decoded-content rules
    ├── sigma/*.yml        # portable SIEM/EDR logic
    ├── kql/*.kql          # Microsoft Defender / Sentinel
    └── iocs/
        ├── iocs.csv       # machine-readable (plain values)
        └── iocs.json      # machine-readable (plain values)
```

## Using these rules

- **YARA** — `yara <campaign>/yara/<rule>.yar <path>`. Read each rule's `meta` for scope; some
  match *decoded* content only (run against memory/unpacked strings, not the raw artifact).
- **Sigma** — convert with [`sigma-cli`](https://github.com/SigmaHQ/sigma-cli) /
  [pySigma](https://github.com/SigmaHQ/pySigma) to your backend.
- **KQL** — paste into Microsoft Defender for Endpoint Advanced Hunting or Sentinel; tune the
  time window and exclude hosts where the flagged tooling is legitimate.

## License

Detection content is released under [MIT](./LICENSE) — use, adapt, and redistribute freely.
Attribution appreciated but not required.

## Contributing

Improvements, false-positive reports, and new conversions (Sigma backends, Splunk, Elastic) are
welcome — see [CONTRIBUTING.md](./CONTRIBUTING.md).

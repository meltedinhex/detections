# Contributing

Thanks for helping improve open detection coverage.

## What's welcome

- **False-positive reports** — tell us the rule, the benign trigger, and (ideally) a tightened condition.
- **New conversions** — Splunk SPL, Elastic EQL/ES|QL, additional Sigma backends.
- **New campaigns** — a folder following the existing layout, tied to a public write-up or sample.
- **IOC corrections** — with a source or reasoning.

## Ground rules

- **No live malware** in this repo. Hashes, strings, and network indicators only.
- **Cite your reasoning.** Detection logic should be explainable; link the artifact, report, or sample hash.
- **Keep `meta` honest.** Note whether a YARA rule matches raw bytes or *decoded* content, and the expected false-positive surface.
- **Defang human-readable docs** (`hxxp`, `[.]`). Keep `iocs.csv` / `iocs.json` plain for tooling.

## Layout for a new campaign

```
<campaign>/
├── README.md
├── yara/*.yar
├── sigma/*.yml
├── kql/*.kql
└── iocs/{iocs.csv,iocs.json}
```

Open a PR with a short description of what the rules detect and how you validated them.

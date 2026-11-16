# Security Research

Applied security research: malware analysis, CVE reproductions, vulnerability
write-ups, reverse-engineering notes, detection rules, and threat intelligence.

All work here is performed in isolated lab environments for defensive and
educational purposes. See [DISCLAIMER.md](DISCLAIMER.md) before using anything
in this repository.

## Contents

| Area | Description |
|---|---|
| [`malware-analysis/`](malware-analysis/) | Static + dynamic analysis reports, IOCs, behavioural profiles |
| [`cve-reproductions/`](cve-reproductions/) | Reproducing published CVEs in controlled labs, with root-cause analysis |
| [`vulnerability-writeups/`](vulnerability-writeups/) | Bugs found first-hand: discovery, impact, disclosure timeline |
| [`reverse-engineering/`](reverse-engineering/) | RE notes, annotated disassembly, protocol and format reversing |
| [`proof-of-concepts/`](proof-of-concepts/) | Minimal PoCs against intentionally vulnerable lab targets |
| [`detections/`](detections/) | YARA and Sigma rules derived from the analysis above |
| [`threat-intel/`](threat-intel/) | Actor/campaign tracking, infrastructure pivots, TTP mapping |
| [`docs/`](docs/) | Lab setup, sample handling, disclosure policy, style guide |
| [`templates/`](templates/) | Report templates — start every new entry from one of these |
| [`tools/`](tools/) | Helper scripts for scaffolding and validating content |

## How research is organised

Every piece of research is a directory, not a file:

```
<area>/<NNNN>-<short-slug>/
├── README.md        # the report itself
├── iocs/            # hashes, domains, IPs (CSV or STIX)
├── rules/           # detections produced by this research
├── scripts/         # unpackers, config extractors, harnesses
└── artifacts/       # screenshots, graphs, diffs (never live samples)
```

Numbering is sequential per area (`0001-`, `0002-`) so entries sort
chronologically and links stay stable.

Start a new entry with:

```bash
python3 tools/new_report.py malware-analysis "Emotet loader variant"
```

Validate everything before committing:

```bash
make check
```

## Ground rules

1. **No live samples in git.** Hashes and analysis only — see [docs/handling-samples.md](docs/handling-samples.md).
2. **Every claim is reproducible.** State the environment, versions, and exact commands.
3. **Detections ship with the analysis.** A malware report without a YARA or Sigma rule is unfinished.
4. **Coordinated disclosure.** Nothing in `vulnerability-writeups/` is published before the timeline in [docs/disclosure-policy.md](docs/disclosure-policy.md) is satisfied.
5. **PoCs target lab software only.** Minimal demonstration of the flaw, never a weaponised tool.

## Licence

Code (scripts, rules, PoCs): [MIT](LICENSE).
Written research (reports, notes): [CC BY 4.0](LICENSE-CONTENT).

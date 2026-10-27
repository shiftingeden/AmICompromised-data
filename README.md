# AmICompromised-data

Data feed for the **Am I Compromised?** app.

`apple-kev.json` lists every entry in CISA's
[Known Exploited Vulnerabilities catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
that affects iPhone OS, with the vulnerable iOS version ranges from the
[National Vulnerability Database](https://nvd.nist.gov/). The app compares the
phone's iOS version against it.

A GitHub Action regenerates the file daily with `generate_apple_kev.py` and
commits it only when something changed.

Both sources are US government works in the public domain.

## Optional extra lists (`extra-indicators.yaml`, `extra/`)

Spyware indicators that the [mvt-indicators](https://github.com/mvt-project/mvt-indicators)
index doesn't list. The app only uses them when the person turns on **Extra lists
(unauthenticated)**, which is **off by default**.

- **Amnesty International** ([investigations](https://github.com/AmnestyTech/investigations)):
  Cytrox 2021 (STIX, passed through), NSO 2018 and Morocco 2019, FinFisher 2020
  (domain lists converted to STIX).
- **Citizen Lab** ([malware-indicators](https://github.com/citizenlab/malware-indicators)):
  NSO 2016–2018 and Cyberbit 2017 reports (MISP CSV converted to STIX: domains, URLs, emails).
- **AdFection** (Citizen Lab and Confiant research, Oct 2026), taken from the CC0
  export of the anonymous [Zero Breach Toolkit](https://github.com/interplains/Zero-Breach-Toolkit)
  project. **Not independently verified.** Pinned to one reviewed commit and checksum in
  `generate_extra_indicators.py`; only primary-confidence domains are used (no IPs, no
  lower-confidence historical domains).

`generate_extra_indicators.py` rebuilds them daily (standard library only). A source
that fails keeps its previous file.

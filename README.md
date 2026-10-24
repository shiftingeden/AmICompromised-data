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

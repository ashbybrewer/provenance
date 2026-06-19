# Provenance

**A citation tracer for statistics that travel.**

Provenance follows famous numbers from the version everyone repeats back to the primary document — and pinpoints the exact spot where the retelling drifts from its source. It is a single, self-contained HTML page: no build step, no dependencies, no tracking.

🔎 **Live site:** https://ashbybrewer.github.io/provenance/

---

## What it is

Widely-cited statistics are a game of telephone. The version that travels — the headline, the slide, the tweet — is rarely the version the source actually supports. Provenance rebuilds the chain of custody for fourteen well-known numbers so a reader can see for themselves where a claim parts ways with its evidence.

Each entry is traced through five steps:

1. **The claim, as cited** — the number in the form it actually circulates.
2. **Traced to source** — the study, agency, or filing it rests on (or the discovery that it rests on nothing).
3. **What the source says** — the primary text, quoted verbatim and attributed.
4. **Where it drifts** — a redline of the cited version against the sourced version, plus an explanation of the move.
5. **Methodology & caveats** — the honest limitations, in both directions.

## What it is *not*

Provenance does **not** rule on whether an underlying issue is real or important. Climate consensus is real; hunger is real; gun deaths are real. The register checks one narrower thing: whether the *cited number* says what the *citation* implies it says. Often the honest correction makes a claim **stronger**, not weaker.

## The drift taxonomy

Every distortion is classified by the move it makes. The eight codes double as filters:

| Code | Name | The move |
|------|------|----------|
| `CAVEAT` | Caveat dropped | A load-bearing qualifier was cut, so the number now claims more than the source did. |
| `SCOPE` | Scope inflated | The population or denominator was quietly widened beyond what was measured. |
| `TERM` | Term swapped | A precisely-defined concept was retold using a vaguer or more vivid word. |
| `FROZEN` | Figure frozen | An estimate that has since moved is still quoted as if it were current. |
| `PHANTOM` | Source phantom | Follow the citation and it dead-ends in no primary evidence at all. |
| `METHOD` | Method elided | Several defensible numbers exist; the citation never says which one it used. |
| `BLEND` | Categories blended | A real figure folds in cases that don't fit the claim being made. |
| `SLOGAN` | Slogan laundered | A marketing or rhetorical number was reintroduced as a research finding. |

## Features

- **14 traced statistics** across Climate, Guns, Economy, Poverty, Immigration, Health, Media, and Everyday claims.
- **An animated hero** that visibly self-corrects a headline back to what its source measured.
- **Filter by drift type or domain** to compare how distortions recur across topics.
- **Per-claim dossiers** with the full chain of custody, a redline diff, primary-source links, and prev/next navigation.
- **Deep linking** — every dossier is addressable via a `#/case/<id>` hash, so individual entries can be shared.
- **Accessible by design** — semantic markup, ARIA labels, a focus trap and keyboard handling in the modal, and a `prefers-reduced-motion` fallback.
- **Zero dependencies** — one HTML file with inline CSS and vanilla JavaScript. Fonts load from Google Fonts; everything else is self-contained.

## Running locally

No build step required. Either open the file directly:

```bash
open index.html
```

…or serve it from a local web server (recommended, so deep-link hashes and fonts behave exactly as in production):

```bash
# Python 3
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Project structure

```
.
├── index.html   # The entire application — markup, styles, data, and logic
├── README.md    # This file
└── LICENSE      # MIT
```

The dataset lives in the `DATA` array inside `index.html`, and the drift codes in the `DRIFT` object. To add an entry, append an object to `DATA` with its claim, source, verbatim quote, redline, and drift codes — the catalog, filters, and dossiers all render from that data.

## Tech stack

- Semantic HTML5
- Vanilla CSS (custom properties, grid, an editorial type system set in Libre Caslon Display, Spectral, Archivo, and IBM Plex Mono)
- Vanilla JavaScript (no framework, no build tooling)

## A note on sourcing

Every quotation in the register is taken from the primary document and linked where a public copy exists. Where a claim traces to no primary source at all, the register says so plainly — that absence is itself the finding.

## License

Released under the [MIT License](LICENSE).

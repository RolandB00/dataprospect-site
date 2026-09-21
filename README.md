# DataProspect Accessibility Scanner

Open-source CLI for automated accessibility checks against WCAG-relevant rules using Playwright and axe-core.

The project is intended for developers, auditors and teams that want a repeatable first-pass accessibility scan of websites and online shops. It can be used as part of BFSG / European Accessibility Act preparation, CI checks, QA workflows and larger accessibility studies.

> Automated testing can identify many accessibility problems, but it cannot prove full WCAG 2.2, EN 301 549, BFSG or EAA compliance. Manual review is still required.

## What it does

- opens a page in Chromium with Playwright
- runs axe-core accessibility rules
- reports violations by impact level
- prints affected selectors and remediation guidance
- supports machine-readable JSON output
- exits with a non-zero status when serious issues are found, making it usable in CI

## Quick start

```bash
git clone https://github.com/RolandB00/dataprospect-site.git
cd dataprospect-site
npm install
npx playwright install chromium
node src/cli.js https://example.com
```

JSON output:

```bash
node src/cli.js https://example.com --json
```

Fail CI on a chosen impact level:

```bash
node src/cli.js https://example.com --fail-on serious
```

## Why this exists

Accessibility reviews are often performed one page at a time with inconsistent tooling. This project provides a small, transparent building block that can be automated across many URLs and integrated into larger audit pipelines.

The longer-term goal is to add:

- sitemap and multi-page crawling
- WCAG 2.2-oriented reporting
- CSV/HTML reports
- recurring regression scans
- CI examples
- optional AI-assisted explanation of findings
- large-scale anonymized aggregate studies

## Usage

```text
node src/cli.js <url> [--json] [--fail-on minor|moderate|serious|critical]
```

Examples:

```bash
node src/cli.js https://example.com
node src/cli.js https://example.com --json
node src/cli.js https://example.com --fail-on moderate
```

## Output

For every violation the CLI reports:

- rule ID
- impact
- description
- help text
- affected DOM selectors
- help URL

## Contributing

Issues and pull requests are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).

## Maintainer

Maintained by [RolandB00](https://github.com/RolandB00) as part of the open tooling around DataProspect accessibility research and auditing.

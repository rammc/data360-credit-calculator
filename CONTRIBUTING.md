# Contributing to Data 360 Credit Calculator

Thanks for your interest in contributing! This project is intentionally simple — a single HTML file with no build step — and contributions should maintain that simplicity.

## How to Contribute

### Reporting Issues

- Open a [GitHub Issue](https://github.com/rammc/data360-credit-calculator/issues)
- Include: what you expected, what happened, browser/OS info
- For rate card discrepancies, link to the official Salesforce source

### Rate Card Updates

When Salesforce publishes updated multipliers:

1. Verify the new rates at [salesforce.com/data/rates/multipliers](https://www.salesforce.com/data/rates/multipliers/)
2. Update the `RATE_CARD` array in `index.html`
3. Update the rate card table in `README.md`
4. Add a note in your PR referencing the official source and date

### Code Changes

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-change`)
3. Make your changes to `index.html`
4. Test locally (open in browser — no build needed)
5. Open a Pull Request with a clear description

### Design Principles

- **Single file**: The entire app lives in `index.html`. Keep it that way.
- **No build step**: React via CDN, plain JavaScript, CSS in `<style>`. No npm, no webpack, no transpilation.
- **Accuracy first**: All rates must match the official Salesforce documentation. If in doubt, don't guess — open an issue instead.
- **Mobile-friendly**: Test on mobile viewports. The calculator should remain usable on phones.

### What We'd Love Help With

- Rate card updates when Salesforce changes multipliers
- Additional usage types that are missing
- Sandbox multiplier toggle (20% discount)
- Export to PDF or CSV
- Translations (German, French, Spanish, etc.)
- Accessibility improvements
- Dark/light theme toggle

## Code Style

- Use `var` (not `let`/`const`) for compatibility with the non-transpiled React approach
- Use `React.createElement` (aliased as `e`) — no JSX
- Keep CSS in the `<style>` block, using CSS custom properties
- Avoid external dependencies beyond React/ReactDOM CDN

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).

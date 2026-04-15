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

### Contributing Templates

Use case templates are one of the easiest ways to contribute. A template is a JSON object
that defines which usage types are active and with what default values.

To add a template:

1. Add your template to the `TEMPLATES` array in `index.html`
2. Include: `templateId` (snake_case), `name`, `description` (1-2 sentences),
   and `usages` with realistic volumes for a mid-size enterprise
3. Open a PR with:
   - The template definition
   - A brief explanation of the use case and why the chosen volumes are realistic
   - Your source or experience basis (e.g., "based on a 5M profile retail implementation")

Template volumes should represent a **mid-size enterprise** starting point (1-10M profiles).
They will always be adjusted by the user — the goal is a reasonable default, not precision.

## Code Style

- Use `var` (not `let`/`const`) for compatibility with the non-transpiled React approach
- Use `React.createElement` (aliased as `e`) — no JSX
- Keep CSS in the `<style>` block, using CSS custom properties
- Avoid external dependencies beyond React/ReactDOM CDN

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).

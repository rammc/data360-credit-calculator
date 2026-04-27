# Data 360 Credit Calculator

An open-source, interactive credit consumption estimator for **Salesforce Data 360** (formerly Data Cloud). Built as a single-page web application — no backend, no build step, runs entirely in the browser.

**[→ Launch Calculator](https://rammc.github.io/data360-credit-calculator/)**

---

## What This Does

Salesforce Data 360 operates on a consumption-based pricing model where different operations (segmentation, calculated insights, activations, etc.) consume credits at different rates. Estimating total credit consumption for a use case requires understanding these rates and projecting volumes over time.

This calculator helps architects, consultants, and business users:

- **Start from templates** — 11 pre-configured scenarios for common Data 360 use cases (from CDP setup to AI-powered service agents)
- **AI-powered configuration** — Describe your use case in plain language and let Claude configure the calculator automatically
- **Estimate credit consumption** across 10 usage types from the official Data Services Rate Card
- **Configure multiple use cases** — Compare credit consumption across different use cases side by side
- **Project costs over 3 years** with configurable YoY growth rates and custom currency/pricing
- **Account for testing overhead** with adjustable test volume and test run parameters
- **Understand what each usage type means** — Business-friendly explanations, examples, and volume hints for every service

## Rate Card Source

All multipliers are sourced from the **official Salesforce Data Services Rate Card** (last updated August 2025), available at:
[salesforce.com/data/rates/multipliers](https://www.salesforce.com/data/rates/multipliers/)

| Usage Type | Multiplier | Unit |
|---|---:|---|
| (External) Data Pipeline | 2,000 | Per 1M Rows (Batch) |
| Profile Unification | 100,000 | Per 1M Rows |
| Batch Calculated Insights | 15 | Per 1M Rows |
| Streaming Calculated Insights | 800 | Per 1M Rows |
| Inferences | 3,500 | Per 1M Inferences |
| Segmentation | 20 | Per 1M Rows |
| Batch Activation | 10 | Per 1M Rows |
| Activate DMO – Streaming | 1,600 | Per 1M Rows |
| Streaming Actions (incl. Lookups) | 800 | Per 1M Rows |
| Data Queries | 2 | Per 1M Rows |

**Note:** Salesforce native data ingestion (Sales Cloud, Service Cloud, Marketing Cloud Engagement, Marketing Cloud Personalization, Commerce Cloud) has been free since September 2025 and is therefore not included in this calculator.

## How It Works

### Credit Calculation Formula

```
Credits = (Total Rows Processed / 1,000,000) × Multiplier
```

### Total Rows Processed

```
Total Rows = (Volume × Frequency) + (Volume × Test Volume % × Test Runs per Year)
```

### Cost Calculation

```
Cost = (Credits / 100,000) × Cost per 100K Credits
```

The Salesforce list price is **$500 per 100,000 Data Service Credits**. The calculator allows you to set a custom price and currency (USD, EUR, GBP, CHF, JPY) to match your negotiated contract rate.

### Year-over-Year Growth

Year 2 and Year 3 values are calculated by applying the configured growth rate compoundingly:

```
Year N+1 = Year N × (1 + Growth Rate)
```

## Getting Started

### Option 1: Use the hosted version

Visit **[rammc.github.io/data360-credit-calculator](https://rammc.github.io/data360-credit-calculator/)** — nothing to install.

The calculator opens with a **template lobby** — pick a pre-configured scenario or start blank. You can add multiple use cases and compare them side by side.

### Use Case Templates

11 templates cover common Data 360 scenarios:

**Getting Started:**
- Proactive Service
- Personalized Marketing Journey
- Lead & Opportunity Scoring
- Real-Time Personalization
- Data Foundation / CDP Setup
- AI-Powered Service Agents

**Advanced Scenarios:**
- Historical Data Migration
- High-Frequency Web & App Events
- Complex Identity Resolution
- Cross-Cloud Activation (Batch vs. Streaming)
- RAG & Unstructured Data for AI

Each template pre-configures relevant usage types with realistic volumes for a mid-size enterprise. All values are adjustable after selection.

### AI-Powered Configuration (optional)

Describe your use case in plain language and let Claude configure the calculator for you. This feature requires an Anthropic API key (BYOK).

1. Click ⚙ in the header and enter your Anthropic API key
2. Use the "Describe your use case" card in the lobby
3. Describe what you want to achieve — the more specific, the better
4. Claude selects usage types and estimates volumes based on your description

**Privacy:** Your API key is stored in your browser's LocalStorage only. It is never sent to our servers — API calls go directly from your browser to `api.anthropic.com`. This is a static GitHub Pages site with no backend.

**Cost:** Each AI configuration request costs approximately $0.01–0.03 in Anthropic API credits, depending on the length of your description.

### Multi-Use-Case Support

You can configure multiple use cases in parallel (e.g., "Proactive Service" + "Lead Scoring") and see:
- Total credits and costs aggregated across all use cases
- A comparison table showing each use case's contribution
- Credit distribution breakdown by use case and by usage type

### Option 2: Run locally

```bash
git clone https://github.com/rammc/data360-credit-calculator.git
cd data360-credit-calculator

# Serve with any static file server
npx serve .
# or
python3 -m http.server 8000
```

Open `http://localhost:8000` (or the port your server uses).

### Option 3: Fork and deploy your own

1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch** → `main` → `/ (root)`
4. Your calculator will be live at `https://<your-username>.github.io/data360-credit-calculator/`

## Project Structure

```
data360-credit-calculator/
├── index.html          # The entire application (single file, zero dependencies)
├── README.md           # This file
├── LICENSE             # MIT License
├── CONTRIBUTING.md     # Contribution guidelines
└── .github/
    └── FUNDING.yml     # Optional: GitHub Sponsors config
```

The calculator is intentionally built as a **single HTML file** with no build step, no npm dependencies, and no framework overhead beyond React via CDN. This makes it trivially deployable, easy to audit, and simple to fork.

## Disclaimer

This calculator provides **estimates only**. Actual credit consumption depends on your specific implementation, data volumes, and processing patterns. Key things to keep in mind:

- The **list price** of $500/100K credits is the default. You can configure your negotiated rate.
- **Sandbox environments** have a 20% discount on multipliers (not reflected in this calculator).
- Salesforce may **update rates** at any time. Check the [official rate card](https://www.salesforce.com/data/rates/multipliers/) for the latest.
- AI-generated configurations are starting estimates — always review and adjust.
- This tool is **not affiliated with or endorsed by Salesforce, Inc.**

Always verify estimates with your Salesforce Account Executive before making purchasing decisions.

## Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Common contributions that would be valuable:
- Rate card updates when Salesforce publishes new multipliers
- New use case templates (see CONTRIBUTING.md for template format)
- AI prompt improvements for better configuration accuracy
- Additional usage types
- Sandbox multiplier toggle
- Export functionality (PDF/CSV)
- Localization (DE, FR, ES, ...)

## Author

**Annika Schühle**
Consultant: Customer Data & Tech · Capgemini Invent

**Fabian Pfann**
Senior Manager Customer Data & Tech · Capgemini Invent

**Christopher Ramm**
Salesforce Certified Technical Architect (CTA) · Salesforce MVP (Class of 2025) · DCX CTO Germany @ Capgemini

- Website: [cramm.dev](https://cramm.dev)
- GitHub: [@rammc](https://github.com/rammc)

## Built with AI Assistance

This repository was developed with support from AI tools (Claude by Anthropic) for code generation, documentation, and architecture. All content has been reviewed, validated, and curated by the authors.

## License

[MIT](LICENSE) — use it, fork it, build on it.

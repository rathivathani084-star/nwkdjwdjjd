# CostGuard — Azure Infrastructure Cost Impact Predictor

A modern Cloud FinOps developer dashboard prototype that analyzes Terraform plans and predicts monthly Azure financial impact before changes reach production.

![CostGuard Dashboard](https://img.shields.io/badge/FinOps-Azure%20Retail%20API-blue)
![CI/CD Guardrail](https://img.shields.io/badge/Guardrail-Circuit--Breaker-emerald)
![Status](https://img.shields.io/badge/Status-Prototype%20Online-indigo)

---

## 🚀 Quick Start

Run the following commands in this directory:

```bash
# 1. Install dependencies
npm install

# 2. Launch the local dev server
npm run dev
```

> **Note for Windows PowerShell users:** If script execution is restricted on your machine, you can run:
> ```powershell
> npm.cmd install
> npm.cmd run dev
> ```

Open [http://localhost:5173/](http://localhost:5173/) in your browser.

---

## 🎯 Key Features

1. **Terraform Plan Ingestion & Analysis**
   - Drag-and-drop Terraform JSON plans (generated via `terraform show -json`).
   - Pre-loaded sample plans from the CostGuard handout.
   - Paste JSON dialog for testing custom plans.
   - 2–3 second realistic simulated pricing pipeline with step-by-step progress tracking.

2. **Dashboard Summary & Impact Metrics**
   - **Prior Monthly Cost:** `$15.18 /mo`
   - **Projected Monthly Cost:** `$50.08 /mo`
   - **Net Monthly Impact:** `+$34.90 /mo`
   - **Budget Threshold:** `+$50.00 /mo`
   - Prominent **WITHIN BUDGET** / **BUDGET EXCEEDED** status banner.

3. **Cost Visualization (Recharts)**
   - Monthly Cost Impact comparison bar chart (Prior, Projected, Delta).
   - Resource allocation donut chart by service category (Compute, Storage, Network, Other).

4. **Interactive Financial Guardrail (Circuit-Breaker)**
   - Dynamic budget allowance slider & number input.
   - Instant visual response:
     - If impact $\le$ threshold: `✓ PASSED`
     - If impact $>$ threshold: `⚠ BUDGET EXCEEDED` with `Exceeded by` delta and `Deployment blocked.`
   - Interactive preset buttons (`$20 Breach`, `$50 Handout Default`, `$100 Safe`) for effortless testing.

5. **Resource Changes Table**
   - Displays all planned lifecycle actions (`azurerm_linux_virtual_machine.app`, `azurerm_managed_disk.data`, `azurerm_linux_virtual_machine.old`).
   - Action badges: `UPDATE`, `CREATE`, `DELETE`.
   - Real-time search and action filtering.
   - Expandable rows for deep inspection and "Details" modal.

6. **Resource Inspection Modal**
   - Resource name, Action, Region, Previous SKU, New SKU, Previous/New Monthly Costs, Monthly Impact.
   - Azure Retail Prices API query filter spec preview.
   - JSON export.

7. **Pricing Engine & Cache Performance**
   - Cache Hits (2), API Lookups (1), Cache Efficiency (66.7%).
   - Live cache operational indicator and in-memory rate latency.

8. **Warnings & Graceful Handling**
   - Collapsible warnings section.
   - Non-billable resources skipped notice.
   - Interactive "Simulate Unknown SKU" toggle demonstrating non-crashing behavior.

9. **Terminal CLI Output Preview**
   - Embedded terminal view replicating the exact handout command-line output.

---

## 🛠️ Tech Stack

- **Framework:** React 19, TypeScript
- **Bundler:** Vite 8
- **Styling:** Tailwind CSS (Modern Dark FinOps Glassmorphism Theme)
- **Charts:** Recharts
- **Icons:** Lucide Icons (`lucide-react`)

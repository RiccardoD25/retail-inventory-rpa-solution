# Retail Inventory Reconciliation RPA

Week 3 project for Retail Innovations Inc. The proposed UiPath automation reconciles POS and ERP inventory, routes unsupported discrepancies for human review, and creates draft replenishment requests for eligible low-stock items.

## Repository contents

- `current_state_process.mmd` — current manual process map source
- `future_state_rpa_flow.mmd` — proposed automation flowchart source
- `lucidchart_build_guide.md` — exact Lucidchart recreation instructions
- `references.md` — APA-formatted references

## UiPath solution structure

Recommended project type: Windows, unattended transactional process.

1. Create Orchestrator assets for URLs, controlled thresholds, calendar, output path, and credential assets.
2. Create queues named `INV-Reconciliation` and `INV-Exceptions`.
3. Implement `Dispatcher.xaml` to acquire, validate, normalize, and queue one item per business date/store/SKU.
4. Implement `Performer.xaml` to compare balances, apply approved rules, update eligible ERP records, verify after-values, and create draft replenishment requests.
5. Implement `EndProcess.xaml` to balance control totals, export KPI data, archive evidence, and send the summary.
6. Configure a nightly Orchestrator trigger after POS close.
7. Start with report-only mode, then a limited pilot with 100% review before production release.

## Important configuration

Do not hard-code credentials, tolerances, materiality limits, reorder points, or recipients. Store credentials in Orchestrator credential assets and controlled business parameters in assets or an approved configuration table.

## Flowcharts

Open the `.mmd` files in Mermaid Live Editor for immediate rendering. For the required Lucidchart submission, follow `lucidchart_build_guide.md`; the guide includes the precise shapes, labels, and connections so both diagrams can be recreated as editable Lucidchart documents.

## Measurement

Collect a four-week baseline before implementation. During report-only and controlled pilots, audit 100% of recommendations and production writes. After stabilization, publish daily operational metrics and conduct monthly exception-Pareto and benefit reviews.

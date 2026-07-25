# Lucidchart Build Guide

Create two separate Lucidchart documents in portrait orientation. Use ovals for start/end, rectangles for actions, diamonds for decisions, solid arrows for sequence, and loop-back connectors for repeated records or retries.

## Current-state process map

Use the labels and connections in `current_state_process.mmd`. Place the main path vertically. Put the mismatch investigation and escalation branch to the right. Loop all completed or escalated SKU outcomes back to **More SKU/store rows?**.

Recommended swimlanes:

1. Inventory analyst
2. POS system
3. ERP system
4. Supervisor

## Future-state RPA flowchart

Use the labels and connections in `future_state_rpa_flow.mmd`. Place the normal automated path in the center, business exceptions on the left, and technical failures on the right. Use a loop from **Retries remaining? — Yes** back to **Update ERP and reread value** and a transaction loop from completed outcomes back to **Next queue item?**.

Recommended swimlanes:

1. UiPath Orchestrator
2. Dispatcher bot
3. Performer bot
4. POS/ERP applications
5. Inventory analyst / support

## Visual conventions

- Blue: automated action
- Gray: external system or data source
- Amber: human review
- Red: stopped, quarantined, or critical exception
- Every decision must have labeled Yes/No connectors
- Add a title, legend, version, and prepared-by line

Export each finished Lucidchart diagram as PNG for the presentation and PDF for repository evidence.

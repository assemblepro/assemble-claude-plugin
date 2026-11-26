# Assemble for Claude

Assemble is construction takeoff and estimating software for builders, contractors and estimators. This plugin connects Claude to your Assemble workspace so you can measure PDF drawings, price jobs from your own library of materials and assemblies, and build estimates without leaving the chat.

## What it does

- **Measure drawings.** Claude looks at a sheet, proposes lines, areas and counts, and Assemble snaps them to the drawing's linework at the sheet's scale. You see a marked-up preview before anything is saved.
- **Price jobs.** Turn the takeoff into an estimate using your library, assemblies and templates, then set markup, margin and tax.
- **Keep prices current.** Apply a supplier price list or reprice a category by a percentage and see how it flows into assemblies.
- **Answer questions.** Pipeline totals, order lists, what's on a job, and who the customer is.

Every change is shown as a preview first and only saved when you confirm. Works in metric and imperial.

## What's included

- `.mcp.json`: the Assemble MCP server at `https://app.assemblepro.com/api/mcp` (OAuth sign-in; you choose which permissions to grant).
- `skills/price-a-job-from-drawings`: the drawings → takeoff → estimate workflow.
- `skills/update-supplier-prices`: supplier price lists and bulk repricing.

The plugin runs no local code. It sends requests only to the Assemble server above, which returns data from your own workspace.

## Install

- **Claude (web and desktop):** find Assemble in the connector directory and connect it.
- **Claude Code:**

  ```
  /plugin install assemble-pro --marketplace assemblepro/assemble-claude-plugin
  ```

## Requirements

An Assemble account (https://assemblepro.com). Sign in when Claude asks you to connect.

## Support and privacy

- Docs: https://assemblepro.com/mcp
- Support: support@assemblepro.com
- Privacy policy: https://app.assemblepro.com/privacy

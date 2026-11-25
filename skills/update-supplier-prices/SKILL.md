---
name: update-supplier-prices
description: Use when someone wants to update material or labour prices in their Assemble library, apply a supplier price list, reprice items by a percentage, or check how a price change flows into assemblies and open estimates.
---

# Update prices in the Assemble library

1. Call `get_workspace_info` for the currency and unit system.
2. Find the items with `search_catalog` (by name, code or category) and check one with `get_library_item`.
3. Choose the right tool:
   - A supplier list (pasted table, CSV text, or file contents): `preview_price_update`. It matches lines to existing items and shows unmatched rows. Ask before creating new items with `preview_catalog_items_upsert`.
   - "Put everything in category X up by N%": `preview_bulk_reprice`.
4. Show the preview as a short before/after table and get a yes before `apply_change`.
5. Show what the change does to assemblies with `explain_assembly_price`.
6. Open estimates keep their old rates until refreshed. If the user wants a job updated, use `preview_line_rates_refresh` on that estimate and apply after they agree.

Never guess a price. If a supplier line doesn't clearly match one library item, ask.

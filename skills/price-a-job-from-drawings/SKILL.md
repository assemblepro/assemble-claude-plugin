---
name: price-a-job-from-drawings
description: Use when someone wants to measure construction drawings, run a takeoff, or turn plans into a priced estimate in Assemble, e.g. "price this extension from the plans", "measure the kitchen floor on A-101", "build the quote from the takeoff".
---

# Price a job from drawings in Assemble

Work through these steps with the Assemble connector. Confirm with the user before each `apply_change`.

1. Call `get_workspace_info` first. Use its unit system (metric or imperial) and currency in everything you say.
2. Find the job with `find_projects`, then `get_project_overview`. If there is no job yet, offer `preview_job_create`.
3. If the job has no drawings, use `start_drawing_upload` (gives the user an upload link) or `import_drawings_from_url`, then poll `get_upload_status`.
4. `list_drawings` to pick the sheet. Check the scale: if a sheet has none, read the scale label with `get_page_text` and set it with `preview_page_scale`.
5. Look before measuring: `get_page_image` (crop to zoom in), `get_page_text` for room names and tags.
6. Measure with `preview_detect_room` (a room's area from one point inside it), `preview_measurements` (lines, areas, counts in image pixels) or `preview_count_text` (count a tag such as "D1"). Assemble snaps points to the drawing's linework and computes the quantities. Show the returned preview image and ask the user to confirm, then `apply_change`.
7. `get_quantities` to read back totals. Never compute or invent quantities yourself.
8. Build the estimate with `preview_estimate_from_takeoff`, adjust with `preview_estimate_lines_edit` or `preview_estimate_pricing` (markup, margin, tax), add `preview_scope_notes`, and apply each after the user agrees.
9. Show the result with `get_estimate`. Only send it to the customer (`preview_estimate_send`) if the user explicitly asks, and show the recipient first.

Tips
- Previews expire; if `apply_change` says a preview is gone, make it again.
- If a tool says a permission is missing, tell the user to reconnect Assemble and tick that permission.

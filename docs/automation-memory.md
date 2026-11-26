# FSEL Graph Viewer — Automation memory

Updated: 2026-11-26 (Asia/Ho_Chi_Minh).

## Source queries

- Jira project key: `FSEL`.
- Confluence space keys: `FD` (Fsel Document), `LFD` (LCMS/LMS FSEL Document).
- Do not use Confluence `space = "FSEL"`: it returned HTTP 500 in the checked environment; the accessible space list contained FD/LFD instead.
- Verified working CQL:

```sql
type = page AND space IN ("FD", "LFD")
AND created >= "<lower bound with overlap>"
ORDER BY created ASC
```

Use limit 50 and paginate until has_more=false. The 2026-11-26 probe returned 12 candidate pages and no further pages. Candidates are not verified Task Docs.

## Scan rules

Read the local automation memory before each run. Scan newly created documents via FSEL Product Intelligence MCP using JQL/CQL created, not updated. Start at 2026-11-12 00:00 Vietnam time until a successful watermark is established. Connector timezone is unconfirmed; the previously used overlapping lower bound is 2026-11-11 16:55. Deduplicate by Jira key and Confluence page ID. Complete both sources and pagination before advancing the watermark; retain it on errors or incomplete results.

Verify FSEL scope and Jira/page linkage from original sources. Title matches alone are insufficient. Retain pending candidates for later matching; their IDs and evidence remain in the local automation report. Do not treat all new pages as Task Docs.

## Schedule and publication

Automation ID: `c-p-nh-t-fsel-graph-viewer`. Active daily at 09:15 Vietnam time. Prompt updated to FD/LFD on 2026-11-26. Notification policy remains failed_runs_only.

Keep Jira/Wiki evidence local. Do not run legacy currentUser() sync_jira.py or export_public_fsel.py/local-index publication. Update public graph data only when an export source supports the new Task Docs and publication permission for the items is confirmed. This memory update does not add Jira/Wiki records to index.html.

# Automation memory

GitHub main is canonical. Viewer index.html fetches data/graph.json. Persist scan watermark, deduplication IDs, pending candidates and gaps in automation/state.json; append each run to automation/runs/<UTC timestamp>.json. Read these remote files before every run. Local files are temporary; required scheduler memory only points here.

Approved by PO Lead on 2026-11-26: automatically publish verified metadata (ID, title, status, source links) and evidence links. Never publish PATs, full document bodies or new personal data. Preserve baseline graph. Jira projects FSEL/FHI/FSLP occur in baseline; confirm FSEL product scope from original sources. Wiki spaces FD/LFD, never FSEL. Use created queries with overlap, paginate fully, deduplicate. Keep watermark on partial/error runs and retain pending candidates across windows. Do not run legacy sync_jira.py/export_public_fsel.py.

Daily schedule remains 09:15 Asia/Ho_Chi_Minh, local Codex execution. Commit graph, state and report atomically with expected-head protection; fetch fresh head and merge on conflicts. Check JSON integrity, edge endpoints and deployment. No new records means report/state update only, no fabricated graph change.

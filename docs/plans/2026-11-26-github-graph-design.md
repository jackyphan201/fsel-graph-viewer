# Approved GitHub graph design

PO Lead approved 2026-11-26. GitHub stores canonical graph, scan state, pending candidates and run history. Static viewer loads data/graph.json with no-store and reports errors visibly. Schedule queries original sources, publishes only verified metadata, preserves existing graph and commits state/data/report atomically. Errors retain watermark. Local runtime storage is temporary; Codex scheduler still runs locally. No credential migration to GitHub.

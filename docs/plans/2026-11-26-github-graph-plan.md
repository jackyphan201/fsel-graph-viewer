# GitHub graph implementation plan

Goal: updates to data/graph.json appear on Pages. Architecture: static JavaScript viewer plus canonical JSON and Codex scheduled GitHub commits. Tech: JavaScript, JSON, Git Data API.

1. Preserve baseline graph and add source-verified pairs.
2. Extract graph.json; load with fetch and error handling.
3. Persist pending candidates and partial-run watermark state.
4. Validate unique IDs, all edge endpoints, JSON and JavaScript syntax.
5. Commit viewer/data/state/docs/report atomically.
6. Update existing schedule preserving timing and notification policy.
7. Verify deployed loader/data and count.

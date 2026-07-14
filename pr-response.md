# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:** Renamed `save_to_watchlist()` to `add_to_watchlist()` in `services/watchlist_service.py` to match the `verb_to_noun` convention used elsewhere (e.g. `add_to_collection()`). Updated the import and call site in `routes/watchlist.py`, and updated the docstring summary to match the new name.
**How I verified:** `grep -rn "save_to_watchlist" .` returned no matches. Full test suite still passes.

## Comment 2 — Deduplication
**What I did:** Added an `AlreadyInWatchlistError` exception and a duplicate check in `add_to_watchlist()`, following the same pattern as `add_to_collection()` — query for an existing `WatchlistEntry` before creating a new one, raise if found. Wired the new exception into `routes/watchlist.py` with a 409 response, mirroring how `AlreadyInCollectionError` is handled in `routes/collection.py`.
**How I verified:** Ran the full test suite, and manually tested via curl by adding the same film twice — first call returns 201, second returns 409 instead of a duplicate row.

## Comment 3 — Missing test
**What I did:**
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
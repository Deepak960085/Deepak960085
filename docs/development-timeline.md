# Development Timeline

> Assumption: 1 PM + 2 Mobile Engineers + 1 QA (part-time), 10-week MVP plan.

## Phase 0 — Discovery & Setup (Week 1)

### Deliverables
- Finalized requirements and acceptance criteria.
- Technical design sign-off.
- Project scaffolding, CI, linting, base navigation.

### Exit Criteria
- All MVP user stories written and estimated.
- Baseline app boots on target Android devices.

---

## Phase 1 — Media Index + Home UI (Weeks 2–3)

### Scope
- Storage/media permissions flow.
- Media scanning service.
- Videos/Music/Folders tabs with sorting and search.
- SQLite schema and repository implementation.

### Exit Criteria
- App lists local media correctly.
- Manual refresh + auto scan both functional.

---

## Phase 2 — Video Playback (Weeks 4–5)

### Scope
- Video player screen with core controls.
- Gestures for brightness/volume/seek.
- Subtitle file loading and rendering.
- Resume playback persistence.
- PiP integration.

### Exit Criteria
- Playback stable on target formats.
- Resume behavior validated.

---

## Phase 3 — Audio Playback + Background Controls (Weeks 6–7)

### Scope
- Audio queue and Now Playing UI.
- Shuffle/repeat/speed controls.
- Background playback service.
- Notification + lock screen controls.

### Exit Criteria
- Audio continues across app background transitions.
- Media keys/headset controls verified.

---

## Phase 4 — File Management Operations (Week 8)

### Scope
- Create/rename/delete folder.
- Move/copy/delete with multi-select.
- Operation confirmations and error handling.

### Exit Criteria
- File operations validated against real storage scenarios.

---

## Phase 5 — Stabilization & Release Prep (Weeks 9–10)

### Scope
- Performance tuning (scan + startup latency).
- Device compatibility sweep.
- Bug fixing and QA regression.
- Release candidate build and checklist.

### Exit Criteria
- MVP quality targets met.
- Release notes + known limitations documented.

---

## Milestone Summary

- **M1 (End W3):** Browsing and indexing complete.
- **M2 (End W5):** Video playback MVP complete.
- **M3 (End W7):** Audio/background MVP complete.
- **M4 (End W8):** File management complete.
- **M5 (End W10):** Release candidate ready.

## Risk Register (Top 4)

1. Device-specific codec incompatibilities.
2. Scoped storage edge cases on newer Android versions.
3. Background playback restrictions on OEM-customized devices.
4. Large library scan performance variability.

## Mitigation

- Build codec fallback strategy early.
- Test storage APIs on Android 10–14 matrix.
- Implement robust foreground service + media session handling.
- Use incremental scans and indexed metadata updates.

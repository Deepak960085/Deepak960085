# Game Feature Roadmap

## 4) Online Multiplayer + Entry Fees

### Scope
- Add **online multiplayer mode** (1v1 real-time matchmaking).
- Allow a **small entry fee per match** (₹5–₹20).
- The **winner receives a larger payout** from the pooled entry fees.

### Suggested Match Flow
1. Player selects `Online (Cash)` mode.
2. Player chooses an entry tier: `₹5`, `₹10`, or `₹20`.
3. System checks balance and creates/joins a matching lobby.
4. Both players pay entry fee into an escrow wallet.
5. Match is played with server-authoritative scoring and anti-cheat checks.
6. On result finalization:
   - Winner gets prize (for example: total pool minus platform fee/tax).
   - Match record and wallet ledger are written atomically.

### Payout Model (Example)
- Pool = `2 x entry fee`
- Platform fee = configurable (example: 10%)
- Winner payout = `pool - platform fee`

Examples:
- ₹5 room → pool ₹10 → payout ₹9 (₹1 fee)
- ₹10 room → pool ₹20 → payout ₹18 (₹2 fee)
- ₹20 room → pool ₹40 → payout ₹36 (₹4 fee)

### Key Safety & Fairness Requirements
- **Server-authoritative outcomes** (client cannot self-report score).
- **Anti-collusion and anti-bot checks** (device fingerprinting, unusual-play heuristics).
- **KYC/age gates** before cash play.
- **Geo-fencing** for restricted regions.
- **Fraud controls**: velocity limits, AML alerts, withdrawal cooldown for suspicious accounts.
- **Dispute handling** with replay/event logs and manual review queue.

### Compliance Notes (Important)
> Real-money gameplay is regulated differently by jurisdiction.

- Some countries/states prohibit or tightly regulate paid-entry competitive games.
- In India, treatment can depend on whether the game is classified as **game of skill** vs **gambling/chance**.
- Implement jurisdiction-aware controls:
  - Region detection and blocking where required.
  - Clear Terms of Service and responsible-play messaging.
  - Tax, KYC, and reporting modules configurable per state/country.
- Launch only after review by qualified legal counsel in each target region.

### Technical Backlog
- Matchmaking service (tier-based queue + latency buckets).
- Real-time game session service (WebSocket).
- Wallet/ledger service with immutable transaction history.
- Escrow + payout service with idempotent settlement jobs.
- Compliance service (geo rules, KYC state, jurisdiction policy engine).
- Admin dashboard for fraud flags, disputes, and payout audits.

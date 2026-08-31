# Blondie Token – Cosmic dApp

Frontend (static) + optional Node backend for custodial ledger, admin, and Solana payouts.

## Folder structure

```
blondie-token/
├── index.html              # Home – tokenomics, roadmap preview
├── miner.html              # 12h Cosmic Miner
├── profile.html            # Register (custodial) / connect wallet / withdraw
├── spark.html              # Spark Points, tasks, leaderboard, referrals
├── roadmap.html            # Full roadmap + socials
├── shop.html               # Shop placeholder
├── admin.html              # Admin panel (competition, withdrawals)
├── css/
│   └── style.css           # Cyberpunk theme (Orbitron, neon, purple)
├── js/
│   ├── app.js              # Client state (localStorage fallback)
│   └── api.js              # Backend API client (BlondieAPI)
├── backend/                # Node API (production / shared users)
│   ├── package.json
│   ├── .env.example
│   ├── .gitignore
│   ├── README.md
│   ├── data/               # SQLite DB lives here (*.db gitignored)
│   ├── supabase/
│   │   └── schema.sql
│   └── src/
│       ├── server.js
│       ├── db/
│       │   ├── sqlite.js
│       │   └── init-sqlite.js
│       ├── middleware/
│       │   └── auth.js
│       ├── routes/
│       │   ├── auth.js
│       │   ├── users.js
│       │   └── admin.js
│       └── services/
│           └── solanaPayout.js
└── README.md
```

## Frontend only (demo)

```bash
npx serve .
# or: python3 -m http.server 8080
```

Data stays in localStorage until backend is connected.

## Backend

```bash
cd backend
cp .env.example .env
npm install
npm run db:local
npm run dev
# → http://localhost:8787/health
```

Default admin: `admin` / `blondie-admin-2026` (change in `.env`).

Frontend:

```html
<script>window.BLONDIE_API_URL = 'http://localhost:8787';</script>
<script src="js/api.js"></script>
<script src="js/app.js"></script>
```

Full API docs: `backend/README.md`.

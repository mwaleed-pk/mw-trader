<div align="center">

# MW Trader Bot

**Token-gated trading dashboard frontend for Binance Futures automation — live at [mwtrader.site](https://mwtrader.site)**

[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38BDF8?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

> A dark, fintech-grade Next.js interface for the MW Trader trading automation platform. Token-gated entry, a trader dashboard, and an admin console — built mobile-first and designed for fast, glanceable market decisions.

> ⚠️ **Risk notice:** This software is a trading interface, not financial advice. Trading leveraged crypto products carries substantial risk.

---

## ✨ Features

- **Token-gated access** — login flow stores a session token in `localStorage`; routes guard on token presence
- **Trader dashboard** (`/dashboard`) — central view for bot status, positions, and market context
- **Admin console** (`/admin`) — privileged panel with elevated controls, visible only to admin-token holders
- **Brand identity component** — custom `Logo.tsx` chart-mark rendered in pure JSX/CSS (no image assets)
- **Dark fintech design system** — disciplined palette (deep blacks, gold advisory accents), Tailwind utility styling
- **Risk-first UX** — prominent advisory banner ("I am not a financial advisor. Risk management is essential.")
- **App Router architecture** — Next.js 14 file-based routing with client components where interactivity is needed
- **Responsive by default** — layouts built for both desktop terminals and mobile screens

## 🛠️ Tech Stack

| Category   | Technology                          |
|------------|-------------------------------------|
| Framework  | Next.js 14 (App Router)             |
| UI Library | React 18                            |
| Styling    | Tailwind CSS 3, PostCSS             |
| Language   | TypeScript 5                        |
| Linting    | ESLint (eslint-config-next)         |
| Runtime    | Node.js 20+                         |

## 🏗️ Architecture / How It Works

```
Browser ──▶ Next.js App Router ──▶ Token check (localStorage)
                                        │
                        ┌───────────────┼───────────────┐
                        ▼               ▼               ▼
                    / (login)     /dashboard        /admin
                   Token entry   Trader view     Admin console
```

- **Entry (`/`)** — `src/app/page.tsx` renders the login screen with the risk advisory box and brand logo. On submit, the token is persisted to `localStorage` under `md_trader_token` and the user is routed to `/dashboard`.
- **Dashboard (`/dashboard`)** — `src/app/dashboard/page.tsx` reads the stored token on mount; admin-only controls render conditionally when the admin token is present. Logout clears the token and returns to `/`.
- **Admin (`/admin`)** — `src/app/admin/page.tsx` validates the admin token before revealing the console.
- **Branding** — `src/components/Logo.tsx` draws the MW Trader mark (candlestick bars + "MW TRADER" wordmark) entirely in JSX/CSS.

> Note: the token gate is a UI-level access control. It is not a substitute for server-side authentication — pair this frontend with a backend that validates sessions for any sensitive operation.

## 🚀 Getting Started

### Prerequisites

- Node.js 20+
- npm 9+

### Installation

```bash
cd frontend
npm install
```

### Environment Variables

None required. The frontend is fully static — the access token is entered in the UI at runtime and kept in the browser's `localStorage`.

### Run

```bash
# Development (http://localhost:3000)
npm run dev

# Production build
npm run build
npm start

# Lint
npm run lint
```

## 📁 Project Structure

```
mwtraderbot/
└── frontend/
    ├── src/
    │   ├── app/
    │   │   ├── page.tsx          # Login / token entry
    │   │   ├── layout.tsx        # Root layout
    │   │   ├── globals.css       # Global Tailwind styles
    │   │   ├── dashboard/
    │   │   │   └── page.tsx      # Trader dashboard
    │   │   └── admin/
    │   │       └── page.tsx      # Admin console
    │   └── components/
    │       └── Logo.tsx          # MW Trader brand mark
    ├── package.json              # "md-trader-frontend"
    ├── tailwind.config.ts
    ├── postcss.config.js
    ├── tsconfig.json
    └── next.config.js
```

## 🔌 API / Usage

This repository is frontend-only and ships no API routes. It is designed to sit in front of a trading backend (e.g. the MW Trader execution engine behind [mwtrader.site](https://mwtrader.site)). To connect it:

1. Point dashboard data-fetching at your backend's REST/WebSocket endpoints.
2. Replace the `localStorage` token check with session validation against your auth service for production use.

## 🗺️ Roadmap

- [ ] Server-validated sessions (replace client-side token gate)
- [ ] Live WebSocket market ticker on the dashboard
- [ ] Position and order-history views wired to the execution backend
- [ ] PWA support for mobile traders

## 🤝 Contributing

Contributions are welcome. Fork the repo, create a feature branch (`git checkout -b feature/your-feature`), commit with clear messages, and open a pull request. Please keep the dark fintech design language consistent and run `npm run lint` before submitting.

## 📄 License

MIT — see [LICENSE](LICENSE) for details.

## 👤 Author

**Muhammad Waleed (MW Trader)** — Software Engineer building trading automation at [mwtrader.site](https://mwtrader.site)
GitHub: [github.com/mwaleed-pk](https://github.com/mwaleed-pk)

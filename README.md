## Edge Boot

Minimal, boring, and reliable bootstrap for Edge Labs with two parallel tracks:

- **Ramp (on rails)**: prescriptive, fewer choices → [RAMP_GUIDE.md](RAMP_GUIDE.md)
- **Core (self-reliant)**: choose options, justify trade-offs → [CORE_GUIDE.md](CORE_GUIDE.md)

This repo ships a FastAPI backend and a React + TypeScript + Vite frontend, a green CI via PR (Node 22, Python 3.12), and clear guides. No database yet—just an in-memory store.

### Track overview

- **Ramp (on rails)** – prescriptive, step-by-step execution following `RAMP_GUIDE.md`
- **Core (self-reliant)** – same end goals, but you decide which improvements matter; see `CORE_GUIDE.md`

### Documentation map

- **Getting started (Ramp)**: [RAMP_GUIDE.md](RAMP_GUIDE.md)
- **Core checklist + prompts**: [CORE_GUIDE.md](CORE_GUIDE.md)
- **Spec, rubric, policies**: [GUIDE.md](GUIDE.md)
- **CI & templates**: `.github/` (`workflows/ci.yml`, `pull_request_template.md`, `ISSUE_TEMPLATE/help_request.md`)

### Prerequisites

- Node.js 22.x (`nvm install && nvm use` reads `.nvmrc`)
- Python 3.12 (`python3 --version` should report ≥ 3.12)
- Git + GitHub account with permission to create a public repo

### Getting started (tl;dr)

1. On GitHub, click **Use this template → Create a new repository**.
2. Clone your new repo, create a branch (`git checkout -b ship-bootstrap/<name>`), and enable branch protection on `main`.
3. Follow the Ramp guide for exact commands, or switch to the Core guide if you want to make your own trade-offs.
4. Push via PR only. Confirm CI is green (see Actions tab) before merging.

### What’s included

- FastAPI backend: `GET /healthz`, `GET/POST /items` (in-memory store)
- React + TS + Vite frontend: list items, add item
- GitHub Actions CI: Python 3.12 + Node 22
- PR template enforcing reflection and AI usage honesty
- Two guides: `GUIDE.md` (general), `RAMP_GUIDE.md` (step-by-step), plus `CORE_GUIDE.md`
- Makefile and npm scripts for a one-command dev loop

### CI in a nutshell

Whenever you push or open a PR, GitHub Actions runs `.github/workflows/ci.yml`:

- Backend job → Python 3.12, `pip install -e "backend[dev]"`, `pytest -q backend/tests`
- Frontend job → Node 22, `npm --prefix frontend ci`, `npm run build`, `npm run typecheck`

Green checks mean you’re ready to merge. Failed checks link to logs explaining what to fix.



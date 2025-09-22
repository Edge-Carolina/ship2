## Edge Boot

Minimal, boring, and reliable bootstrap for Edge Labs with two parallel tracks:

- **Ramp (on rails)**: prescriptive, fewer choices → [RAMP_GUIDE.md](RAMP_GUIDE.md)
- **Core (self-reliant)**: choose options, justify trade-offs → [CORE_GUIDE.md](CORE_GUIDE.md)

This repo ships a FastAPI backend and a React + TypeScript + Vite frontend, a green CI via PR (Node 22, Python 3.12), and clear guides. No database yet—just an in-memory store.

### Use this repository as a template

Create your own copy of this repo under your GitHub account and work there.

1) On GitHub, open this repo's page and click "Use this template" → "Create a new repository".
2) Choose your owner, name it (e.g., `edge-boot-<you>`), set visibility to Public, and create it.
3) Clone your new repo locally:

```bash
git clone https://github.com/<you>/<your-repo>.git
cd <your-repo>
```

4) Protect `main` (docs in `GUIDE.md`).
5) Create a feature branch and develop via PRs:

```bash
git checkout -b ship-bootstrap/<your-name>
```

Alternative (import by git): if you created an empty repo first, you can pull this template into it:

```bash
git clone https://github.com/<you>/<your-empty-repo>.git
cd <your-empty-repo>
git remote add upstream https://github.com/<edge-org-or-source>/edge-boot.git
git pull upstream main
git push -u origin main
```

### Quickstart

Run from your repo root.

```bash
nvm install  # if Node 22.6.0 not yet installed
nvm use
npm --prefix frontend ci
python -m venv .venv && source .venv/bin/activate  # PowerShell: .\.venv\Scripts\Activate.ps1
pip install -e "backend[dev]"
make dev  # backend on :8000, frontend on :5173
```

Open:

- Backend: `http://localhost:8000/healthz`
- Frontend: `http://localhost:5173`

### What’s included

- FastAPI backend: `GET /healthz`, `GET/POST /items` (in-memory store)
- React + TS + Vite frontend: list items, add item
- GitHub Actions CI: Python 3.12 + Node 22
- PR template enforcing reflection and AI usage honesty
- Two guides: `GUIDE.md` (general), `RAMP_GUIDE.md` (step-by-step), plus `CORE_GUIDE.md`
- Makefile and npm scripts for a one-command dev loop

### Where to read next

- General guide: [GUIDE.md](GUIDE.md)
- Ramp, step-by-step: [RAMP_GUIDE.md](RAMP_GUIDE.md)
- Core checklist and prompts: [CORE_GUIDE.md](CORE_GUIDE.md)

### Full setup guide

If you want the explicit end-to-end steps (create repo from template, branch protection, install, run, tiny change, open PR, confirm green CI), read `RAMP_GUIDE.md`.



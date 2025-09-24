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

Run from your repo root. Make sure your Python interpreter is 3.12 (check with `python3 --version`). If your default `python3` is older, use `python3.12` explicitly or install 3.12 via pyenv/brew.

```bash
nvm install  # if Node 22.6.0 not yet installed
nvm use
npm --prefix frontend install  # sync package-lock.json on first run
npm --prefix frontend ci
python3 -m venv .venv && source .venv/bin/activate  # ensure python3 --version >= 3.12 (PowerShell: .\.venv\Scripts\Activate.ps1)
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
- CI and templates: explore `.github/` for the workflow (`workflows/ci.yml`), PR template, and help-request issue template.

### Full setup guide

If you want the explicit end-to-end steps (create repo from template, branch protection, install, run, tiny change, open PR, confirm green CI), read `RAMP_GUIDE.md`.

### What is CI (continuous integration)?

CI is an automated check that runs every time you push or open a pull request. Our workflow lives in `.github/workflows/ci.yml` and runs two jobs:

- Backend: installs Python 3.12, runs `pytest`
- Frontend: installs Node 22, runs `npm run build` and `npm run typecheck`

Green CI means both jobs succeed. If a job fails, open the “Actions” tab in GitHub to view logs, fix the issue locally, and push again.



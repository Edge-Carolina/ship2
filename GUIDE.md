## Guide (Both Tracks)

This ship bootstraps a minimal, reliable repo with a FastAPI backend, a React+TS+Vite frontend, and green CI. No DB yet—use an in-memory store.

### Purpose of this guide

This document is the high-level specification for both tracks. It defines what “done” means, the rubric, policies, and shared workflows (e.g., branch protection). Use `RAMP_GUIDE.md` for prescriptive step-by-step, and `CORE_GUIDE.md` for a concise checklist and prompts.

### Objectives and Deliverables

- Fresh, public repository with clear scaffolding
- Feature branch workflow, squash merge via PR
- Branch protection on `main` (no direct pushes, require PR and CI)
- CI green (backend and frontend)
- Backend:
  - `GET /healthz` → `{ "status": "ok" }`
  - `/items` → `GET` list, `POST` create `{text}`; returns `{id, text, created_at}`
- Frontend:
  - Renders items
  - Can add an item

### Pass/Fail Rubric

- Must pass:
  - Repo created fresh and public
  - Branch protection on `main`
  - Work on feature branch, squash merge via PR
  - CI green (both jobs)
  - `/healthz` works; `/items` GET/POST work
  - Frontend can add and render items
- Stretch:
  - Optimistic UI for add
  - Minimal error boundary
  - Input length validation on client and server

### Stuck Protocol

1) Reproduce the issue. 2) Copy the first 20 lines of the error. 3) Search for that exact error message. 4) Make a tiny change and retry. 5) Ask for help using the issue template with: OS, versions, exact command, error snippet, steps tried.

### AI Policy

AI is allowed for scaffolding and routine code generation. Your PR description must include an “AI usage” section listing suggestions accepted and code you wrote yourself.

### Branch Protection (Docs Only)

GitHub → Settings → Branches → Branch protection rules → Add rule:

- Branch name pattern: `main`
- Require a pull request before merging (squash merge allowed)
- Require status checks to pass before merging (select your CI workflow)
- Restrict who can push to matching branches (optional for public forks)

Placeholder screenshot:

![Branch protection settings](docs/screenshots/branch-protection.png)

### Local Development

```bash
nvm use
npm --prefix frontend ci
python -m venv .venv && source .venv/bin/activate  # PowerShell: .\.venv\Scripts\Activate.ps1
pip install -e "backend[dev]"
make dev
```

Backend: `http://localhost:8000/healthz`  Frontend: `http://localhost:5173`

### Start from this template (your own repo)

On GitHub: Use this repo as a template → create your repo. Then:

```bash
git clone https://github.com/<you>/<your-repo>.git
cd <your-repo>
git checkout -b ship-bootstrap/<your-name>
```

Turn on branch protection for `main` (steps above), then follow Local Development.



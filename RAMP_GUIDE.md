## Ramp Guide (Step-by-Step)

Follow these commands exactly from repo root.

### 1) Install prerequisites

Node via nvm:

```bash
nvm use  # reads .nvmrc (Node 22.x)
```

Python venv:

```bash
python -m venv .venv
source .venv/bin/activate
# PowerShell:
# .\.venv\Scripts\Activate.ps1
```

### 2) Install dependencies

Backend:

```bash
pip install -e "backend[dev]"
```

Frontend:

```bash
npm --prefix frontend ci
```

### 3) Run the dev servers

```bash
make dev  # backend :8000, frontend :5173
```

Check:

- `GET /healthz` shows `{ "status": "ok" }`
- Frontend lists items (empty initially)

### 4) Make the tiny change

Goal: Add a placeholder and ensure min length 1 validation on the client, then extend the tests.

- Edit `frontend/src/components/AddItem.tsx` input to add: `placeholder="Describe your item"`
- Ensure the form prevents empty submissions (min length 1)
- Add one extra assertion in `backend/tests/test_items.py` (e.g., check `created_at` is a string containing `T`)

Run:

```bash
pytest -q  # inside backend
```

### 5) Open a PR and confirm CI

1) Create a feature branch: `git checkout -b ship-bootstrap/<your-name>`
2) Push and open a PR against `main`
3) Confirm both CI jobs are green (backend + frontend)

### Screenshots (what you should see)

- Browser hitting `http://localhost:8000/healthz` → JSON `{ "status": "ok" }`
- Frontend showing the list and an input/button to add an item
- PR page with green checks

### Troubleshooting (Windows)

- ExecutionPolicy: `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`
- Git credentials: ensure `git config --global credential.helper manager-core`



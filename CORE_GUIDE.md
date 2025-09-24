## Core Guide (Checklist + Prompts)

No hand-holding. Hit the targets, explain trade-offs.

**Start from the template** like Ramp. Ship the same healthz/items endpoints and frontend experience, then decide which improvements matter most and why.

Reference docs:
- `.github/workflows/ci.yml` – how CI runs
- `.github/pull_request_template.md` – expectations for PRs
- `.github/ISSUE_TEMPLATE/help_request.md` – format for asking for help

### Targets

- [ ] Public repo with scaffold
- [ ] Feature branch, squash merge via PR
- [ ] Branch protection on `main`
- [ ] Green CI (backend + frontend)
- [ ] `GET /healthz` → `{ status: "ok" }`
- [ ] `/items` GET/POST (id, text, created_at), most recent first
- [ ] Frontend lists items and can add one

### Optional improvements (choose your own)

- [ ] Optimistic UI for add
- [ ] Minimal error boundary
- [ ] Zod validation on client
- [ ] Fetch retry policy tuning
- [ ] Tiny design polish
- [ ] Docker devcontainer instead of venv
- [ ] Different CI setup (GitLab, Buildkite, etc.)
- [ ] Alternate lint/format tooling (biome, ruff, etc.)

### Explain and defend (answer in PR description)

- Which optional improvements did you prioritize, and why?
- What trade-offs did you make to meet the functional requirements?
- If you changed anything from the template, what was your reasoning?
- How did you balance quick delivery vs. long-term maintainability?



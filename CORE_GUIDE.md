## Core Guide (Checklist + Prompts)

No hand-holding. Hit the targets, explain trade-offs.

**Start from the template** like Ramp, but then make your own choices about architecture, dependencies, and improvements. Use the scaffold as a foundation, then modify and justify your decisions.

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

### Explain and defend (answer in PR description)

- What were your biggest architectural decisions and why?
- What trade-offs did you make to meet the functional requirements?
- If you changed anything from the template, what was your reasoning?
- How did you balance getting it working vs. keeping it maintainable?



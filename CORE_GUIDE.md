## Core Guide (Checklist + Prompts)

No hand-holding. Hit the targets, explain trade-offs.

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

### Explain and defend (answer in PR description)

- Why TanStack Query over manual fetch state?
- What is your fetch retry policy and why?
- How do you generate ids server-side, and why is that acceptable pre-DB?
- What trade-offs did you make to keep the repo boring and reliable?



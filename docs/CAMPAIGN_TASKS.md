# GuildPass Frontend Tasks

This document lists tasks suitable for open contributions.

---

## 🟢 Ready to Contribute

### TASK-FE-001: Add loading skeleton to the member dashboard
- **Difficulty**: Easy
- **Labels**: `good first issue`, `frontend`, `ui`
- **Description**: The member dashboard shows no loading state while data is being fetched. Add a skeleton loader using Tailwind CSS.
- **Files to change**: `app/dashboard/` or the relevant member dashboard page component
- **Acceptance criteria**:
  - Skeleton appears during loading (visible when network is slow or in mock mode with artificial delay)
  - Skeleton matches the layout of the actual content
  - Works in mock mode
- **Tests**: Visual verification; `npm run typecheck` passes
- **Reviewer expectations**: Tailwind CSS, no inline styles, no extra dependencies

---

### TASK-FE-002: Add an empty state for the admin member list
- **Difficulty**: Easy
- **Labels**: `good first issue`, `frontend`, `ui`
- **Description**: The admin member list shows nothing when there are no members. Add a friendly empty state with an icon and a call-to-action message.
- **Files to change**: The admin member list component (likely under `app/admin/` or `components/`)
- **Acceptance criteria**:
  - Empty state shown when member array is empty
  - Includes an icon and a short message
  - Accessible (`aria-label` or visible text)
- **Tests**: Verify in mock mode by returning an empty member array
- **Reviewer expectations**: Follows existing design language; Tailwind only

---

### TASK-FE-003: Add TypeScript strict null checks to lib/api/types.ts
- **Difficulty**: Easy–Medium
- **Labels**: `good first issue`, `frontend`, `api-layer`
- **Description**: Some types in `lib/api/types.ts` use loose typing or missing `| null` on optional fields. Audit and tighten the type definitions to match the guildpass-core API response shapes.
- **Files to change**: `lib/api/types.ts`, potentially `lib/api/live.ts` and `lib/api/mock.ts`
- **Acceptance criteria**:
  - No type errors introduced
  - All optional fields are explicitly `T | null` or `T | undefined`
  - `npm run typecheck` passes
- **Tests**: `npm run typecheck`
- **Reviewer expectations**: No `any` types; changes aligned with core API contracts

---

### TASK-FE-004: Add a CI workflow for lint and type-checking
- **Difficulty**: Easy
- **Labels**: `good first issue`, `tests`
- **Description**: Add a GitHub Actions workflow that runs `npm run typecheck` and `npm run lint` on every push and PR.
- **Files to change**: `.github/workflows/ci.yml` (new)
- **Acceptance criteria**:
  - Triggers on `push` and `pull_request` to `main`
  - Node 18, `npm ci`, typecheck, lint steps
  - Fails the workflow on lint or type errors
- **Tests**: Workflow passes on a draft PR
- **Reviewer expectations**: Clean YAML, correct trigger events

---

### TASK-FE-005: Improve accessibility of the wallet connect button
- **Difficulty**: Easy
- **Labels**: `good first issue`, `a11y`, `wallet`
- **Description**: The wallet connect button is missing ARIA attributes and does not announce its state to screen readers. Add `aria-label`, `aria-pressed`, or `role` as appropriate.
- **Files to change**: The wallet connect button (likely in `components/nav.tsx` or `lib/wallet/`)
- **Acceptance criteria**:
  - Button has a meaningful `aria-label` that changes state with connection status
  - Keyboard navigable and focusable
  - Screen reader announces connection state change
- **Tests**: Manual keyboard and screen reader test
- **Reviewer expectations**: No visual regressions; ARIA attributes follow W3C standards

---

## 🟡 Planned (not yet open)

- Add contribution history section to member dashboard
- Implement dark mode toggle
- Add comprehensive mock data for all community types
- Add Playwright or Cypress e2e tests for key user flows

---

*To work on a task, comment on the linked GitHub issue.*

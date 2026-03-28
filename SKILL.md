# SKILL: Solo Dev Coding Standards
**Stack:** JavaScript/TypeScript · Python · React/Next.js · Node.js/Express · GitHub  
**Context:** Solo indie developer, heavy AI/vibe coding, full-stack + automation projects  
**Last updated:** 2026-03

---

## When to apply this skill

Use this skill when:
- Starting a new project (any stack)
- Reviewing or generating code for this developer
- Helping resume work on an existing project
- Suggesting file/folder placement
- Writing commit messages or branch names
- Generating boilerplate, components, scripts, or utilities

---

## The 3-Pillar Framework

| Pillar | Name | Purpose |
|--------|------|---------|
| 1 | **Start Right** | Project setup + PROJECT.md before any code |
| 2 | **Stay Sane** | Daily coding checklist (before/during/after) |
| 3 | **Stay Honest** | Standards doc — rules held to on every project |

---

## Pillar 1: Start Right — Project Setup

### Every project must have PROJECT.md with these 12 sections:
1. 🎯 What Is This? — one paragraph, what problem, who uses it
2. 🏗️ Architecture — frontend, backend, DB, external APIs
3. 🔑 Key Decisions — why this stack/library, what was rejected
4. 📦 Tech Stack — every major dependency and its purpose
5. 🚀 How to Run — step-by-step, assume total amnesia
6. 🌿 Branch Strategy — main = production-ready, all work on feature branches
7. 🗄️ Env Variables — every var listed (no values — use .env.example)
8. 📁 Folder Structure — explain any non-obvious folder
9. ⚡ Current Status — [ACTIVE / PAUSED / COMPLETE] + what’s in progress
10. 🐛 Known Issues — running bug list
11. 🗺️ Roadmap — prioritized next steps
12. 🔗 Important Links — Figma, APIs, staging, production URLs

### Standard Folder Structure (Full-Stack: Next.js + Node/Express)
```
project-root/
├── src/
│   ├── app/                  # Next.js App Router pages & layouts
│   ├── components/
│   │   ├── ui/               # Base/primitive components
│   │   └── features/         # Feature-specific components
│   ├── lib/                  # Pure utility functions (no side effects)
│   ├── hooks/                # Custom React hooks
│   ├── services/             # API calls, external integrations
│   ├── types/                # TypeScript type definitions
│   └── constants/            # App-wide constants
├── server/
│   ├── routes/               # Route handlers
│   ├── controllers/          # Business logic
│   ├── middleware/            # Auth, validation, logging
│   ├── models/               # DB models/schemas
│   └── utils/                # Server utility functions
├── scripts/                  # Automation & one-off scripts (Python/JS)
├── tests/                    # Mirrors src/ structure
├── .env.example              # Template (never commit .env)
├── PROJECT.md                # 🔑 Living project doc — required
└── README.md                 # Public-facing setup guide
```

### New Project Kickoff Order
1. Create GitHub repo → clone → add .gitignore → commit "chore: initial project setup"
2. Set up folder structure above
3. Install Prettier + ESLint (JS/TS) or Black + Flake8 (Python)
4. Create .env + .env.example — commit only .env.example
5. Fill in PROJECT.md before writing application code
6. Deploy a "hello world" to verify the pipeline
7. Tag: `git tag v0.0.1` — clean baseline
8. Create first feature branch and start building

---

## Pillar 2: Stay Sane — Daily Coding Checklist

### Before writing a line
- [ ] Open PROJECT.md and read the Current Status section
- [ ] Write down the ONE thing to finish today
- [ ] Create or switch to the correct feature branch
- [ ] Pull latest from GitHub
- [ ] State the problem in plain English before prompting AI

### While coding
- [ ] Read all AI-generated code before accepting it
- [ ] Verify file placement — does this belong here?
- [ ] Run the app after every meaningful change
- [ ] Break any function over 40 lines into smaller pieces
- [ ] Add comments explaining WHY, not what
- [ ] Never let AI create new folders without review
- [ ] Commit every working checkpoint with a clear message

### Before closing the laptop
- [ ] Update PROJECT.md Current Status section
- [ ] Do a quick `git diff` review
- [ ] Push to GitHub
- [ ] Write down known bugs/TODOs in PROJECT.md
- [ ] Is the folder structure still clean?

---

## Pillar 3: Stay Honest — Coding Standards

### Code Formatting
| Language | Formatter | Linter |
|----------|-----------|--------|
| JavaScript / TypeScript | Prettier | ESLint (Airbnb or custom) |
| Python | Black | Flake8 |

- Max line length: 100 characters
- No commented-out dead code in commits
- No `console.log` in production code — use a logger

### Naming Conventions
| Context | Convention | Example |
|---------|-----------|---------|
| JS/TS variables & functions | camelCase | `getUserData()`, `isLoading` |
| JS/TS classes & components | PascalCase | `UserProfile`, `AuthService` |
| Constants | UPPER_SNAKE_CASE | `MAX_RETRIES`, `API_BASE_URL` |
| Python functions & variables | snake_case | `get_user_data()`, `is_loading` |
| Python classes | PascalCase | `UserProfile`, `AuthService` |
| Database tables/columns | snake_case | `user_profiles`, `created_at` |
| React component files | PascalCase.tsx | `UserCard.tsx`, `AuthModal.tsx` |
| Utility files | camelCase.ts | `formatDate.ts`, `apiHelpers.ts` |
| CSS/Tailwind modules | kebab-case | `user-card.module.css` |

### Git: Branch Naming
```
feat/short-description       # New feature
fix/short-description        # Bug fix
refactor/short-description   # Code refactor
hotfix/short-description     # Urgent production fix
chore/short-description      # Tooling, deps, config
experiment/short-description # Exploratory work
```

### Git: Commit Message Format
```
<type>(<scope>): <short description>

Types: feat | fix | refactor | chore | docs | test | style
```
Examples:
```
feat(auth): add JWT refresh token logic
fix(api): handle null response from user endpoint
refactor(components): extract UserCard into shared component
chore(deps): update next.js to 15.1
docs(readme): add environment setup instructions
```

### AI Usage Rules

**AI can decide:**
- Boilerplate & scaffolding
- CRUD operations & API handlers
- Utility/helper functions
- CSS and styling details
- TypeScript type definitions from existing code
- Test case generation
- Refactoring for readability

**Developer must decide (never delegate to AI):**
- Folder/file structure
- Authentication & security logic
- Database schema design
- Error handling strategy
- Third-party library selection
- Environment & config management
- Performance-critical paths

**Before accepting any AI-generated code, verify:**
1. Do I understand every line?
2. Does it handle error cases and edge cases?
3. Does it belong in the file/folder where AI put it?
4. Could this cause a security issue?
5. Will I be able to debug this in 3 weeks?

### Pre-Commit Self-Review
- [ ] Does the code do what I said it would?
- [ ] Any console.logs, debug statements, or temp code?
- [ ] Are all new functions named clearly and doing one thing?
- [ ] Are environment variables used instead of hardcoded values?
- [ ] Have I read the full diff with `git diff`?
- [ ] Is the error handling explicit (not silent fails)?
- [ ] Did AI add any files I didn’t ask for?
- [ ] Does my commit message accurately describe what changed?

### Testing Expectations
- Write at least a smoke test for every new route or API endpoint
- Test the happy path AND the most likely failure mode
- For Python scripts: test with real sample data before automating
- For React components: verify with no props, partial props, full props
- No rigid coverage mandates — but every critical function needs a test

---

## GitHub Repo Settings
| Setting | Value |
|---------|-------|
| Default branch | `main` |
| Branch protection on main | Enabled (no direct push) |
| Delete branch after merge | Enabled |
| Auto-merge | Disabled |
| Issues | Enabled (use for TODO tracking) |

## Recommended .gitignore Additions
```
# Environment
.env
.env.local
.env.*.local

# Dependencies
node_modules/
.venv/
__pycache__/
*.pyc

# Build outputs
.next/
dist/
build/

# Editor
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Logs
logs/
*.log
npm-debug.log*
```

---

## Core Principles (apply to all advice)

1. **Structure before speed.** Fill in PROJECT.md before writing code.
2. **You own everything AI writes.** Read it, understand it, own it.
3. **One folder convention, always.** Never improvise structure mid-project.
4. **Small commits, often.** Commit every working checkpoint.
5. **Resume-ability over cleverness.** Write code your future self can pick up after a 2-week break.
6. **Clean up before it becomes normal.** Fix structure drift immediately, not eventually.

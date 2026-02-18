# Vibe-Coding-101
# 🚀 Vibe Coding: Your Complete Documentation Guide

### A Beginner-Friendly Reference for Building Apps with AI

> **What is Vibe Coding?**  
> Vibe coding is building apps by describing what you want to an AI (like Claude, Cursor, or Copilot) and letting it write the code. The secret to making it work? **Write your docs first.** Great documentation = great AI output. No documentation = chaos.

---

## 📋 Table of Contents

1. [Why Documentation First?](#why-documentation-first)
2. [The 6 Documents You Need](#the-6-documents-you-need)
3. [Document 1: PRD.md](#document-1-prdmd)
4. [Document 2: APP_FLOW.md](#document-2-app_flowmd)
5. [Document 3: TECH_STACK.md](#document-3-tech_stackmd)
6. [Document 4: FRONTEND_GUIDELINES.md](#document-4-frontend_guidelinesmd)
7. [Document 5: BACKEND_STRUCTURE.md](#document-5-backend_structuremd)
8. [Document 6: IMPLEMENTATION_PLAN.md](#document-6-implementation_planmd)
9. [How to Use These Docs with AI](#how-to-use-these-docs-with-ai)
10. [Quick Start Checklist](#quick-start-checklist)
11. [Common Beginner Mistakes](#common-beginner-mistakes)
12. [Copy-Paste AI Prompts](#copy-paste-ai-prompts)

---

## Why Documentation First?

When you ask an AI to "build me an app," it has to guess:

- What the app actually does
- Who uses it
- What it looks like
- How the data is stored
- What order to build things in

**Guessing = hallucinations = broken code = frustration.**

When you give an AI documentation upfront, it stops guessing and starts building exactly what you described. Think of docs as your **blueprint**. You wouldn't build a house without blueprints. Don't build an app without docs.

### The Payoff

| Without Docs            | With Docs                          |
| ----------------------- | ---------------------------------- |
| AI makes up features    | AI builds only what you specified  |
| Inconsistent code style | Consistent patterns throughout     |
| Wrong tech choices      | Correct, compatible versions       |
| Random build order      | Logical, dependency-aware sequence |
| Lots of back-and-forth  | Clear, predictable output          |

---

## The 6 Documents You Need

Each document answers a specific question:

| #   | Document                   | Answers                           |
| --- | -------------------------- | --------------------------------- |
| 1   | **PRD.md**                 | What am I building and for whom?  |
| 2   | **APP_FLOW.md**            | How do users navigate the app?    |
| 3   | **TECH_STACK.md**          | What tools and versions do I use? |
| 4   | **FRONTEND_GUIDELINES.md** | What does the app look like?      |
| 5   | **BACKEND_STRUCTURE.md**   | How is data stored and served?    |
| 6   | **IMPLEMENTATION_PLAN.md** | What order do I build things in?  |

> **⏱️ Time Investment:** Writing all 6 docs takes 2–4 hours. It saves 20–40+ hours of debugging, refactoring, and AI confusion. Worth it every time.

---

## Document 1: PRD.md

### What Is It?

PRD = **Product Requirements Document**. It's your contract with the AI — a clear definition of _what_ you're building, _who_ it's for, and _what success looks like_.

### Why Do You Need It?

Without a PRD, you'll constantly tell the AI "no, not like that" and end up with features you didn't ask for. The PRD eliminates ambiguity.

### Key Sections to Include

**1. Problem Statement**
What problem does your app solve? Be brutally specific.

```
❌ Bad:  "An app to help people be more productive"
✅ Good: "Remote workers lose 45 min/day searching for meeting notes across
         3+ tools. This app centralizes notes in one searchable place."
```

**2. Target Users & Personas**
Who uses this? Write 1–2 personas:

```markdown
### Persona: Sarah, the Freelance Designer

- Age: 28, works from home
- Pain Points: Forgets client feedback, loses time re-reading old emails
- Goals: Find any note in under 10 seconds
- Technical Proficiency: Comfortable with apps, not a developer
```

**3. Features — Organized by Priority**

Use P0/P1/P2 to rank features:

| Priority | Meaning                                   | Build When  |
| -------- | ----------------------------------------- | ----------- |
| **P0**   | Must-have. App doesn't work without this. | MVP         |
| **P1**   | Should-have. Important but not blocking.  | Version 1.0 |
| **P2**   | Nice-to-have. Future enhancement.         | Later       |

For every P0 feature, include:

- What it does
- A user story: `"As a [user], I want [goal] so that [benefit]"`
- Acceptance criteria (specific, testable checkboxes)

**4. Explicitly OUT OF SCOPE**
This section is often skipped by beginners. Don't skip it. List 5–10 things you are NOT building. This prevents AI from adding features you never wanted.

```markdown
## Out of Scope (Version 1.0)

- Mobile app (web only for now)
- Team collaboration features
- Integrations with Slack or Notion
- AI-generated summaries
- File attachments
```

**5. Success Metrics**
How will you know it worked?

```markdown
- Users can find any note in < 10 seconds
- 80% of users return within 7 days
- Zero data loss incidents
```

### PRD Template Prompt for AI

Copy this and replace the `[BRACKETS]`:

```
Create a comprehensive PRD.md for [YOUR APP IDEA].

  - Target Users: [WHO USES IT]
  - Main Problem: [WHAT PROBLEM DOES IT SOLVE]
  - Unique Value: [WHY THIS SOLUTION]

Include:
1. Problem Statement (specific, not vague)
2. 2 User Personas with pain points and goals
3. SMART success metrics (measurable targets)
4. Features split into P0/P1/P2 tiers
5. For each P0 feature: user story + 3-5 acceptance criteria
6. Explicitly OUT OF SCOPE section (at least 5 items)
7. 3 user scenarios (step-by-step flows with edge cases)
8. Non-functional requirements (performance, security, accessibility)

Use specific, testable language. Avoid vague terms. Output as Markdown.
```

---

## Document 2: APP_FLOW.md

### What Is It?

A map of every screen, every button click, every user path — including what happens when things go wrong.

### Why Do You Need It?

AI will invent navigation patterns if you don't define them. APP_FLOW.md tells it exactly what happens when a user clicks "Sign Up" vs. "Log In" vs. "Forgot Password."

### Key Sections to Include

**1. Core User Flows**
A flow = one complete user task from start to finish. Map out your most important flows.

For each flow, document:

```
HAPPY PATH (when everything works):
Step 1 → Step 2 → Step 3 → Success ✅

ERROR STATES (when something breaks):
- What can go wrong at each step?
- What message does the user see?
- How do they recover?

EDGE CASES:
- User closes the browser halfway through
- User hits the back button
- Session expires during the flow
```

**Example Flow — User Registration:**

```
Entry: User clicks "Sign Up" on landing page

Happy Path:
1. Landing Page → User clicks "Sign Up"
2. Registration Form → User enters email + password
3. System validates → Creates account → Sends verification email
4. Email Verification Page → User clicks link in email
5. Dashboard → User is logged in ✅

Error States:
- Invalid email format → Inline error: "Please enter a valid email"
- Email already exists → Modal: "Account exists. Log in instead?"
- Weak password → Strength indicator appears, submit blocked

Edge Cases:
- Verification link expires → "Resend verification email" button
- User closes browser mid-form → Save form data, show "Continue" on return
```

**2. Navigation Map**
Show the hierarchy of your screens:

```
Home
├── Sign Up → Onboarding → Dashboard
├── Log In → Dashboard
│   ├── Notes List
│   │   ├── New Note
│   │   └── Note Detail → Edit Note
│   ├── Search
│   └── Settings
│       ├── Profile
│       └── Account
└── Forgot Password → Reset Password → Dashboard
```

**3. Screen Inventory**
For every screen, define:

```markdown
### Screen: Dashboard

- Route: /dashboard
- Access: Authenticated users only
- Purpose: Shows recent notes and search bar
- Key Elements: Search bar, recent notes list, "New Note" button
- Actions: Click note → Note Detail | Click "New Note" → New Note page
- States: Loading (skeleton), Empty (no notes yet), Default
```

**4. Decision Points**
Write out the logic that controls what users see:

```
IF user is NOT logged in:
  THEN redirect to /login

IF user IS logged in AND email NOT verified:
  THEN show "Verify your email" banner

IF user IS logged in AND email IS verified:
  THEN show full dashboard
```

### APP_FLOW Template Prompt for AI

```
Create APP_FLOW.md for [YOUR APP NAME].

App description: [BRIEF DESCRIPTION]

Generate:
1. Entry Points — all ways users can arrive (direct URL, email links, etc.)
2. Core User Flows — cover these flows:
   - User registration/onboarding
   - Main feature usage
   - Account management
   For each flow: happy path (step-by-step), error states, edge cases
3. Navigation Map — hierarchical tree of all screens
4. Screen Inventory — for each screen: route, access level, purpose, key elements, available actions, state variants
5. Decision Points — IF-THEN logic for authentication, permissions, empty states
6. Error Handling — 404, 500, network offline, permission denied
7. Responsive behavior differences (mobile vs desktop)

Requirements: Every action must have a next step. Document both success and failure paths.
Output as Markdown.
```

---

## Document 3: TECH_STACK.md

### What Is It?

The definitive list of every tool, library, and service your app uses — with exact version numbers.

### Why Do You Need It?

AI defaults to "latest" versions, which often have breaking changes or incompatibilities. Locking versions prevents your AI from mixing Next.js 14 components with Next.js 13 patterns, or using a deprecated API.

### The Golden Rule: **Always Specify Exact Versions**

```
❌ Bad:  "Use Next.js latest"
✅ Good: "Use Next.js 14.1.0"

❌ Bad:  "Use React"
✅ Good: "Use React 18.2.0"
```

### Recommended Beginner Stack

If you're not sure what to choose, start here:

**Frontend:**

- **Framework:** Next.js 14.1.0
- **Language:** TypeScript 5.3.3
- **Styling:** Tailwind CSS 3.4.1
- **State:** Zustand 4.4.7
- **Forms:** React Hook Form 7.49.3 + Zod 3.22.4
- **Icons:** Lucide React 0.312.0

**Backend:**

- **Runtime:** Node.js 20.11.0 LTS
- **Framework:** Express.js 4.18.2
- **Database:** PostgreSQL 16.1 with Prisma 5.8.1
- **Caching:** Redis 7.2.4
- **Auth:** JWT (jsonwebtoken 9.0.2) + bcrypt 5.1.1
- **Email:** Resend 3.0.0
- **File Storage:** AWS S3

**DevOps:**

- **Frontend Hosting:** Vercel
- **Backend Hosting:** Railway or Fly.io
- **CI/CD:** GitHub Actions
- **Error Tracking:** Sentry

**Testing:**

- **Unit Tests:** Vitest 1.2.0
- **E2E Tests:** Playwright 1.41.1

### Key Sections to Include

**1. Environment Variables**
List every environment variable your app needs:

```bash
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/myapp"

# Auth
JWT_SECRET="your-32-char-random-string-here"

# Email
RESEND_API_KEY="re_xxxxxxxxxxxx"

# App
NEXT_PUBLIC_API_URL="http://localhost:3001"
NODE_ENV="development"
```

**2. Exact Package Versions (JSON)**

```json
{
  "next": "14.1.0",
  "react": "18.2.0",
  "typescript": "5.3.3",
  "tailwindcss": "3.4.1",
  "zustand": "4.4.7",
  "zod": "3.22.4"
}
```

**3. Why Each Choice Was Made**
Document your reasoning — it helps AI understand constraints:

```markdown
### State Management: Zustand 4.4.7

- Reason: Lightweight, TypeScript-first, minimal boilerplate
- Alternatives rejected: Redux (too verbose for small apps),
  Context API (performance issues with frequent updates)
```

### TECH_STACK Template Prompt for AI

```
Create TECH_STACK.md for [YOUR APP DESCRIPTION].

App details:
- Type: [Web app / Mobile / API]
- Scale: [MVP / Small startup / Enterprise]
- Team Size: [1 developer / small team]
- MVP Date: [Your target date]

For EVERY technology, specify:
- Exact version number (NOT "latest")
- Official documentation URL
- License type
- Reason for choosing it
- Alternatives considered and why rejected

Include sections for:
1. Frontend Stack (framework, language, styling, state, forms, HTTP client, routing, UI components)
2. Backend Stack (runtime, framework, database + ORM, caching, auth, file storage, email)
3. DevOps (version control strategy, CI/CD, hosting for frontend/backend/database, monitoring, testing)
4. Development Tools (linter, formatter, git hooks, IDE recommendations)
5. Environment Variables (ALL required vars with descriptions)
6. Package.json Scripts (dev, build, test, database operations)
7. Exact dependency versions (JSON code blocks for frontend and backend)
8. Security considerations (auth flow, password hashing, rate limits, CORS)
9. Version upgrade policy (when and how to update)

CRITICAL: No "latest" or version ranges. Exact versions only. Output as Markdown.
```

---

## Document 4: FRONTEND_GUIDELINES.md

### What Is It?

Your complete design system — every color, font size, spacing value, and UI component defined exactly. The AI uses this as a reference when building every screen.

### Why Do You Need It?

Without guidelines, AI will make random design decisions. Your buttons will have 3 different styles. Your spacing will be inconsistent. Colors will clash. With guidelines, every component looks like it belongs to the same app.

### Key Sections to Include

**1. Design Tokens (Your App's Visual DNA)**

**Colors:**

```css
/* Primary (your brand color — replace with your chosen color) */
--color-primary-500: #3b82f6; /* Main brand color */
--color-primary-600: #2563eb; /* Hover state */
--color-primary-100: #dbeafe; /* Light background */

/* Semantic colors (never change these meanings) */
--color-success: #10b981; /* Green — confirmations */
--color-warning: #f59e0b; /* Amber — cautions */
--color-error: #ef4444; /* Red — errors */
--color-info: #3b82f6; /* Blue — tips */
```

**Typography:**

```css
/* Font sizes */
--text-sm: 0.875rem; /* 14px — small labels */
--text-base: 1rem; /* 16px — body text */
--text-lg: 1.125rem; /* 18px — large text */
--text-xl: 1.25rem; /* 20px — small headings */
--text-2xl: 1.5rem; /* 24px — section headings */
--text-3xl: 1.875rem; /* 30px — page titles */
```

**2. Component Patterns**

Define your core UI components once, use them everywhere:

```jsx
/* ✅ Primary Button — use for main actions (one per screen) */
<button className="px-4 py-2 bg-primary-500 hover:bg-primary-600
  text-white font-medium rounded-lg transition-colors duration-200
  focus:outline-none focus:ring-2 focus:ring-primary-500
  disabled:opacity-50 disabled:cursor-not-allowed">
  Click Me
</button>

/* ✅ Input Field — always include label + error state */
<div className="space-y-1">
  <label className="block text-sm font-medium text-neutral-700">
    Email
  </label>
  <input className="block w-full px-3 py-2 border border-neutral-300
    rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500"
    placeholder="you@example.com" />
</div>
```

**3. Accessibility Rules (Don't Skip This)**

```
- All text must have 4.5:1 contrast ratio with background
- All interactive elements must work with keyboard (Tab, Enter, Escape)
- Every image needs alt text
- Every form input needs a label (not just a placeholder)
- Buttons need visible focus outlines
```

**4. State Patterns**
Define how loading/empty/error states look across the app:

```jsx
/* Loading Skeleton */
<div className="animate-pulse h-4 bg-neutral-200 rounded w-3/4" />

/* Empty State */
<div className="text-center py-12">
  <Icon className="w-12 h-12 text-neutral-400 mx-auto mb-3" />
  <h3 className="text-lg font-medium">Nothing here yet</h3>
  <button className="mt-4 primary-button">Get Started</button>
</div>

/* Error State */
<div className="bg-red-50 border border-red-200 text-red-700 px-4 py-3 rounded-md">
  Something went wrong. Please try again.
</div>
```

### FRONTEND_GUIDELINES Template Prompt for AI

```
Create FRONTEND_GUIDELINES.md for [YOUR APP].

Style direction: [Modern/Minimal/Bold/Playful/Professional]
Brand colors (if any): [YOUR HEX CODES or "choose appropriate colors"]
Target audience: [DESCRIPTION]

Generate:
1. Design Principles (3-5 core values)
2. Complete Design Tokens:
   - Color palette: primary (50-900 scale), neutral (50-900 scale), semantic colors
   - Typography: font families, sizes (xs to 4xl with rem values), weights, line heights
   - Spacing scale (0 to 16)
   - Border radius values
   - Shadow definitions
3. Layout System: grid, breakpoints, common layout patterns with code
4. Complete Component Library with Tailwind CSS code for:
   - Buttons (primary, secondary, outline, danger) in small/medium/large
   - Input fields (all states: default, focus, error, disabled)
   - Cards, Modals, Alerts
   - Navigation (header, mobile menu)
   - Loading, empty, and error states
5. Accessibility requirements (WCAG AA)
6. Animation guidelines (duration, easing, reduced motion)
7. Icon system (library, sizes, usage)
8. Responsive design rules (mobile-first, touch targets min 44x44px)
9. Browser support list

All CSS classes must be Tailwind-compatible. Include complete code snippets for every component. Output as Markdown.
```

---

## Document 5: BACKEND_STRUCTURE.md

### What Is It?

The complete definition of your database (every table, every column, every relationship) and API (every endpoint, request/response format, validation rules).

### Why Do You Need It?

This document prevents your AI from:

- Creating inconsistent column names across tables
- Missing foreign keys (breaking relationships between data)
- Returning different response formats from similar endpoints
- Forgetting validation rules

### Key Sections to Include

**1. Database Schema**

For every table, use this format:

```markdown
### Table: `users`

**Purpose:** Stores user account information

| Column        | Type         | Constraints      | Description       |
| ------------- | ------------ | ---------------- | ----------------- |
| id            | UUID         | PRIMARY KEY      | Unique identifier |
| email         | VARCHAR(255) | UNIQUE, NOT NULL | Login email       |
| password_hash | VARCHAR(255) | NOT NULL         | Bcrypt hash       |
| full_name     | VARCHAR(255) | NOT NULL         | Display name      |
| created_at    | TIMESTAMP    | DEFAULT NOW()    | Account created   |
| updated_at    | TIMESTAMP    | DEFAULT NOW()    | Last modified     |

**Indexes:**

- `idx_users_email` ON (email)

**Relationships:**

- One user has many posts
- One user has many sessions
```

> **Rule:** Every table needs `id`, `created_at`, and `updated_at`. No exceptions.

**2. API Endpoints**

For every endpoint, document the full contract:

```markdown
### POST /api/auth/register

**Purpose:** Create a new user account
**Authentication:** Not required

**Request Body:**
{
"email": "user@example.com",
"password": "SecurePass123!",
"full_name": "Jane Doe"
}

**Validation:**

- email: valid format, unique in DB, max 255 chars
- password: min 8 chars, 1 uppercase, 1 number, 1 symbol
- full_name: 2-255 characters

**Success Response (201):**
{
"message": "Account created. Please verify your email.",
"user": { "id": "uuid", "email": "...", "full_name": "..." }
}

**Error Responses:**

- 400: Validation failed (returns field-level errors)
- 409: Email already exists

**Side Effects:**

- Creates user record in database
- Sends verification email via Resend
```

**3. Authentication Flow**

```markdown
### JWT Strategy

- Access Token: 15 minute expiry, stored in HTTP-only cookie
- Refresh Token: 7 day expiry, stored in HTTP-only cookie
- Password: bcrypt with 12 rounds (never stored plain text)
- On logout: Invalidate refresh token in database

### Access Token Payload:

{
"sub": "user_id",
"email": "user@example.com",
"role": "user",
"exp": [timestamp]
}
```

**4. Error Response Format (Be Consistent)**

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [{ "field": "email", "message": "Email already exists" }]
  }
}
```

Define your error codes:

```
VALIDATION_ERROR → 400
UNAUTHORIZED     → 401
FORBIDDEN        → 403
NOT_FOUND        → 404
CONFLICT         → 409
RATE_LIMITED     → 429
SERVER_ERROR     → 500
```

### BACKEND_STRUCTURE Template Prompt for AI

```
Create BACKEND_STRUCTURE.md for [YOUR APP].

Main features: [LIST YOUR KEY FEATURES]
Authentication: JWT-based with HTTP-only cookies

Generate:
1. Architecture Overview (REST API, auth strategy, data flow, caching)
2. Complete Database Schema — for EACH table:
   - Full column table (name, type, constraints, description)
   - Indexes (primary key, foreign keys, query-optimized columns)
   - Relationships to other tables
   Include: users, sessions, [your feature tables], [junction tables]
   Rule: Every table must have id (UUID), created_at, updated_at
3. Complete API Endpoints — for EACH endpoint:
   - HTTP method + path
   - Authentication required?
   - Request body (example JSON)
   - Validation rules per field
   - Success response (status code + example JSON)
   - All error responses (code + when it occurs)
   - Side effects (DB changes, emails, cache invalidation)
4. Authentication & Authorization (JWT structure, route protection levels)
5. Data Validation Rules (email regex, password requirements, sanitization)
6. Standardized Error Response Format with error code mapping
7. Caching Strategy (what gets cached, TTL values, cache keys, invalidation)
8. Rate Limiting (by endpoint type: login, register, general API)
9. Database Migration Strategy (tool, process, rollback plan)
10. Backup & Recovery (frequency, retention, restore procedure)
11. API Versioning Strategy

Use snake_case for DB, camelCase for API responses. Output as Markdown.
```

---

## Document 6: IMPLEMENTATION_PLAN.md

### What Is It?

A step-by-step build sequence — the exact order to build your app, broken into small, testable chunks.

### Why Do You Need It?

Without a plan, you'll try to build everything at once, get stuck, and lose track of what's done. The implementation plan keeps you (and the AI) on track with clear milestones.

### The Phase Structure

```
Phase 1: Project Setup & Foundation (Day 1)
Phase 2: Design System (Day 1-2)
Phase 3: Authentication (Day 2-3)
Phase 4: Core Features (Day 3-7)
Phase 5: Testing (Day 7-8)
Phase 6: Deployment (Day 8-10)
```

### How to Write Each Step

Every step should have this structure:

```markdown
### Step 1.1: Initialize Project Structure

**Duration:** ~1 hour
**Goal:** Working project with all config files

**Tasks:**

1. Create GitHub repository
2. Run: `npx create-next-app@14.1.0 my-app --typescript --tailwind --app`
3. Install dependencies from TECH_STACK.md
4. Set up ESLint + Prettier config
5. Configure Husky pre-commit hooks

**Success Criteria:**

- [ ] `pnpm dev` runs without errors
- [ ] No linting errors on `pnpm lint`
- [ ] Git hooks trigger on commit

**Reference Docs:** TECH_STACK.md sections 2, 5
```

### Full Phase Breakdown

**Phase 1: Foundation**

- Step 1.1: Initialize project + install dependencies
- Step 1.2: Configure environment variables
- Step 1.3: Set up and migrate database

**Phase 2: Design System**

- Step 2.1: Configure Tailwind with design tokens from FRONTEND_GUIDELINES.md
- Step 2.2: Build reusable components (Button, Input, Card, Modal)
- Step 2.3: Build layout components (Header, Sidebar, Footer)

**Phase 3: Authentication**

- Step 3.1: Backend — register + login endpoints
- Step 3.2: Backend — JWT middleware + protected routes
- Step 3.3: Frontend — registration page
- Step 3.4: Frontend — login page + session management

**Phase 4: Core Features**
_(One step per P0 feature from your PRD.md)_

- Step 4.1: [Feature 1] — backend API + database
- Step 4.2: [Feature 1] — frontend UI
- Step 4.3: [Feature 2] — backend API + database
- Step 4.4: [Feature 2] — frontend UI

**Phase 5: Testing**

- Step 5.1: Unit tests for business logic
- Step 5.2: Integration/E2E tests for core flows

**Phase 6: Deployment**

- Step 6.1: Deploy to staging, run smoke tests
- Step 6.2: Deploy to production, monitor errors

### IMPLEMENTATION_PLAN Template Prompt for AI

```
Create IMPLEMENTATION_PLAN.md for [YOUR APP].

Tech Stack: [From TECH_STACK.md]
MVP Features: [List P0 features from PRD.md]
Timeline: [Number of days/weeks]

Generate 6 phases with numbered steps. For EACH step include:
- Duration estimate
- Clear goal statement
- Numbered tasks with exact bash commands where applicable
- Code snippets for configuration
- Testable success criteria (checkbox list)
- Reference to relevant documentation sections

Phases:
1. Project Setup & Foundation (init, environment, database)
2. Design System (Tailwind tokens, core components)
3. Authentication (backend endpoints, frontend pages, JWT)
4. Core Features (one step per P0 feature — backend then frontend)
5. Testing (unit tests, E2E tests with coverage targets)
6. Deployment (staging then production)

Also include:
- Milestones table (target dates + deliverables checklist)
- Risk table (Technical Risks + Timeline Risks with mitigations)
- Overall MVP success criteria
- Post-MVP roadmap (P1 features)

Each step must output something testable. Reference PRD, APP_FLOW, TECH_STACK, FRONTEND_GUIDELINES, and BACKEND_STRUCTURE throughout.
Output as Markdown.
```

---

## How to Use These Docs with AI

### The Setup (Do This Once)

1. Create a `/docs` folder in your project root
2. Put all 6 documents in it
3. Commit them to your repository
4. Reference them every time you prompt the AI

### The Right Way to Prompt AI

**At the start of every coding session:**

```
I'm building [APP NAME]. My documentation is in /docs.

Before writing any code, please read:
- docs/PRD.md — for feature requirements
- docs/TECH_STACK.md — for technology decisions
- docs/APP_FLOW.md — for user flows
- docs/FRONTEND_GUIDELINES.md — for design patterns
- docs/BACKEND_STRUCTURE.md — for data models and APIs

Today I want to implement: [SPECIFIC STEP FROM IMPLEMENTATION_PLAN.md]

Do not add features not in PRD.md. Do not use technologies not in TECH_STACK.md.
Ask me if anything is ambiguous before writing code.
```

**When building a specific feature:**

```
Referring to docs/PRD.md (Feature: Post Creation) and
docs/BACKEND_STRUCTURE.md (POST /api/posts endpoint),
implement the post creation API following IMPLEMENTATION_PLAN.md Step 4.1.

Use the database schema exactly as defined. Return errors in the
standardized format from BACKEND_STRUCTURE.md section 7.
```

**When building a UI:**

```
Build the Post Creation page following:
- docs/APP_FLOW.md (Post Creation flow, including error states)
- docs/FRONTEND_GUIDELINES.md (use Button and Input components as defined)
- docs/PRD.md (Post Creation acceptance criteria)

The form must handle: validation errors, loading state, and success redirect.
Follow the responsive patterns in FRONTEND_GUIDELINES.md section 9.
```

---

## Quick Start Checklist

Use this checklist when starting a new project:

### Before Writing Any Code

```
[ ] Brainstorm your app idea (write a 1-paragraph description)
[ ] Write PRD.md (use the AI prompt from Document 1 section)
[ ] Write APP_FLOW.md (use the AI prompt from Document 2 section)
[ ] Write TECH_STACK.md (use the AI prompt from Document 3 section)
[ ] Write FRONTEND_GUIDELINES.md (use the AI prompt from Document 4 section)
[ ] Write BACKEND_STRUCTURE.md (use the AI prompt from Document 5 section)
[ ] Write IMPLEMENTATION_PLAN.md (use the AI prompt from Document 6 section)
[ ] Review all docs for consistency (same feature names everywhere?)
[ ] Create /docs folder and commit all documents to Git
```

### During Development (Per Step)

```
[ ] Read the relevant docs before prompting AI
[ ] Reference specific section numbers in your prompt
[ ] Check AI output against success criteria before moving on
[ ] Test the step before starting the next one
[ ] Commit working code after each completed step
```

### Before Launch

```
[ ] All P0 features from PRD.md implemented and tested
[ ] All flows from APP_FLOW.md working (including error states)
[ ] UI matches FRONTEND_GUIDELINES.md
[ ] API matches BACKEND_STRUCTURE.md exactly
[ ] Tests passing (80%+ coverage target)
[ ] Deployed to staging and tested
[ ] No critical errors in logs
```

---

## Common Beginner Mistakes

### Mistake 1: Writing Vague Requirements

```
❌ "The app should be fast"
✅ "Page load time < 2 seconds on 4G mobile connection"

❌ "Users can manage their content"
✅ "Users can create, edit, and delete posts. Drafts auto-save every 30 seconds."
```

### Mistake 2: Skipping the "Out of Scope" Section

If you don't tell AI what NOT to build, it will add features. An "out of scope" list prevents unnecessary complexity.

### Mistake 3: Using "Latest" Package Versions

Always pin exact versions. `"next": "14.1.0"` not `"next": "latest"`. This one habit will save you hours of debugging version conflicts.

### Mistake 4: Building Without Testing Each Step

Don't build 5 steps and then test. Build Step 1 → test → build Step 2 → test. Problems caught early are easy to fix. Problems caught late cascade.

### Mistake 5: Ignoring Error States

Most beginners document only the happy path. Document what happens when:

- The API call fails
- The user enters invalid data
- The network is offline
- The session expires

### Mistake 6: Inconsistent Naming

If your PRD calls it "posts" but your BACKEND_STRUCTURE calls it "articles" and your APP_FLOW calls it "content" — the AI will get confused. Pick one name for each concept and use it everywhere.

### Mistake 7: Not Referencing Docs in AI Prompts

Writing the docs isn't enough — you need to tell the AI to read them. Reference specific documents and sections in every prompt.

---

## Copy-Paste AI Prompts

### Generate All 6 Documents in Sequence

Use these prompts in order. Each one references the previous documents for consistency.

**Step 1: Generate PRD.md**

```
Create PRD.md for [YOUR APP IDEA].
Target users: [WHO]
Problem: [WHAT PAIN POINT]
Include: problem statement, 2 personas, SMART success metrics, P0/P1/P2 features with user stories and acceptance criteria, out of scope section (5+ items), 3 user scenarios, non-functional requirements.
Output as Markdown.
```

**Step 2: Generate APP_FLOW.md**

```
Based on the PRD.md I'll paste below, create APP_FLOW.md.
Include: entry points, user flows for every P0 feature (happy path + errors + edge cases), navigation map, screen inventory, decision point logic, error handling (404/500/offline), responsive differences.
[PASTE YOUR PRD.md HERE]
```

**Step 3: Generate TECH_STACK.md**

```
Create TECH_STACK.md for a [web app / type] built for [YOUR APP DESCRIPTION].
Team size: 1 developer. MVP scale.
Recommend a complete beginner-friendly stack with exact version numbers (no "latest").
Include: frontend stack, backend stack, DevOps, testing, all environment variables, package.json scripts, security considerations.
```

**Step 4: Generate FRONTEND_GUIDELINES.md**

```
Create FRONTEND_GUIDELINES.md for [YOUR APP].
Style: [modern/minimal/etc]. Using Tailwind CSS from TECH_STACK.md.
Include: design tokens (colors, typography, spacing, radius, shadows), layout system, component library with complete Tailwind code (buttons, inputs, cards, modals, alerts, loading/empty/error states), accessibility requirements, animation rules.
```

**Step 5: Generate BACKEND_STRUCTURE.md**

```
Create BACKEND_STRUCTURE.md for [YOUR APP].
Features from PRD.md: [LIST FEATURES].
Stack from TECH_STACK.md: PostgreSQL + Prisma + Express + JWT.
Include: database schema for all tables (column tables with types/constraints), all API endpoints (with request/response JSON), auth flow, validation rules, error format, caching strategy, rate limits.
```

**Step 6: Generate IMPLEMENTATION_PLAN.md**

```
Create IMPLEMENTATION_PLAN.md for [YOUR APP].
Stack: from TECH_STACK.md
P0 Features: [LIST FROM PRD.md]
Timeline: [X weeks]
Create 6 phases with numbered steps. Each step: duration, goal, tasks with commands, testable success criteria, doc references.
Also: milestone table, risk table, overall success criteria, post-MVP roadmap.
```

---

## Quick Reference Card

Save this summary to your desktop:

```
📁 /docs
├── PRD.md              → WHAT to build (features, users, success)
├── APP_FLOW.md         → HOW users navigate (flows, screens, errors)
├── TECH_STACK.md       → WHICH tools to use (exact versions!)
├── FRONTEND_GUIDELINES.md → HOW it looks (colors, components, patterns)
├── BACKEND_STRUCTURE.md   → HOW data works (schema, APIs, auth)
└── IMPLEMENTATION_PLAN.md → WHAT ORDER to build (phases, steps, tests)

GOLDEN RULES:
✅ Write docs BEFORE code
✅ Use exact version numbers
✅ Document error states, not just happy paths
✅ Define "out of scope" explicitly
✅ Reference docs in every AI prompt
✅ Test after every step
✅ One name per concept (be consistent)

PROMPT PATTERN:
"Referring to [DOCS], implement [SPECIFIC STEP].
Do not deviate from the specs. Ask if ambiguous."
```

---

_Built with the documentation-first approach. Your project stays on track because AI has no room to guess._

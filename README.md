<p align="center">
  <h1 align="center">Claude Startup Validator</h1>
  <p align="center">
    Validate and generate AI startup ideas grounded in real industry workflows — not random brainstorm lists.
    <br />
    <strong>A Claude Code Plugin | Claude.ai Project | Claude Cowork Skill</strong>
    <br />
    <br />
    <a href="#quick-start">Quick Start</a>
    &middot;
    <a href="#installation">Installation</a>
    &middot;
    <a href="#all-commands">All Commands</a>
    &middot;
    <a href="#how-it-works">How It Works</a>
    &middot;
    <a href="#customization">Customization</a>
  </p>
</p>

---

## What Is This?

A skill (prompt framework) for Claude that transforms how AI generates startup ideas. Instead of shallow "build an AI chatbot for X" suggestions, this skill produces **founder-grade business intelligence** — the kind of analysis you'd pay a strategy consultant $10,000 to produce.

Every idea generated is:

- Grounded in a **real manual workflow** someone does today
- Mapped against the **full competitor landscape** — who exists, who failed, and why there's still room
- Stress-tested against **10 known startup failure patterns** with specific mitigation strategies
- Scored on a **6-dimension weighted rubric** with composite scores
- Packaged with a **concrete MVP plan** including architecture, timeline, pricing, and launch strategy

## Why This Exists

Most AI idea generators produce lists like:
> "AI-powered CRM", "Smart document processor", "AI assistant for businesses"

These are useless for founders making real investment decisions. They lack:
- Who specifically has this problem?
- What are they doing manually today?
- Who else tried this and failed?
- Can current AI actually do this well?
- What does the MVP look like technically?
- How do I reach my first 10 customers?

**This skill answers all of those questions for every single idea it generates.**

## What Makes This Different

| Feature | Generic AI Ideas | This Skill |
|---------|-----------------|------------|
| Workflow grounding | "AI for healthcare" | "Prior auth coordinators spend 15+ hrs/week copying between EHR and payer portals" |
| Competitor analysis | None | Direct, indirect, adjacent, and DIY alternatives mapped |
| Failure risk | None | 10 failure modes checked, failed predecessors analyzed |
| Scoring | "High potential" | 7.4/10 composite from 6 weighted dimensions |
| MVP plan | "Build an app" | "Laravel + queue workers, email integration, 4-week timeline, $500 budget" |
| Buyer persona | "Businesses" | "Operations Manager at 3PL companies, 50-500 employees" |
| Pricing | None | "$149-299/mo per seat based on $60k/yr manual cost replacement" |

---

## Quick Start

### 30-Second Version

1. Install the skill (see [Installation](#installation) below)
2. Open Claude Code (or Claude.ai Project)
3. Type: `Give me 5 AI startup ideas for industries with manual document processing`
4. Get 5 scored, ranked opportunities with competitor maps, failure analysis, and MVP plans

### Your First Prompt

```
Give me AI startup ideas for industries that still rely heavily on manual data entry
```

**What you'll get back:**

- A ranked table of 5+ ideas with composite scores
- Each idea with all 28 analysis fields
- Competitor landscape per idea
- Failure risk assessment with survival confidence
- Summary: Best Overall, Fastest to Build, Highest Revenue, Best for Solo Founder

---

## Installation

### Prerequisites

- **Claude Code** (CLI) — [Install guide](https://docs.anthropic.com/en/docs/claude-code)
- OR **Claude.ai** account (Pro/Team/Enterprise)
- OR **Claude Cowork** workspace

### Method 1: `/plugin` Install (Recommended)

The easiest way — two commands in Claude Code:

```bash
# Step 1: Add the marketplace
/plugin marketplace add nmsavaliya/claude-startup-validator

# Step 2: Install the plugin
/plugin install claude-startup-validator
```

Or use the interactive UI:

```
1. Type /plugin in Claude Code
2. Go to "Marketplaces" tab → Add → nmsavaliya/claude-startup-validator
3. Go to "Discover" tab → Find "claude-startup-validator" → Install
4. Restart Claude Code
```

**Done!** The skill is now available globally.

### Method 2: Clone + Settings (Manual Plugin Install)

If you prefer manual installation:

```bash
# Step 1: Clone the repo anywhere you like
git clone https://github.com/nmsavaliya/claude-startup-validator.git ~/claude-plugins/claude-startup-validator
```

```bash
# Step 2: Add the plugin path to your Claude Code settings
# Open (or create) ~/.claude/settings.json and add:
```

```json
{
  "permissions": {},
  "plugins": [
    "~/claude-plugins/claude-startup-validator/plugins/claude-startup-validator"
  ]
}
```

```bash
# Step 3: Restart Claude Code — the skill is now available globally
```

### Method 3: Per-Project Plugin

Add it to a specific project so it only loads in that workspace:

```bash
# Step 1: In your project root, clone the repo
git clone https://github.com/nmsavaliya/claude-startup-validator.git .claude/plugins/claude-startup-validator
```

Create `.claude/settings.local.json` in your project root:

```json
{
  "plugins": [
    ".claude/plugins/claude-startup-validator/plugins/claude-startup-validator"
  ]
}
```

### Method 4: Manual Download (Standalone Skill)

If you prefer not to use git or the plugin system:

```bash
# Step 1: Create the directory structure
mkdir -p ~/.claude/skills/ai-startup-opportunity-generator/references
mkdir -p ~/.claude/skills/ai-startup-opportunity-generator/assets
```

```bash
# Step 2: Download each file
BASE_URL="https://raw.githubusercontent.com/nmsavaliya/claude-startup-validator/main/plugins/claude-startup-validator/skills/ai-startup-opportunity-generator"

# Core file
curl -o ~/.claude/skills/ai-startup-opportunity-generator/SKILL.md "$BASE_URL/SKILL.md"

# Reference files
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/scoring-rubric.md "$BASE_URL/references/scoring-rubric.md"
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/output-schema.md "$BASE_URL/references/output-schema.md"
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/productization-templates.md "$BASE_URL/references/productization-templates.md"
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/industry-playbook.md "$BASE_URL/references/industry-playbook.md"
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/competitor-analysis-framework.md "$BASE_URL/references/competitor-analysis-framework.md"
curl -o ~/.claude/skills/ai-startup-opportunity-generator/references/failure-patterns.md "$BASE_URL/references/failure-patterns.md"

# Example output
curl -o ~/.claude/skills/ai-startup-opportunity-generator/assets/example-output.md "$BASE_URL/assets/example-output.md"
```

```bash
# Step 3: Verify all files are present
ls -la ~/.claude/skills/ai-startup-opportunity-generator/
ls -la ~/.claude/skills/ai-startup-opportunity-generator/references/
# You should see: SKILL.md, and 6 files in references/
```

### Method 5: Claude.ai (Projects)

For users who prefer the Claude.ai web interface:

```
Step 1: Go to claude.ai and click "Projects" in the left sidebar
Step 2: Click "+ Create Project"
Step 3: Name it "AI Startup Opportunity Generator"
```

```
Step 4: Click "Set custom instructions"
Step 5: Open the SKILL.md file from: plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/SKILL.md
Step 6: Copy the ENTIRE content (everything after the --- frontmatter closing ---)
Step 7: Paste it into the custom instructions box
Step 8: Click "Save"
```

```
Step 9: Click "Add content" → "Upload files"
Step 10: Upload ALL 6 files from plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/:
   - scoring-rubric.md
   - output-schema.md
   - productization-templates.md
   - industry-playbook.md
   - competitor-analysis-framework.md
   - failure-patterns.md
```

```
Step 11: Optionally upload plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/assets/example-output.md as an additional reference
Step 12: Start a new conversation within the project
Step 13: Ask: "Give me 5 AI startup ideas in healthcare"
```

**Important Notes for Claude.ai:**
- The skill works best with Claude Opus or Sonnet models
- Reference files uploaded as project knowledge are automatically available
- You don't need to tell Claude to "use the skill" — the project instructions handle that

### Method 6: Claude Cowork

```
Step 1: Clone the repository into your Cowork workspace:
        git clone https://github.com/nmsavaliya/claude-startup-validator.git

Step 2: Add the plugins/claude-startup-validator/ folder to your
        Cowork workspace's plugins directory

Step 3: Ensure your workspace can access:
        - plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/SKILL.md (core logic)
        - plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/ (all 6 files)
        - plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/assets/ (example output)

Step 4: The skill auto-triggers when you discuss:
        - AI startup ideas
        - Business opportunities
        - Workflow automation
        - Competitor analysis for AI products
        - Startup failure analysis
```

### Verifying Installation

After installing via any method, verify it works:

```
# In Claude Code or Claude.ai, type:
Give me one AI startup idea in the logistics industry — deep analysis mode
```

**Expected output:** A single, deeply analyzed opportunity with all 28 fields including competitor map, failure risk analysis, scoring breakdown, and MVP plan. If you see a generic brainstorm list instead, the skill isn't loading correctly — check the file paths.

---

## All Commands

### Input Mode Commands

These determine what KIND of ideas you get:

#### Broad Discovery
```
Give me 10 AI startup ideas
Find opportunities in manual industries
List industries where AI can automate work
What AI products should I build?
Show me the best AI business opportunities right now
```

#### Industry-Specific
```
Generate ideas for logistics
Find AI opportunities in legal ops
What can I build for real estate brokers?
AI startup ideas in healthcare administration
Show me construction industry AI opportunities
AI for accounting and finance
Opportunities in HR and recruiting
AI products for insurance companies
Agricultural AI startup ideas
Education technology AI opportunities
```

#### Workflow-Specific
```
How can AI improve invoice processing?
Generate ideas around call center QA
Automate lead qualification
AI for document review and extraction
Improve employee onboarding with AI
Automate compliance tracking
AI for customer support ticket triage
Streamline contract review with AI
```

#### Persona-Specific
```
Ideas for accountants
Tools for customer support managers
AI products for Shopify merchants
What can I build for project managers?
AI tools for real estate agents
Products for HR directors
Tools for insurance claims adjusters
AI for freelancers and agencies
```

#### Constraint-Based
```
Give me ideas I can build in 30 days
Ideas for solo developers
Opportunities with local models only
B2B ideas under $5k MVP cost
Ideas I can build with Laravel in 4 weeks
AI micro-SaaS for bootstrapped founders
Ideas that don't require enterprise sales
Products I can build and launch this month
Give me ideas using only open-source models
```

### Behavior Mode Commands

These determine HOW deep the analysis goes:

#### Ideation Mode (Default)
```
Give me 5 AI startup ideas for [industry]
# Returns: Ranked table with scores + brief competitor snapshots
```

#### Deep Analysis Mode
```
Deep dive on AI for construction RFI management
Do a deep analysis of [idea name]
Analyze AI opportunities in [industry] — full analysis
Give me 2 ideas for [industry] with complete business plans
```

#### Ranking Mode
```
Compare invoice processing vs lead scoring vs contract review
Rank these ideas by opportunity score: [list ideas]
Which is better to build: [idea A] or [idea B]?
```

#### MVP Mode
```
Turn AI invoice processing into an MVP plan
Give me the technical architecture for [idea name]
Break down [idea] into weekly milestones
How would I build [idea] as a Laravel developer?
```

#### Validation Mode
```
Validate this idea: AI-powered RFI tracker for construction
Stress-test [idea name] — what could go wrong?
What assumptions does [idea] depend on?
Is [idea] actually viable? Run the pre-mortem checklist
```

#### Competitor Audit Mode
```
Who are the competitors for AI invoice processing?
Map the competitive landscape for [idea/space]
Is the [industry] AI market too crowded?
Show me who's already doing [idea] and where the gaps are
```

#### Failure Post-Mortem Mode
```
Why do AI startups fail in healthcare?
What failed before in legal tech AI?
Show me startup failures in [industry] and what I can learn
What are the risks of building [idea]?
```

### Output Format Commands

#### Short Mode (Default for 5+ Ideas)
```
Give me 10 ideas — table format
Quick overview of AI opportunities in [industry]
# Returns: Markdown table with scores and survival ratings
```

#### Detailed Mode (Default for 1-3 Ideas)
```
Deep analysis of [idea]
Give me 2 ideas with full details
# Returns: Full 28-field cards per idea
```

#### JSON Mode
```
Give me 5 AI startup ideas — output as JSON
Export ideas for [industry] in JSON format
Generate opportunities as JSON
# Returns: Structured JSON matching the output schema
```

### Combination Commands

You can combine modes for powerful queries:

```
# Industry + Constraint + Ranking
Rank AI opportunities in logistics that I can build solo in 6 weeks

# Persona + Deep Analysis
Deep analysis: What AI tools should I build for insurance claims adjusters?

# Workflow + Validation + Competitor
Validate AI-powered invoice processing — include competitor map and failure risks

# Broad + Constraint + JSON
Give me 10 AI micro-SaaS ideas under $1k MVP cost — export as JSON

# Industry + Failure Post-Mortem
What AI products failed in healthcare, and what opportunities remain?

# Persona + MVP
I'm a Laravel developer — turn the best idea for accountants into an MVP plan
```

---

## How It Works

### The 12-Step Analysis Engine

Every opportunity passes through a 12-step analytical procedure. No steps are skipped.

```
Step 1:  Identify the Domain
         └─ Industry, sub-sector, company size

Step 2:  Map Real Work
         └─ What humans do today, tools used, bottlenecks

Step 3:  Find Candidate Tasks
         └─ Repetitive, cognitive-but-structured, pattern-heavy tasks

Step 4:  Score Pain Level
         └─ Frequency, urgency, error cost, labor cost, compliance risk

Step 5:  Match AI Capabilities
         └─ LLM reasoning, extraction, classification, RAG, voice, vision

Step 6:  Design Product Angle
         └─ Dashboard, inbox assistant, API, agent, browser extension

Step 7:  Define MVP Scope
         └─ One persona, one workflow, one pain, one outcome

Step 8:  Commercial Framing
         └─ Who pays, why they pay, pricing model, ROI math

Step 9:  Personalization Check
         └─ Adapt to founder's tech stack and background

Step 10: Apply Productization Template
         └─ Match to Template A-E for architectural patterns

Step 11: Competitor & Market Landscape
         └─ Direct, indirect, adjacent, DIY alternatives mapped

Step 12: Failure Risk Analysis
         └─ 10 failure modes checked, predecessors analyzed, survival rated
```

### The 6-Dimension Scoring Rubric

Every opportunity is scored on these dimensions:

| Dimension | Weight | Scale | What It Measures |
|-----------|--------|-------|-----------------|
| **Pain Severity** | 25% | 1-10 | How urgent and costly the problem is |
| **Budget Availability** | 20% | 1-10 | Whether the buyer already spends money solving this |
| **Automation Fit** | 20% | 1-10 | How well current AI can actually perform the task |
| **MVP Simplicity** | 15% | 1-10 | How quickly and cheaply a working v1 can be built |
| **Distribution Ease** | 10% | 1-10 | How easily you can reach and convert buyers |
| **Differentiation Potential** | 10% | 1-10 | Whether a defensible moat can develop over time |

**Composite Score** = weighted average

| Score | Rating | What It Means |
|-------|--------|---------------|
| **8.0+** | Exceptional | Pursue immediately. Strong on all fronts. |
| **6.5 - 7.9** | Strong | Worth building. Address weak dimensions in planning. |
| **5.0 - 6.4** | Viable | Could work with the right founder-market fit. |
| **Below 5.0** | Weak | Needs significant pivot or niche refinement. |

### The 28-Field Output Schema

Every opportunity includes these fields:

**Core Analysis (Fields 1-24):**
| # | Field | Example |
|---|-------|---------|
| 1 | Idea Name | AI-Powered Construction RFI Tracker |
| 2 | Industry | Construction / Project Management |
| 3 | Target Buyer | Project Manager at general contractors |
| 4 | End User | Project engineers, site superintendents |
| 5 | Current Manual Workflow | Engineers spend 8-12 hrs/week managing 200-800 RFIs via email + spreadsheets |
| 6 | Core Problem | RFI management consumes skilled staff time and delays projects |
| 7 | Business Impact | Late RFIs cost $5-15k/day in delays; 50 late RFIs = $250-750k |
| 8 | AI Solution | Classify, route, draft responses, track deadlines, flag incomplete RFIs |
| 9 | Key Features | Auto-classification, smart routing, deadline alerts, daily digest, response drafts |
| 10 | Recommended MVP | Email-based RFI tracker for one GC, single integration |
| 11 | Data Required | RFI emails, project directory, contract scope docs |
| 12 | Integrations | Email (IMAP/SMTP) in v1, Procore API in v2 |
| 13 | AI Capability Match | LLM classification, document extraction, email drafting |
| 14 | Business Model | Monthly SaaS per project |
| 15 | Pricing Range | $199-499/month per active project |
| 16 | Complexity | Medium |
| 17 | Time to MVP | 5 weeks |
| 18 | Defensibility | Workflow integration depth + historical RFI data |
| 19 | Risks | Behavior change needed, accuracy requirements |
| 20 | Go-to-Market | Construction PM communities, AGC chapters, free 30-day pilot |
| 21 | Existing Alternatives | Procore RFI module, PlanGrid (Autodesk) |
| 22 | Why This Wins | AI-native vs bolt-on, 60% cheaper, focused on one workflow |
| 23 | Scores | Pain: 8, Budget: 7, Auto: 8, MVP: 7, Dist: 6, Diff: 7 = **7.35** |
| 24 | Final Verdict | Strong opportunity targeting well-defined pain in validated market |

**Market Intelligence (Fields 25-28):**
| # | Field | What It Contains |
|---|-------|-----------------|
| 25 | Competitor Map | Direct, indirect, adjacent, and DIY alternatives with strengths/weaknesses |
| 26 | Failed Predecessors | Startups that tried this space and failed — names, reasons, lessons |
| 27 | Failure Lessons | What this idea does differently to avoid past mistakes |
| 28 | Market Timing Signal | Why NOW — AI maturity, cost drops, regulatory shifts, buyer readiness |

### Competitor Analysis Framework

Every opportunity includes a structured competitive landscape:

```
Direct Competitors     → Same problem, same AI approach
Indirect Competitors   → Same problem, different approach (manual, legacy software)
Adjacent Players       → Different problem, could expand here
DIY Alternatives       → Spreadsheets, ChatGPT copy-paste, hiring VAs

Market Saturation Assessment:
  0-2 funded competitors  → Underserved (opportunity or no market)
  3-5 funded competitors  → Validated (best position for new entrants)
  6-10 funded competitors → Getting crowded (need clear wedge)
  10+ funded competitors  → Crowded (avoid unless unique angle)
```

### Failure Pattern Library

Every opportunity is checked against 10 known failure modes:

| # | Failure Mode | What Kills Startups |
|---|-------------|-------------------|
| 1 | Solution Looking for a Problem | No real workflow pain behind the idea |
| 2 | Accuracy Dependency Trap | Product needs 99%+ accuracy but AI delivers 85% |
| 3 | Enterprise Sales Cycle Death | Bootstrapped startup dies waiting for 12-month sales cycles |
| 4 | Integration Complexity Hell | MVP needs 5+ system integrations before delivering value |
| 5 | Data Moat Delusion | Plan depends on accumulating proprietary data that never comes |
| 6 | Horizontal Trap | "AI for everyone" competes with ChatGPT, Copilot, and everyone else |
| 7 | Pricing Misalignment | API costs $200/mo but buyer won't pay more than $49/mo |
| 8 | Market Timing Failure | Too early (AI isn't ready) or too late (market is saturated) |
| 9 | Regulatory Blindside | HIPAA/SOC2/GDPR compliance costs more than the product development |
| 10 | Team-Market Mismatch | Founders don't understand the industry they're building for |

Each idea gets a **Survival Confidence** rating: High / Medium / Low

### Industry Playbook

Pre-analyzed market intelligence for 10 industries:

| Industry | Top Pain Points | Competition Density |
|----------|----------------|-------------------|
| Logistics & Supply Chain | Fragmented systems, manual data entry, customs errors | Moderate |
| Legal / Compliance | Contract review backlogs, compliance tracking, billing | Growing |
| Healthcare Administration | Prior auth, claims denial, medical coding errors | Moderate-Crowded |
| Real Estate | Listing copy, CMA analysis, lease abstraction | Low-Moderate |
| Construction | Estimation errors, RFI bottlenecks, safety compliance | Low |
| Accounting & Finance | Month-end close, reconciliation, audit prep | Moderate |
| HR & Recruiting | Resume screening, interview scheduling, performance reviews | Crowded (ATS), Gaps exist |
| Insurance | Claims processing, underwriting, fraud detection | Moderate |
| Agriculture | Crop scouting, pest ID, compliance docs, maintenance | Low |
| Education & Training | Grading, IEP writing, accreditation prep, curriculum alignment | Low |

### Productization Templates

5 architectural patterns for common AI product types:

| Template | Pattern | Best For |
|----------|---------|----------|
| **A: Knowledge Work** | AI ingests → extracts → drafts → human reviews | Data entry, report generation, email drafting |
| **B: Review & QA** | AI samples → scores → flags → summarizes | Call center QA, compliance, content moderation |
| **C: Routing & Triage** | AI classifies → prioritizes → routes → drafts action | Support tickets, lead routing, claims intake |
| **D: Sales Intelligence** | AI enriches → scores → prioritizes → drafts outreach | Lead qualification, CRM enrichment, prospect research |
| **E: Document Ops** | AI OCRs → extracts → validates → flags exceptions | Invoice processing, contract review, permit applications |

Each template includes Laravel-specific architecture suggestions.

---

## Example Output

Here's a condensed example of what the skill produces for a single idea in detailed mode:

```markdown
## AI-Powered Construction RFI Tracker

Industry: Construction / Project Management
Target Buyer: Project Manager at general contractors (50-500 employees)
End User: Project engineers, site superintendents

### The Problem
On a typical commercial construction project, 200-800 RFIs are generated.
Project engineers spend 8-12 hours per week managing them.
Late RFI responses delay schedules by 3-5 days per incident.
On a $10M project, each delay day costs $5,000-15,000.

### The Solution
AI reads incoming RFIs, classifies by trade, routes to responsible party,
flags incomplete submissions, tracks deadlines, and generates daily summaries.

### Competitive Landscape
Direct: Procore RFI module ($500+/mo, not AI-native), PlanGrid (basic RFI log)
Indirect: Email + spreadsheets, dedicated coordinators ($60-80k/yr)
Market Saturation: Validated but not AI-crowded

### Failure Risk
Vulnerable to: Integration Complexity (mitigated: email-only v1)
Failed predecessors: Broad construction AI startups (2018-2020) — too wide scope
Survival Confidence: High

### Scores
Pain: 8 | Budget: 7 | Automation: 8 | MVP: 7 | Distribution: 6 | Differentiation: 7
Composite: 7.35/10 — Strong
```

See [example-output.md](plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/assets/example-output.md) for a complete 28-field example.

---

## Customization

### Changing the Developer Profile

The skill defaults to biasing toward **Laravel/full-stack developer** ideas. To change this:

1. Open `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/SKILL.md`
2. Find **Step 9: Personalization Check** (around line 170)
3. Replace the tech stack list with your preferred stack:

```markdown
# For Python/Django developers:
Django backend, Celery workers, PostgreSQL, Redis,
FastAPI microservices, Hugging Face models, Streamlit dashboards

# For Node.js/Next.js developers:
Next.js frontend, Express/Fastify backend, Bull queues,
Prisma ORM, Vercel deployment, Supabase, tRPC

# For Ruby on Rails developers:
Rails backend, Sidekiq workers, Hotwire/Turbo,
Action Cable, Active Storage, Heroku deployment
```

### Adding New Industries

1. Open `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/industry-playbook.md`
2. Add a new section following this format:

```markdown
## [Industry Number]. [Industry Name]

**Top Manual Workflows**: [List 4-6 specific workflows people do manually]

**Pain Points**: [List 3-5 quantified pain points with dollar/time costs]

**Competition Density**: [Low / Moderate / Crowded + explanation]

**Buyer Personas**: [2-3 specific job titles with company size]
```

### Adjusting Scoring Weights

1. Open `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/scoring-rubric.md`
2. Modify the weights in the "Dimension Weights" table
3. Update the composite formula to match
4. Example: If you value speed over everything:

```markdown
| MVP Simplicity | 30% |        ← increased
| Pain Severity  | 25% |
| Automation Fit | 20% |
| Distribution   | 15% |        ← increased
| Budget         | 5%  |        ← decreased
| Differentiation| 5%  |        ← decreased
```

### Adding Failure Patterns

1. Open `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/failure-patterns.md`
2. Add a new numbered section:

```markdown
### 11. [Failure Mode Name]
**What it looks like**: [One sentence description]
**Warning signs**: [Specific red flags to watch for]
**Real pattern**: [Anonymized real-world example]
**How to de-risk**: [Specific mitigation strategies]
```

3. Update the pre-mortem checklist if the new pattern adds a new question

### Adding Productization Templates

1. Open `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/references/productization-templates.md`
2. Add a new template section (F, G, etc.) following the existing format
3. Include: Pattern description, architecture, Laravel stack, pricing model, timeline, key risk

---

## File Structure

```
claude-startup-validator/
│
├── .claude-plugin/
│   └── marketplace.json                        # Marketplace catalog (for /plugin install)
│
├── plugins/
│   └── claude-startup-validator/               # The plugin
│       ├── .claude-plugin/
│       │   └── plugin.json                     # Plugin manifest (auto-discovery)
│       └── skills/
│           └── ai-startup-opportunity-generator/
│               ├── SKILL.md                    # Core skill logic (277 lines)
│               │   ├── YAML frontmatter        #   name + description (triggering)
│               │   ├── Role definition         #   Expert AI startup strategist
│               │   ├── Input/Behavior modes    #   5 input + 7 behavior modes
│               │   ├── 12-step thinking engine #   The analytical engine
│               │   ├── Scoring + output format #   6 dimensions + 28 fields
│               │   └── Quality rules + examples
│               │
│               ├── references/                 # Loaded on demand
│               │   ├── scoring-rubric.md       #   Full 1-10 anchored scales
│               │   ├── output-schema.md        #   28-field schema + formats
│               │   ├── productization-templates.md  # 5 templates (A-E)
│               │   ├── industry-playbook.md    #   10 pre-analyzed industries
│               │   ├── competitor-analysis-framework.md
│               │   └── failure-patterns.md     #   10 failure modes + checklist
│               │
│               └── assets/
│                   └── example-output.md       #   Complete 28-field example
│
├── README.md
└── LICENSE
```

### How Files Work Together

```
User asks a question
        │
        ▼
SKILL.md loads (always)
        │
        ├─ Detects input mode (broad/industry/workflow/persona/constraint)
        ├─ Detects behavior mode (ideation/deep/ranking/MVP/validation/competitor/failure)
        ├─ Runs 12-step thinking procedure
        │
        ├─ Step 8  → reads scoring-rubric.md
        ├─ Step 10 → reads productization-templates.md
        ├─ Step 11 → reads competitor-analysis-framework.md
        ├─ Step 11 → reads industry-playbook.md (if industry known)
        ├─ Step 12 → reads failure-patterns.md
        │
        └─ Output → formatted per output-schema.md
```

All reference files are in the skill's `references/` directory and loaded on demand.

---

## Benchmark Results

Tested with 3 evaluation prompts comparing with-skill vs without-skill (baseline):

| Metric | With Skill | Without Skill | Improvement |
|--------|-----------|---------------|-------------|
| **Assertion Pass Rate** | 100% (19/19) | Not graded | - |
| **Avg Output Quality** | 28-field structured | Freeform list | Structured |
| **Competitor Analysis** | Full mapping | Occasional mention | Always present |
| **Failure Risk Analysis** | 10-mode check | None | Always present |
| **Scoring Rubric** | 6-dimension weighted | Ad-hoc | Consistent |
| **Avg Tokens Used** | ~38k | ~13k | 2.9x more thorough |
| **Avg Response Time** | ~5 min | ~1.5 min | Deeper analysis |

The skill uses ~3x more tokens because it follows a 12-step procedure, reads reference files, and produces comprehensive 28-field output. The result is dramatically more actionable for founders making real decisions.

---

## FAQ

### Does this require API keys or external services?
No. This is a prompt-based skill — it enhances how Claude thinks about startup ideas. No API keys, databases, or external services needed.

### Can I use this with other AI models?
The SKILL.md is a prompt framework. It works best with Claude (Opus, Sonnet) but the content of SKILL.md can be adapted as a system prompt for other LLMs. Results may vary with model capability.

### How do I get JSON output?
Add "as JSON" or "export JSON" to any prompt. Example: `Give me 5 AI startup ideas in logistics — export as JSON`

### Can I add my own industries?
Yes! Edit `references/industry-playbook.md` and add a new section following the existing format. See [Customization](#adding-new-industries).

### The skill isn't triggering in Claude Code — what do I check?

**If installed via `/plugin install`:**

1. Run `/plugin` and check the "Installed" tab for `claude-startup-validator`
2. If not listed, check "Marketplaces" tab for `nmsavaliya/claude-startup-validator`
3. Restart Claude Code after installing
4. Use explicit trigger phrases: "AI startup ideas", "AI business opportunities"

**If installed via clone + settings.json:**

1. Verify the plugin path in `~/.claude/settings.json` points to `plugins/claude-startup-validator/`
2. Check that `plugins/claude-startup-validator/.claude-plugin/plugin.json` exists
3. Verify `plugins/claude-startup-validator/skills/ai-startup-opportunity-generator/SKILL.md` exists
4. Start a new Claude Code session (plugins are loaded at session start)

**If installed as a standalone skill:**

1. Verify `SKILL.md` exists at `~/.claude/skills/ai-startup-opportunity-generator/SKILL.md`
2. Check that the YAML frontmatter is valid (name and description fields present)
3. Start a new Claude Code session (skills are loaded at session start)
4. Use explicit trigger phrases: "AI startup ideas", "AI business opportunities"

### Can I use this for non-AI startup ideas?
The skill is specifically designed for AI/ML-powered product opportunities. It maps AI capabilities to workflow pain points. For non-AI ideas, you'd need to modify the AI capability matching in Steps 5 and 13.

### Is the scoring system customizable?
Yes. Edit `references/scoring-rubric.md` to change weights, add dimensions, or modify the anchored scales. See [Adjusting Scoring Weights](#adjusting-scoring-weights).

---

## Contributing

Contributions are welcome! This project improves when founders and developers contribute real-world data.

### How to Contribute

1. **Fork** this repository
2. **Create a branch**: `git checkout -b feature/add-fintech-industry`
3. **Make your changes** (see guidelines below)
4. **Test** with at least 3 different prompts
5. **Submit a pull request** with a clear description

### What to Contribute

| Type | What's Needed | Priority |
|------|--------------|----------|
| **Industries** | New industry entries for the playbook with real workflow data | High |
| **Failure Patterns** | Additional failure modes with real-world examples | High |
| **Templates** | New productization templates for emerging AI patterns | Medium |
| **Scoring** | Improved rubric anchors or alternative weighting schemes | Medium |
| **Prompts** | Better examples or edge case handling | Medium |
| **Translations** | Non-English versions of the skill | Low |

### Guidelines

- Keep `SKILL.md` under 500 lines — add new content to reference files
- Every example must be grounded in real workflows, not hypothetical
- Test changes by running the skill with at least 3 different prompts
- Follow the existing format and tone
- Do not add speculative or unverified market data

---

## License

[MIT License](LICENSE) — free to use, modify, and distribute for any purpose, including commercial use.

---

## Star History

If this skill helped you find your next startup idea, consider giving it a star! It helps other founders discover it.

---

<p align="center">
  Built for founders, developers, and product teams who want to build AI businesses grounded in real market opportunities — not hype.
</p>

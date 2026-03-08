# Hello Claude Code — Full Guide Content

## For use with skills/add_project.md
- **Section:** Applied Projects
- **Project title:** Hello Claude Code
- **Short description (for project card):** A step-by-step guide to setting up a
  reproducible research workflow using Claude Code, GitHub Codespaces, and Supabase.
  Learn how to build a professional, protected, and fully automated project environment
  from scratch — no prior developer experience required.
- **Image:** Placeholder for now
- **Link label:** Read guide
- **Link URL:** guides/hello_claude_code.html
- **Position:** First project in the Applied Projects section

---

## Guide structure — questions as headings

Use these as the section headings of the HTML page, in this order.
Each heading is a question a researcher would naturally ask.
Definitions marked with [TOOLTIP] should appear as hover popups on the term in bold.

---

### What is Claude Code and how is it different from this chat?

Claude Code is a **command-line tool** [TOOLTIP: A program you interact with by typing
text commands in a terminal window, rather than clicking buttons in a graphical interface]
that lets Claude read, write, and run code directly inside your project. Unlike this chat
interface — where Claude gives you answers in a conversation — Claude Code operates
autonomously inside your codebase, executing real changes to real files.

Think of it this way:
- **Claude.ai (this chat)** — for planning, learning, and making decisions. Use it when
  you want to think through a problem, understand a concept, or decide between approaches.
  It has memory of your full conversation and is good for open-ended discussion.
- **Claude Code (terminal)** — for executing. It works best with clear, specific,
  actionable instructions. It reads your project files, writes code, runs commands,
  and commits changes. It does not have memory between sessions — every time you
  launch it, it starts fresh (except for what is in your CLAUDE.md file).

The best workflow combines both: use Claude.ai to develop judgment and make decisions,
then use Claude Code to execute with that judgment already baked into your instructions.

---

### Should I run Claude Code on my computer or in the cloud?

You have two options:

**Option A — Claude Code on your local machine**
You install Claude Code on your own computer. It runs in your normal terminal and
Claude can see and edit files that physically live on your hard drive.

**Option B — Claude Code inside GitHub Codespaces**
GitHub Codespaces gives you a **virtual computer** [TOOLTIP: A simulated computer
that runs on remote servers in the cloud. It behaves exactly like a real computer
but exists only as software — you access it through your browser] in the cloud,
accessible from your browser. You install Claude Code inside that virtual machine,
so Claude operates on files stored in the cloud, not on your physical computer.

**Trade-offs:**

| | Local | Codespaces |
|---|---|---|
| Setup | You manage everything | GitHub manages the environment |
| Cost | Free (pay only for Claude) | Free tier: 120 core-hours/month |
| Access | Your machine only | Any browser, anywhere |
| Risk to your computer | Higher | None — fully isolated |
| Good for | Solo, daily work | Occasional work, any device |

**Recommendation for researchers:** Codespaces is the safer starting point. Nothing
touches your computer, and the free tier is generous enough for project work that
does not happen every day.

---

### How much computing power does Codespaces give me?

GitHub Codespaces offers different **machine types** [TOOLTIP: Pre-configured virtual
computers with different amounts of CPU, RAM and storage that you choose when creating
a Codespace] you select when creating a workspace:

| Machine | CPUs | RAM | Storage |
|---|---|---|---|
| 2-core | 2 | 8 GB | 32 GB |
| 4-core | 4 | 16 GB | 32 GB |
| 8-core | 8 | 32 GB | 64 GB |
| 16-core | 16 | 64 GB | 128 GB |

For most research work — data cleaning, modeling, writing — the 2-core or 4-core
machine is plenty. The free tier gives you 120 core-hours per month, meaning a
2-core machine gives you 60 hours of free usage per month.

---

### Can I use R, Stata, or Python in Codespaces?

Codespaces runs on **Ubuntu Linux** [TOOLTIP: A free, open-source operating system
widely used on servers and in research computing. It is the same system that runs
on most university computing clusters], which supports virtually any research tool:

- **R** — fully supported, installable in minutes
- **Python** — pre-installed
- **Julia** — installable
- **LaTeX / Quarto / R Markdown** — all work for document generation
- **Stata** — the one exception. Stata is commercial software with a license tied
  to a physical machine. Running it in a cloud virtual machine likely violates its
  license terms. Check with your institution before attempting this.

---

### What plans do I need to use Claude Code?

Claude Code requires at minimum a **Pro subscription** at $20/month. The free plan
does not include Claude Code access.

| Plan | Price | Claude Code usage | Best for |
|---|---|---|---|
| Free | $0 | ❌ Not available | Chat only |
| Pro | $20/month | ✅ Light to moderate | Solo research, occasional use |
| Max 5x | $100/month | ✅ Moderate to heavy | Professional daily use |
| Max 20x | $200/month | ✅ Heavy | Full-time developer use |

Usage limits reset every five hours and are shared across Claude chat and Claude Code.
For a researcher who does not work on projects every day, Pro is more than sufficient.

---

### How do I set up my GitHub repository correctly before starting?

Before writing any code, protect your repository with two things:

**1. Branch protection on main**

Your **main branch** [TOOLTIP: The primary, official version of your project in Git.
Think of it as the published version — stable, reviewed, and trusted] should be
locked so that nothing reaches it without your explicit approval.

Go to your repository on GitHub → Settings → Branches → Add branch protection rule:
- Branch name pattern: `main`
- Enable: Require a pull request before merging

This means Claude Code can push freely to other branches, but main is sealed.
The only way to get changes into main is through a **Pull Request** [TOOLTIP: A
formal proposal on GitHub to merge one branch into another. It shows you exactly
what changed and requires a human to review and approve before the merge happens]
that you manually review and approve.

**2. A .gitignore file**

A **.gitignore** [TOOLTIP: A file that tells Git which files to never track or commit,
no matter what. Files listed here are completely invisible to Git] file prevents
sensitive files from ever reaching GitHub:

```
# Credentials - never push these
.env

# Raw data files
*.csv
*.xlsx
*.dta
*.parquet

# LaTeX compilation artifacts
*.aux
*.log
*.synctex.gz
```

The most critical entry is `.env` — this is where your cloud storage credentials
live, and it must never be pushed to GitHub.

---

### What is CLAUDE.md and why does it matter?

`CLAUDE.md` is a plain text file that Claude Code reads automatically at the start
of every session. Think of it as a standing instruction manual for your project —
the rules of the house that Claude always follows without you having to repeat them.

A good CLAUDE.md for a research project includes:
- Git rules (never push to main, always work on dev branch)
- Folder structure rules (where inputs and outputs live)
- Coding style preferences (R vs Python, naming conventions)
- What Claude is and is not allowed to do without asking

Example:
```markdown
## Git rules — CRITICAL
- NEVER push to main under any circumstances
- Always work on the dev branch
- NEVER commit .env files or credentials

## Folder structure
- Never modify files inside any input/ folder
- Always write outputs to the output/ folder of the current stage
```

You can also create a **global CLAUDE.md** [TOOLTIP: A CLAUDE.md file stored at
~/.claude/CLAUDE.md on your machine, outside any repository. It applies to every
project you work on, not just one] at `~/.claude/CLAUDE.md` for preferences that
apply across all your projects, like your coding style and general behaviour rules.

---

### How do I protect my work from Claude making mistakes?

Claude Code is powerful but not infallible. These four layers of protection cover
the main risks:

**Layer 1 — Git is your safety net**
As long as something is committed to Git, it can always be recovered. The real
danger is only when Claude does something before you have committed, or pushes
without your review. Commit frequently.

**Layer 2 — Branch protection**
With the branch protection rule in place, even if Claude tries to push directly
to main, GitHub's server rejects it. The protection is enforced server-side —
Claude cannot bypass it through terminal commands.

**Layer 3 — .gitignore**
Prevents credentials and raw data from ever reaching GitHub, regardless of what
Claude does.

**Layer 4 — Explicit instructions at session start**
Tell Claude at the start of autonomous sessions:
```
Do not run git push to main. Do not delete files without asking me first.
```

**What about Docker?**

**Docker** [TOOLTIP: A tool that creates a completely isolated mini-computer
(called a container) inside your machine. What happens inside the container cannot
affect anything outside it — it is a sealed sandbox] adds another layer by
limiting exactly which folders Claude can see and touch. It is worth adding when:
- You are running Claude autonomously for hours with no human supervision
- You are working with truly sensitive data
- You want hard filesystem boundaries, not just instructional ones

For solo research with active supervision, branch protection plus .gitignore
gives you most of the safety with much less complexity.

---

### What is DVC and why should I use it for research?

**DVC (Data Version Control)** [TOOLTIP: A free, open-source tool that does for
data what Git does for code — tracks versions, stores history, and lets you
travel back to any previous state] is a tool that sits alongside Git and manages
your data files the way Git manages your code.

Git struggles with data files because they are large, binary, and do not change
in meaningful line-by-line ways. DVC solves this by storing a tiny **pointer
file** [TOOLTIP: A small text file (ending in .dvc) that lives in your Git
repository and contains a fingerprint of the actual data file. Git tracks the
pointer; DVC uses the pointer to find the real data in cloud storage] in your
GitHub repository instead of the actual data, and storing the real data in cloud
storage.

```
GitHub repo
├── clean_data.csv.dvc    ← tiny pointer file (tracked by Git)
└── my_script.R           ← actual code (tracked by Git)

Cloud storage (Supabase)
└── clean_data.csv        ← actual dataset
```

**The luggage tag analogy:** DVC is like a luggage tag system. Your GitHub repo
holds the tags (small, lightweight). Your cloud storage holds the actual luggage
(the data). DVC makes sure every tag always points to the right bag.

**When is DVC worth using?**

| Situation | Use DVC? |
|---|---|
| Pipeline takes hours or days to run | ✅ Yes — save expensive outputs as checkpoints |
| Data comes from an external source that may disappear | ✅ Yes — preserves exact snapshot |
| Working with a team sharing intermediate outputs | ✅ Yes |
| Fast pipeline, solo project, deterministic outputs | ❌ Probably not — just rerun the code |

**The video game save point analogy:** Think of expensive pipeline stages as boss
fights. You do not save after every footstep — you save before the hard part so
if something goes wrong you do not replay the whole dungeon.

**What about storage versions?**

DVC uses **content-based hashing** [TOOLTIP: A method of generating a unique
fingerprint for a file based on its actual contents. If the file content has not
changed, the fingerprint is identical and DVC does not upload a duplicate] meaning
it only stores a new copy when the file actually changed. Running the same script
twice with identical output costs zero extra storage.

To clean up old versions no longer referenced by any Git commit:
```bash
dvc gc --cloud
```

---

### What cloud storage should I use with DVC?

DVC supports any S3-compatible storage. **S3-compatible** [TOOLTIP: A storage
service that speaks the same communication protocol as Amazon S3, meaning any
tool built for S3 (including DVC) works with it automatically without special
configuration] means you are not locked into Amazon — many services use the same
standard.

**Recommended options:**

| Service | Free tier | Best for |
|---|---|---|
| Supabase | 1 GB forever | Researchers who also want a database |
| Backblaze B2 | 10 GB forever | Pure storage, budget-friendly |
| Cloudflare R2 | 10 GB forever | No download fees |

**Why Supabase?** Beyond storage, Supabase bundles a full PostgreSQL database,
authentication, and edge functions in one free account. For a researcher, this
means your datasets, structured query results, and project metadata can all live
in the same place. The 1 GB free tier is enough for most research projects, and
`dvc gc --cloud` keeps it clean over time.

---

### How do I structure a reproducible research pipeline?

A reproducible pipeline means anyone can clone your repository, run one command,
and reproduce your entire analysis from raw data to final output. This is the
gold standard in research.

**Recommended folder structure:**

```
project/
├── Makefile                    ← master pipeline runner
├── dvc.yaml                    ← DVC pipeline definition
├── CLAUDE.md                   ← instructions for Claude Code
├── .gitignore                  ← protects credentials and data
│
├── 01_data_processing/
│   ├── code/                   ← R or Python scripts
│   ├── hand/                   ← config YAML files
│   └── output/                 ← tracked by DVC → stored in cloud
│
├── 02_cleaning/
│   ├── code/
│   ├── hand/
│   └── output/
│
├── 03_covariates/
├── 04_target/
├── 05_analysis_dataset/
├── 06_estimation/
│
└── 07_figures_tables/
    ├── code/
    ├── output/
    └── paper.tex               ← LaTeX working paper
```

**What lives where:**

| Location | Contents |
|---|---|
| GitHub repo | All code, config files, DVC pointer files, Makefile |
| Cloud storage (Supabase) | All output folders — datasets, figures, tables |
| Codespace | Your active working environment |
| .env file | Credentials — never committed, recreated each session |

**The one-command reproduction:**
```bash
git clone your-repo
dvc pull        # downloads all data from Supabase
make all        # runs the full pipeline in order
```

**dvc.yaml** [TOOLTIP: A configuration file where you define your pipeline as a
sequence of named stages. DVC tracks which stages depend on which, so it only
reruns stages affected by your changes] defines each stage and its dependencies
so DVC knows what to rerun when something changes.

---

### What is a typical work session with this setup?

```bash
# 1. Open your Codespace — code is already there from GitHub
git pull origin dev       # get latest code
dvc pull                  # restore data from Supabase

# 2. Do your work — edit scripts, run analysis

# 3. Save everything
git add 02_cleaning/code/clean.R
git add 02_cleaning/output/clean.csv.dvc   # pointer, not actual data
git commit -m "updated cleaning logic"
git push origin dev       # code → GitHub
dvc push                  # data → Supabase

# 4. When ready to publish to main
# Go to GitHub → open Pull Request → review → merge
```

---

### How do I write and preview LaTeX documents inside Codespaces?

Install LaTeX and the LaTeX Workshop VS Code extension:

```bash
sudo apt-get update
sudo apt-get install -y texlive-full
```

Then in VS Code, search for and install the **LaTeX Workshop** extension.

This gives you a near-Overleaf experience:
- Auto-compile on save — PDF updates every time you save
- Side-by-side editing — .tex source on the left, PDF preview on the right
- Click PDF text → jumps to that line in the source

Claude Code can write and edit your .tex files, compile them, and iterate based
on your instructions:
```
"Condense the introduction to 3 paragraphs and sharpen the contribution statement"
```

**Comparison with Overleaf:**

| Feature | Overleaf | Codespace + LaTeX Workshop |
|---|---|---|
| Real-time PDF preview | ✅ | ✅ On save |
| Side-by-side editing | ✅ | ✅ |
| Works with Claude Code | ❌ | ✅ |
| Version history | ✅ Built-in | ✅ Via Git (more powerful) |
| Real-time collaboration | ✅ | ⚠️ Via GitHub only |

---

### What are Skills and how do I use them?

**Skills** are reusable instruction files — markdown documents that tell Claude
Code exactly how to handle a specific repeated task, like a recipe it follows
every time.

Skills live in a `skills/` folder in your repository:

```
skills/
├── new_section.md      ← how to create a new webpage section
└── add_project.md      ← how to add a project card to a section
```

To invoke a skill, tell Claude Code explicitly:
```
Read skills/new_section.md and follow it to create the Applied Projects section
```

A well-written skill has three parts:
1. **Clarifying questions** — Claude asks before touching anything
2. **Confirmation step** — Claude summarizes its plan and waits for your approval
3. **Execution steps** — only after you confirm does Claude write any code

This pattern — ask, confirm, execute — means Claude never surprises you with
unwanted changes.

---

### What is the difference between Claude.ai and Claude Code's think mode?

**Claude.ai (this guide)** builds your understanding. You learn why things work
the way they do, develop judgment, and make informed decisions. That knowledge
lives in your head and applies to every future project.

**Claude Code think mode** is Claude reasoning about a specific execution problem.
You trigger it by saying:
```
Think carefully about this before doing anything
```
or:
```
Make a plan first and show it to me before executing
```

Claude Code will pause, reason through the problem, present a step-by-step plan,
and wait for your approval before touching any files.

**The right workflow:**
```
Claude.ai          →    Claude Code (think mode)    →    Claude Code (execute)
Plan and decide    →    Review the approach          →    Implement
```

Use Claude.ai when you are stuck on a concept or decision.
Use Claude Code when you know what you want built.

---

## Glossary of terms (for tooltips)

These are all the terms that should appear as hover tooltips on the guide page.
Each entry shows the term as it appears in the text and the popup definition.

| Term | Tooltip definition |
|---|---|
| command-line tool | A program you interact with by typing text commands in a terminal window, rather than clicking buttons in a graphical interface |
| virtual computer | A simulated computer that runs on remote servers in the cloud. It behaves exactly like a real computer but exists only as software — you access it through your browser |
| machine types | Pre-configured virtual computers with different amounts of CPU, RAM and storage that you choose when creating a Codespace |
| Ubuntu Linux | A free, open-source operating system widely used on servers and in research computing. It is the same system that runs on most university computing clusters |
| main branch | The primary, official version of your project in Git. Think of it as the published version — stable, reviewed, and trusted |
| Pull Request | A formal proposal on GitHub to merge one branch into another. It shows you exactly what changed and requires a human to review and approve before the merge happens |
| .gitignore | A file that tells Git which files to never track or commit, no matter what. Files listed here are completely invisible to Git |
| global CLAUDE.md | A CLAUDE.md file stored at ~/.claude/CLAUDE.md on your machine, outside any repository. It applies to every project you work on, not just one |
| Docker | A tool that creates a completely isolated mini-computer (called a container) inside your machine. What happens inside the container cannot affect anything outside it |
| DVC | Data Version Control — a free, open-source tool that does for data what Git does for code. It tracks versions, stores history, and lets you travel back to any previous state |
| pointer file | A small text file (ending in .dvc) that lives in your Git repository and contains a fingerprint of the actual data file. Git tracks the pointer; DVC uses it to find the real data in cloud storage |
| content-based hashing | A method of generating a unique fingerprint for a file based on its actual contents. If the content has not changed, the fingerprint is identical and DVC does not upload a duplicate |
| S3-compatible | A storage service that speaks the same communication protocol as Amazon S3, meaning any tool built for S3 works with it automatically without special configuration |
| dvc.yaml | A configuration file where you define your pipeline as a sequence of named stages. DVC tracks which stages depend on which, so it only reruns stages affected by your changes |

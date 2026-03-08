# Skill: Add Project to Section

Use this skill when asked to add a new project to an existing section.
Before writing any code, ask the clarifying questions below and wait for answers.


---

## Step 2 — Ask these clarifying questions

Ask all of these in a single message, numbered clearly:

1. **Section** — Which section should this project be added to? (e.g. Applied Projects, Research, Other)

2. **Project title** — What is the title of the project?

3. **Project content** - I will search in content folder for a subfolder with the section name and subfolder within it name [title] (or the closest name I infer). If I find something, I will print the locations and ask you, do you confirm these locations?
   - If yes: I will print the locations and continue with the following question
   - If no: I will create the subfolder with the section name if it doesn't exists and or just the sub-subfolder with the project name [title] if the section name subfolder already exists

4. **Description** — Do you want to provide a description? 
   - If yes: write down the description or share the location of document and I will create a summary
   - If no: I will create a placeholder text

5. **Image** — Do you have an image for this project?
   - If yes: provide the location in repo
   - If no: I will use a placeholder image block

6. **Link** — Is there a link for this project?
   (e.g. a PDF, an external URL, a GitHub repo)
   - If yes: provide the URL and the link label (e.g. "Read paper", "View repo",
     "See project")
   - If no: I will omit the link for now

7. **Position** — Where within the section should this project appear?
   (e.g. first, last, after a specific existing project)

---

## Step 2 — Confirm before building

Summarize your understanding:

> "I will add a project card titled '[title]' to the [section] section,
> positioned [position]. It will include: [list of fields with content].
> Shall I proceed?"

Wait for explicit confirmation before writing any code.

---

## Step 3 — Add the project

Only after confirmation:

1. Read index.html to understand the overall structure and style
2. Read the relevant section HTML file (e.g. applied_projects.html)
   to understand the existing card structure
3. Identify an existing project card (if any) to use as a formatting reference.
   If no cards exist yet, use the section's empty state structure as reference
4. Build the new card matching the exact style — same spacing, image dimensions,
   font sizes, button styles, and card patterns
5. Insert it at the correct position within the section file
6. Validate the HTML is well-formed
7. Commit with message: "add [project title] to [section name]"

---

## Rules
- Never modify other project cards while adding the new one
- Never change the section's layout or styling
- If an image is not provided, use a styled placeholder div — never use
  external placeholder image services
- If a link is not provided, omit the button entirely — do not add a
  disabled or greyed-out button
- If the user's answers are ambiguous, ask a follow-up before proceeding

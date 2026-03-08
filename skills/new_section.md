# Skill: New Section

Use this skill when asked to create a new section on the webpage.
Before writing any code, you MUST ask the following clarifying questions
and wait for answers. Do not proceed until all are answered.

---

## Step 1 — Ask these clarifying questions

Ask all of these in a single message, numbered clearly:

1. **Section name** — What is the title of the new section as it should appear on the page?

2. **Purpose** — What is this section for? What will it contain?
   (e.g. project cards, a list of publications, a bio paragraph, etc.)

3. **Layout** — How should items be arranged?
   (e.g. grid of cards, vertical list, two columns, single block of text)

4. **Card/item contents** — If the section contains repeating items (like project cards),
   what fields should each item have?
   (e.g. title, description, image, link, date, tags)

5. **Empty state** — Should the section show a placeholder message when there is no
   content yet, or just show the section header with nothing below it?

6. **Navigation** — Should a link to this section be added to the navigation menu?

7. **Position** — Where on the page should this section appear?
   (e.g. after the About section, at the bottom of the page)

---

## Step 2 — Confirm before building

Once the user answers, summarize your understanding in plain English:

> "I will create a section called X, positioned after Y, with a Z layout.
> Each item will show: [list fields]. I will add it to the navigation menu.
> The empty state will [show placeholder / show nothing].
> Shall I proceed?"

Wait for explicit confirmation before writing any code.

---

## Step 3 — Build the section

Only after confirmation:

1. Read index.html to understand the overall structure, navigation and style
2. Read any existing section HTML files to use as a formatting reference
3. Create a new HTML file for this section (e.g. applied_projects.html)
   matching the exact style of existing section pages — same spacing, fonts,
   colors, heading levels, and card patterns
4. Add a navigation link in index.html pointing to the new section page (if there is already one modify accordingly)
5. Validate the HTML is well-formed in both files
6. Create a folder in the content folder which will serve to store all the content attached to this section page (e.g. pfd projects, images). The folder will have the same name ass the html file
7. Preview the new HTML created

---

## Rules
- Never invent content — use placeholders like "Project Title" and "Description goes here"
- Never change existing styles or sections while adding the new one
- If the user's answers are ambiguous, ask a follow-up before proceeding

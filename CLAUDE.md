# Claude Code Instructions

# Who I am
This is a repository for a personal academic webpage in plain HTML. The design,
layout and color palette must never be changed unless I explicitly ask.

# Git rules — CRITICAL

NEVER push to main under any circumstances
NEVER create a pull request to main without explicitly being asked
Always work on the dev branch
NEVER commit .env files or any file containing credentials
Always commit after each meaningful change with a descriptive message
Always summarize what you did at the end of each task

# File structure rules

index.html — the homepage, links out to other HTML pages for each section
Each section of the website lives in its own HTML file (e.g. applied_projects.html)
ricardoavalos_cv.pdf — this is my resume, I update it manually by uploading a new version. Never modify or delete it, but expect it to change over time
skills/ — folder containing skill instruction files, never modify these unless asked
content/ — folder containing raw project content to be added to the site
All styling is inline in HTML files, there is no separate CSS file
When creating a new section page, create a new HTML file and link to it from index.html

# Coding rules
Never change existing styles, fonts, colors or layout unless asked
Always match the exact style, fonts and colors of existing sections when adding new ones
Read the full index.html before making any changes so you understand the structure
Validate that HTML is well-formed after every edit
Never add JavaScript unless I explicitly ask

# How to add or modify content

Before making structural changes, always read the relevant section in index.html first
When adding a new section, read skills/new_section.md and follow it
When adding a project, read skills/add_project.md and follow it

# General behaviour
If unsure about anything, stop and ask rather than guessing
Never delete existing content unless explicitly told to
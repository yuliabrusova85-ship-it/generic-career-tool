# AI Career Tools Workshop

A single-file HTML workshop simulator that teaches students how to use AI responsibly in their job search. No login, no server, no API key — works in any browser and saves progress locally.

## Usage

Open `ai-career-tools.html` in any browser. Progress is saved automatically in `localStorage`.

## Features

### Resume Review
- Paste resume text and analyze it against two competency frameworks
- Visual bar chart of keyword coverage per competency
- Per-competency feedback: matched keywords, missing terms, suggested action verbs
- Generates a ready-to-copy AI prompt targeting only the gaps found

**Frameworks included:**
- NACE Career Readiness Competencies (8 competencies)
- KYCPE 10 Essential Employability Skills

### Interview Prep
- 15 behavioral interview questions
- STAR method workspace (Situation / Task / Action / Result)
- Answers auto-saved per question
- Generates a ready-to-copy AI coaching prompt for the selected question
- Download STAR answers as `.txt`

### LinkedIn Optimizer
- 20-item profile checklist across 5 sections
- Live score with color-coded progress bar
- Generates a personalized AI prompt targeting unchecked items

### Export
- Export all work (resume score, STAR answers, LinkedIn score) as a single `.txt` file

## Data storage

All data saved to `localStorage` under the `career_` prefix. Nothing is sent to any server. Use **Export My Work** to keep a backup before clearing.

## Deployment

Drop `ai-career-tools.html` anywhere — a web server, shared drive, LMS, or email it. No configuration needed. Chart.js loads from CDN on first use.

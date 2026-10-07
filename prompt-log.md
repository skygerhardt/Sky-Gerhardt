# Prompt Log

This file records meaningful AI-assisted work completed in this portfolio.

Entries are added as the work happens and are not backfilled.

---

## September 20, 2026 — Personal LLM Foundation Setup

### What I asked
I used ChatGPT to help me set up the personal LLM foundation for my professional portfolio, including my AGENTS.md file, CLAUDE.md file, reusable bio-review skill, and review-bio slash command.

### What the AI produced
ChatGPT helped me draft:
- Personal AI working preferences for AGENTS.md
- A one-line CLAUDE.md reference
- A reusable `review-bio` skill
- A `/review-bio` command

### What needed correction or improvement
I compared the AI-generated setup with the course instructions and made changes so the file names, structure, and requirements matched the assignment. 

I reviewed the instructor feedback and corrected the repository structure to match the course conventions. I added README files to the analysis/ and docs/ folders and removed the duplicate /review-bio command from skills/review-bio/.claude/commands/, keeping the main version in .claude/commands/ as the single source of truth.

### How I reviewed or verified it
I reviewed each file before committing it to GitHub and compared the repository structure with the course onboarding instructions.

### Final outcome
I created a reusable AI workflow that can review my professional bio while following my preferred writing style and portfolio standards. 

## October 5, 2026 — Perfect Competition Brief Critique

### What I asked
After writing and committing my engagement brief on my own, I used AI to critique the reasoning without rewriting or changing the brief. I asked it to identify implicit assumptions, unsupported claims, three questions a client might ask, and whether my hypothesis was falsifiable.

### What I learned
The critique pointed out that my assumptions about stable prices, labor availability, and the labor formula still need to be tested. It also identified my predictions about tomato capacity, carrot and mesclun capacity, and labor being the primary constraint as claims that the model will need to confirm or reject.

### What I did with it
I used the critique only to check the strength and falsifiability of my reasoning. I did not rewrite or change my committed engagement brief.

## October 5, 2026 — Perfect Competition Model Build

### What I asked
I used my committed marginal-analysis specification as the requirements for generating the Excel workbook. The workbook needed to follow the named inputs, calculation logic, constraints, outputs, and validation rules already written in my spec.

### What was produced
A model.xlsx workbook was generated with named inputs, crop and labor calculations, marginal-cost schedules, a Solver-ready model, validation checks, and a summary of the model results.

### What I still need to verify
I still need to run Solver from the required 0/0/0 and 20/0/0 starting points in an editable desktop version of Excel, complete the Farm Profit Lab cross-check, and record the audit findings before marking the specification as audited.

## October 5–6, 2026 — Perfect Competition Stage 3

### Tool
ChatGPT

### What I asked
I used ChatGPT to help organize the evidence from my completed marginal-analysis model, check the numerical results I was using in my analysis, create the required marginal-cost figures, and help edit my Stage 3 analysis and decision memo.

### What I got
ChatGPT helped identify the model results that were most important for the four Stage 3 questions, including the tomato stopping point, the binding crop constraints, the drop in tomato marginal cost between beds 5 and 6, and the standalone profitability of each crop. It also helped create the two marginal-cost-versus-price figures used in my analysis.

### What I did with it
I compared the AI-supported results with my workbook and the Farm Profit Lab before using them in my final analysis. I also edited the wording so the analysis reflected how I understood the model and the economic reasoning behind the recommendation.

### Reflection
AI helped me organize my model results and figure out which numbers actually mattered most for my analysis. It was also helpful for creating the charts and making my final analysis clearer and less repetitive. At the same time, I did not just assume that everything AI gave me was correct. I checked the tomato labor calculation at q = 1 myself and got 99 hours, and I also used the Farm Profit Lab to verify the 5th tomato bed. The lab showed about $1,139 in marginal profit, which implies a marginal cost of about $7,661, and that matched my workbook's $7,660.43 after rounding. This showed me that AI was really useful for organizing and explaining the results, but I still needed to check the calculations myself and make sure the conclusions actually matched what my model was showing.

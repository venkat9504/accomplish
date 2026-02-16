---
name: echo-brief
description: Build a context-aware intelligence brief from web updates, validate with multi-source consensus, and produce concrete developer actions tied to the local project.
command: /echo-brief
verified: true
---

# Echo Brief

Generate a high-signal, project-aware intelligence brief with actionable next steps.

Use this when the user asks for:
- daily or weekly tech brief
- updates that matter to their current codebase
- release or security monitoring with concrete actions

## Workflow

1. Build local interest profile first
- Read workspace context before web research:
  - root and package READMEs
  - `package.json`, lockfiles, and key config files
  - active issue/plan docs in the repo (if present)
- Extract stack and priorities:
  - languages/frameworks
  - major dependencies/providers
  - deployment/runtime constraints
- Split into:
  - must-track topics
  - useful topics
  - ignore topics

2. Collect candidate updates
- For each must-track topic, gather candidate headlines from primary sources first:
  - official release notes/changelogs
  - security advisories
  - official docs/blogs
- Add secondary sources only to expand context, not to replace primary evidence.
- Record publication date for each candidate.

3. Apply consensus validation
- Do not ship a headline unless it is confirmed by at least 3 independent sources, with at least 1 primary source.
- Compare claims across sources and flag conflicts explicitly.
- Assign confidence:
  - high: consistent across trusted sources
  - medium: minor discrepancy
  - low: conflicting or weak evidence

4. Prioritize and convert into actions
- Score each item for project relevance (0-5).
- Keep top 3-7 items.
- For each selected item include:
  - what changed
  - why it matters for this project
  - dev action (specific, executable, and scoped)
  - urgency (`now`, `this week`, `watch`)

5. Produce a markdown brief
- Write the brief to:
  - `reports/echo-brief/<YYYY-MM-DD>-echo-brief.md`
- Create directories if missing.
- Use `assets/brief-template.md` as the output structure.

6. Return concise delivery message
- In chat, provide:
  - 3-5 bullet executive summary
  - exact path to generated brief
  - top immediate action

## Quality Bar

- No fabricated versions, dates, CVEs, or release notes.
- If a claim cannot be validated, label it `unverified` and exclude from priority items.
- Prefer precision over volume.
- Keep promotional or duplicate content out of the final brief.
- Include source links in the markdown output for every item.

## Reference Material

- Trusted source guidance:
  - `references/trusted-sources.md`
- Output format template:
  - `assets/brief-template.md`


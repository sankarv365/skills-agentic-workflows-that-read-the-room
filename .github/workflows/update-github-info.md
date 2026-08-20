---
name: update-github-info

on:
  schedule: daily
  workflow_dispatch:

tools:
  edit:
  web-fetch:
  github:
    toolsets:
      - repos

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates that help developers learn GitHub faster.

## Sources and repository context

1. Read `notes/mona-notes.md` with the repository file tools.
2. Read the current `site/content/github-info.md` with the repository file tools.
3. Use the `web-fetch` tool to fetch and read https://github.blog/latest/.
4. Use the `web-fetch` tool to fetch and read https://github.blog/changelog/.
5. Use the `web-fetch` tool to fetch and read https://awesome-copilot.github.com/workflows/.
6. Use GitHub repository API tools for any additional repository guidance or reference files. Do not use terminal, CLI, bash, or sandboxed commands to read repository guidance.

## Update rules

- Update only `site/content/github-info.md`.
- Keep summaries short, practical, and useful to developers.
- Preserve the existing editorial angle and Markdown structure.
- Mention the source whenever an update comes from the GitHub Blog or GitHub Changelog.
- Mention Awesome Copilot as the source whenever an update comes from https://awesome-copilot.github.com/workflows/.
- Do not invent details, dates, links, or product claims. Use only information supported by the fetched sources.
- If there is no worthwhile, well-supported update, leave the file unchanged.

## Review process

When the update is complete, use the `create-pull-request` safe output to open a pull request containing the proposed change for Mona to review. The pull request should briefly summarize the updates and link to the relevant GitHub Blog or Changelog sources. Never write changes directly to the `main` branch.

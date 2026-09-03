---
name: update-github-info
description: Reviews GitHub Blog and Changelog updates and proposes edits to the GitHub Info site content for Mona to review.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

engine: copilot

tools:
  edit:
  web-fetch:

network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    labels: [automation]
    draft: true
---

# Update GitHub Info

Keep the GitHub Info website's content current with the latest GitHub Blog and
Changelog stories, following Mona's editorial guidance.

## Steps

1. Read [notes/mona-notes.md](../../notes/mona-notes.md) to understand Mona's
   editorial angle and expectations for this site.
2. Fetch <https://github.blog/latest/> to review the most recent GitHub Blog posts.
3. Fetch <https://github.blog/changelog/> to review the most recent GitHub Changelog entries.
4. Fetch <https://awesome-copilot.github.com/workflows/> to review the latest Awesome
   Copilot workflows.
5. Compare what you find against the current content in
   [site/content/github-info.md](../../site/content/github-info.md).
6. Update `site/content/github-info.md` with concise, practical summaries of any
   noteworthy new stories or changes, mentioning the source (GitHub Blog, GitHub
   Changelog, or Awesome Copilot workflows) for each item you add, per Mona's notes.
   Keep existing content that is still accurate; avoid unnecessary rewrites.
7. Open a pull request with your changes so Mona can review everything before it
   goes live. If there is nothing worth updating, do not open a pull request.

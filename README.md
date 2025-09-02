Quarto Blog Plan (GitHub Pages)
Goals

Publish weekly posts across RL, NLP, ML, Uncertainty Quantification (UQ).

Start with an RL mini-series (clearly labelled, sequential).

Add static pages: Introduction/About, Publications, Honors, Contact.

Site-wide communication: Giscus comments, email link, and optional contact form.

Automated deploy with GitHub Actions.

1) Repository Layout
your-blog/
├─ _quarto.yml
├─ index.qmd
├─ about.qmd
├─ publications.qmd
├─ honors.qmd
├─ contact.qmd
├─ posts/
│  ├─ _metadata.yml
│  ├─ rl/
│  │  ├─ _metadata.yml
│  │  ├─ 2025-09-01-rl-series-01-exploration-overview.qmd
│  │  ├─ 2025-09-08-rl-series-02-epsilon-greedy-thompson.qmd
│  │  ├─ 2025-09-15-rl-series-03-ucb-bandits.qmd
│  │  ├─ 2025-09-22-rl-series-04-intrinsic-motivation.qmd
│  │  └─ index.qmd   # RL series hub
│  ├─ nlp/
│  │  └─ index.qmd
│  ├─ ml/
│  │  └─ index.qmd
│  └─ uq/
│     └─ index.qmd
├─ static/           # images, diagrams, downloadable artifacts
├─ refs.bib          # optional bibliography
├─ .github/
│  └─ workflows/
│     └─ publish.yml
└─ requirements.txt  # optional (for notebooks/code execution)

2) Quarto Configuration (_quarto.yml)
project:
  type: website
  output-dir: _site

website:
  title: "Your Name — RL · NLP · ML · UQ"
  description: "Weekly deep dives on reinforcement learning, NLP, ML, and uncertainty quantification."
  site-url: https://<your-username>.github.io/<repo-name>/
  navbar:
    left:
      - text: Home
        href: index.qmd
      - text: Posts
        href: posts/index.qmd
      - text: RL Series
        href: posts/rl/index.qmd
      - text: NLP
        href: posts/nlp/index.qmd
      - text: ML
        href: posts/ml/index.qmd
      - text: UQ
        href: posts/uq/index.qmd
      - text: Publications
        href: publications.qmd
      - text: Honors
        href: honors.qmd
      - text: About
        href: about.qmd
      - text: Contact
        href: contact.qmd
    right:
      - icon: github
        aria-label: GitHub
        href: https://github.com/<your-username>/<repo-name>

  sidebar:  # optional contextual sidebar on posts
    collapse-level: 1
    contents:
      - section: "Series & Topics"
        contents:
          - posts/rl/index.qmd
          - posts/nlp/index.qmd
          - posts/ml/index.qmd
          - posts/uq/index.qmd

  page-footer:
    left: "© {{< var year >}} Your Name"
    right:
      - text: "RSS"
        href: posts/index.xml
      - text: "Email"
        href: "mailto:your.name@domain.com"
      - text: "GitHub"
        href: "https://github.com/<your-username>"

  comments:
    giscus:
      repo: <your-username>/<repo-name>
      category: Announcements
      mapping: pathname
      reactions-enabled: true
      input-position: top
      theme: light

format:
  html:
    theme: cosmo
    toc: true
    code-copy: true
    highlight-style: github
    smooth-scroll: true
    include-in-header:
      text: |
        <meta name="robots" content="index,follow" />
        <meta property="og:type" content="website" />
        <!-- Optional analytics -->
        <!-- <script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script> -->
    include-after-body:
      text: |
        <!-- Simple contact link in footer already provided -->

execute:
  freeze: auto  # cache computations; re-run only changed posts

metadata-files:
  - posts/_metadata.yml

profile:
  default: true

3) Posts Defaults (posts/_metadata.yml)
# Applies to all posts
title-block-banner: true
comments: true
categories: [post]
format:
  html:
    toc: true
    toc-depth: 3
    fig-cap-location: bottom
    df-print: kable


RL subfolder metadata (posts/rl/_metadata.yml)

# Defaults for RL series
categories: [RL]
series: "Foundations of RL: Exploration"
listing:
  sort: "date desc"
  type: default
  categories: true
  feed: true

4) Index Pages
Site Home (index.qmd)
---
title: "Welcome"
image: static/og-card.png
---

**Weekly deep dives** on **Reinforcement Learning**, **NLP**, **Machine Learning**, and **Uncertainty Quantification**.

- Start with the **[RL Exploration Series](posts/rl/index.qmd)**.
- Browse all **[Posts](posts/index.qmd)** or jump to **[NLP](posts/nlp/index.qmd)**, **[ML](posts/ml/index.qmd)**, **[UQ](posts/uq/index.qmd)**.

> 👋 Questions or feedback? Comment below each post or **[contact me](contact.qmd)**.

Posts Hub (posts/index.qmd)
---
title: "All Posts"
listing:
  contents: .
  sort: "date desc"
  type: default
  categories: true
  feed: true
page-layout: article
---

Browse the latest posts across RL, NLP, ML, and UQ.

RL Series Hub (posts/rl/index.qmd)
---
title: "RL Exploration Series"
description: "A practical, code-first series on exploration methods in reinforcement learning."
listing:
  contents: .
  sort: "date"
  type: default
  feed: true
---

This series walks through core exploration strategies:

1. Overview of exploration–exploitation trade-offs
2. ε-greedy & Thompson Sampling
3. Upper Confidence Bound (UCB)
4. Intrinsic motivation & curiosity
5. (Planned) Exploration in deep RL (Bootstrapped DQN, NoisyNets)
6. (Planned) Count-based & pseudo-count exploration
7. (Planned) Exploration in sparse-reward tasks

Subject Hubs (NLP / ML / UQ)

Create posts/nlp/index.qmd, posts/ml/index.qmd, posts/uq/index.qmd with similar listings:

---
title: "NLP"
listing:
  contents: .
  sort: "date desc"
  type: default
  categories: true
---
Topic hub for Natural Language Processing.

5) Static Pages
About (about.qmd)
---
title: "About"
---

Short introduction, research interests (NLP, RL, UQ), and current affiliations.

- **Email:** your.name@domain.com
- **GitHub:** <https://github.com/<your-username>>
- **Google Scholar / ORCID:** links here

I publish weekly deep dives and maintain code snippets for reproducibility.

Publications (publications.qmd)
---
title: "Publications"
---

- **[Title, Venue, Year]** — brief one-line summary. [PDF](#) · [Code](#) · [BibTeX](#)
- ...

Honors (honors.qmd)
---
title: "Honors & Awards"
---

- **Year — Award Name**, granting org. One-line context.
- ...

Contact (contact.qmd)
---
title: "Contact"
---

- **Email:** [your.name@domain.com](mailto:your.name@domain.com)
- **GitHub Issues/Discussions:** Use the comment box beneath any post.

Optional form (Formspree example):

<form action="https://formspree.io/f/<your-id>" method="POST">
  <label>Your email:<br/><input type="email" name="email" required></label><br/>
  <label>Your message:<br/><textarea name="message" rows="6" required></textarea></label><br/>
  <button type="submit">Send</button>
</form>

6) RL Series: First Posts (skeletons)
Post 1 (posts/rl/2025-09-01-rl-series-01-exploration-overview.qmd)
---
title: "RL Exploration #1 — The Exploration–Exploitation Trade-off"
description: "Intuition, taxonomy, and when each method shines."
date: 2025-09-01
categories: [RL, Exploration]
tags: [overview, bandits, MDP]
image: static/rl-01-card.png
draft: false
---

## Why exploration matters

- Problem framing, regret, sample efficiency.

## Methods at a glance

- ε-greedy, UCB, Thompson Sampling, intrinsic motivation.

## Tiny experiment

- Simulate K-armed bandit; compare regret curves.

## Takeaways

- When to choose which method; pitfalls.

Post 2 (posts/rl/2025-09-08-rl-series-02-epsilon-greedy-thompson.qmd)
---
title: "RL Exploration #2 — ε-greedy vs Thompson Sampling"
description: "Hands-on comparison with bandit simulation."
date: 2025-09-08
categories: [RL, Exploration]
tags: [epsilon-greedy, thompson-sampling, bandits]
image: static/rl-02-card.png
draft: false
---

## Setup

- Synthetic rewards; stationary vs non-stationary.

## Results

- Cumulative reward, regret; sensitivity to hyperparameters.

## What to try next

- Contextual bandits; priors; batched exploration.


(Add Posts 3–4 similarly.)

7) Communication & Comments

Giscus is enabled site-wide via _quarto.yml → website.comments.giscus.

Email & footer links present on every page (navbar/footer).

Contact form on contact.qmd (optional).

Encourage readers with a block at end of each post:

---
# in each post front matter or body end:
---

> 💬 Questions or suggestions? Leave a comment below or **[contact me](../../contact.qmd)**.

8) Publishing (GitHub Actions)
Workflow (.github/workflows/publish.yml)
name: Quarto Publish
on:
  push:
    branches: [ main ]
  workflow_dispatch:
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with: { fetch-depth: 0 }
      - uses: quarto-dev/quarto-actions/setup@v2
      - uses: actions/setup-python@v5
        with: { python-version: '3.11' }
      - run: pip install -r requirements.txt || true
      - run: quarto render
      - uses: quarto-dev/quarto-actions/publish@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          target: gh-pages

Requirements (optional, if you run notebooks)

requirements.txt

jupyter
numpy
pandas
matplotlib
scipy


GitHub Pages: In Settings → Pages, set Source: GitHub Actions.

9) Taxonomy & Series Conventions

Categories: use one of [RL, NLP, ML, UQ].

Tags: method- or topic-specific (e.g., bandits, UCB, transformers, calibration, conformal).

Series: set series: "Foundations of RL: Exploration" in RL posts to group the sequence.

Filenames: prefix date YYYY-MM-DD for chronological builds.

10) SEO, Social, Accessibility

Provide image: in front matter for social cards (1200×630).

Always set description: in front matter (≤160 chars).

Add alt text to images: ![Alt text](path "caption").

Use headings in order (H2→H3), avoid overly wide figures.

11) Weekly Cadence & Backlog

Keep a backlog of 6–8 draft outlines (can live as .qmd with draft: true).

Publish Mondays 9:00 local time (schedule your push).

Each post ends with “What to try next” + GitHub repo/code links.

12) Quick Start Checklist

 Create repo and copy the structure above.

 Replace placeholders (<your-username>, domain, email).

 Enable Discussions on repo (for Giscus).

 Add Formspree ID to contact.qmd if using a form.

 Push to main → verify GitHub Actions deploys to gh-pages.

 Set a custom domain (optional): add CNAME and DNS.

 Publish RL Post #1; share RSS link.

13) Optional Enhancements

Search: add client-side search via Fuse.js (small script) or Quarto’s built-in search (enabled by default in recent versions).

Analytics: uncomment Plausible (privacy-friendly) or add GA4 snippet.

Notebooks: if heavy, set execute: { freeze: true } and commit rendered outputs.

14) Post Template (copy for new posts)
---
title: "<Concise, compelling title>"
description: "<<=160 char summary>"
date: 2025-09-xx
categories: [RL]        # or NLP/ML/UQ
tags: [<method>, <topic>]
image: static/<card>.png
draft: false
# series: "Foundations of RL: Exploration"  # include if part of a series
---

## TL;DR
One-paragraph summary + key figure.

## Problem
Context, assumptions, related work (cite [@paper2024]).

## Method/Experiment
Minimal, reproducible code and figures.

## Results
Plots, metrics, brief discussion.

## Takeaways
When to use, pitfalls, links to code & data.

> 💬 Comments welcome below or reach out via **[contact](../../contact.qmd)**.
# Trigger deployment

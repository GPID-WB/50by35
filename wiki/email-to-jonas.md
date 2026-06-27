# Email to Jonas — 50by35 Book Repository

---

**To:** Jonas  
**Subject:** Re: 50by35 book — repository is ready

---

Hi Jonas,

Good news — I've set up the repository for the 50by35 monitoring framework book.
Everything is in place: the book structure, the chapter stubs, the automated
publishing pipeline, and documentation for your co-authors. Here is what you need
to know to get started.

---

## The Live Book

The book publishes automatically to this URL every time someone pushes a change:

> **https://GPID-WB.github.io/50by35/**

The repository itself lives here:

> **https://github.com/GPID-WB/50by35**

---

## What I Set Up

- **Six chapter stubs** ready to be filled in (`chapters/` folder)
- **Automated publishing** — every push to `main` rebuilds and redeploys the book
- **Stata + R support** — both languages work out of the box
- **Contributor guides** in the `wiki/` folder covering everything your co-authors
  need to know

---

## Your One-Time Setup

You will need to install four things on your Windows machine. You only do this once.

| # | Software | Download link |
|---|---|---|
| 1 | **Git** | https://git-scm.com/downloads |
| 2 | **Quarto** | https://quarto.org/docs/get-started/ |
| 3 | **R** | https://cran.r-project.org/bin/windows/base/ |
| 4 | **Positron** | https://positron.posit.co/ |

Positron is the IDE we are using — it is free, built for data science, and works
seamlessly with Quarto and R. Stata you already have — nothing to do there.

After installing, open Positron and run this in the **Console** panel:

```r
install.packages(c("tidyverse", "haven", "knitr", "gt", "ggplot2", "scales", "here"))
```

Then clone the repository. Open the **Terminal** in Positron (`View → Terminal`) and run:

```bash
git clone https://github.com/GPID-WB/50by35.git
```

Then open the `50by35` folder: **File → Open Folder…** and select it.

---

## Day-to-Day: How to Save and Share Changes

Once you have the repository on your machine, the routine is always the same three
commands in the Positron Terminal:

```bash
git add .
git commit -m "Brief note about what you changed"
git push
```

The book rebuilds automatically after every push. That's it.

> **If you ran any Stata code**, run `quarto render` once before the three commands
> above. This is explained in detail in `wiki/r-and-stata-usage.md`.

---

## For Your Co-Authors

Point them to `wiki/contributing.md` in the repository — it has step-by-step setup
instructions written specifically for Windows users with Positron. The short version
of what to tell them:

1. Install Git, Quarto, R, and Positron (links above).
2. Clone the repo: open the Positron Terminal and run
   `git clone https://github.com/GPID-WB/50by35.git`.
3. Read `wiki/contributing.md` before writing anything.
4. If they will write Stata code, also read `wiki/r-and-stata-usage.md` to
   configure Stata on their machine.

If anyone prefers to stick with RStudio, there is a short guide at
`wiki/rstudio-users.md` — everything works the same way.

---

## Where to Find Everything

| File | What it covers |
|---|---|
| `wiki/contributing.md` | Full setup and day-to-day workflow |
| `wiki/quarto-basics.md` | How to write chapters (headings, tables, citations, etc.) |
| `wiki/r-and-stata-usage.md` | R and Stata code chunks; Stata PATH setup on Windows |
| `wiki/tachyons-guide.md` | How to add styled callout boxes and highlights |
| `wiki/rstudio-users.md` | Notes for anyone who prefers RStudio over Positron |

---

Let me know if you run into any issues.

Best,  
[Your name]

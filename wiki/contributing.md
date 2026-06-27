# Contributing to the 50by35 Monitoring Framework Book

## Who This Guide Is For

This guide is for anyone contributing chapters, edits, or code to this Quarto book,
including researchers, economists, and data analysts who may be new to Quarto.
Instructions are written for **Windows** users. macOS notes are included where the
steps differ.

## One-Time Setup

### 1. Install Git

Download from https://git-scm.com/downloads and run the installer. Accept all defaults.

Verify the installation by opening **Command Prompt** (`Win + R`, type `cmd`, press Enter)
and running:

```
git --version
```

> **macOS:** Install via Homebrew (`brew install git`) or the Xcode Command Line Tools
> (`xcode-select --install`).

### 2. Install Quarto

Download the Windows installer (`.msi`) from https://quarto.org/docs/get-started/ and
run it. Verify in Command Prompt:

```
quarto --version
```

It should report version ≥ 1.4.

> **macOS:** Download the `.pkg` installer from the same page.

### 3. Install R and RStudio

1. Download R from https://cran.r-project.org/bin/windows/base/ and run the installer.
2. Download RStudio from https://posit.co/download/rstudio-desktop/ and run the installer.

Always open RStudio from the project folder (see step 5 below).

### 4. Install R packages

Open RStudio, then in the **Console** panel run:

```r
install.packages(c("tidyverse", "haven", "knitr", "gt", "ggplot2", "scales", "here"))
```

> If your team decides to use `renv` for stricter package version control, see
> [`wiki/renv-guide.md`](renv-guide.md) instead.

### 5. Install Stata (only if you will write Stata code)

Stata must be installed on your machine. Most team members will already have it.
See [`wiki/r-and-stata-usage.md`](r-and-stata-usage.md) for how to configure Stata
so Quarto can find it.

### 6. Clone the repository

Open **Git Bash** (installed with Git) or **Command Prompt** and run:

```bash
git clone https://github.com/GPID-WB/50by35.git
cd 50by35
```

Then open the `50by35` folder in RStudio: **File → Open Project** and select the folder,
or simply double-click the `.Rproj` file if one exists.

---

## Workflow for Contributing

1. **Create a branch** for your work. In Git Bash or Command Prompt:
   ```bash
   git checkout -b your-name/chapter-topic
   ```

2. **Edit or create** your `.qmd` chapter in `chapters/`.

3. **Preview locally** before pushing. In the RStudio Terminal pane (or Git Bash):
   ```bash
   quarto preview
   ```
   This opens a live browser preview. Changes are reflected on save.

4. **If you wrote or modified Stata chunks**, render the full book locally first:
   ```bash
   quarto render
   ```
   Then commit the `_freeze/` folder along with your `.qmd` file.

5. **Commit and push** your branch:
   ```bash
   git add .
   git commit -m "feat: add baseline methodology for indicator X"
   git push origin your-name/chapter-topic
   ```

6. **Open a Pull Request** on GitHub against `main`. Request a review from a teammate.

7. Once approved and merged to `main`, GitHub Actions will automatically rebuild and
   publish the book to GitHub Pages.

---

## Running Terminal Commands on Windows

Throughout this guide, short commands like `git add .` or `quarto render` can be run in
any of these places — use whichever you're most comfortable with:

| Option | How to open |
|---|---|
| **RStudio Terminal** | Bottom-left pane → "Terminal" tab (easiest for R users) |
| **Git Bash** | Right-click any folder → "Open Git Bash here" |
| **Command Prompt** | `Win + R` → type `cmd` → Enter |
| **PowerShell** | `Win + X` → Windows PowerShell |

All commands in this guide work in any of these options.

---

## Commit Message Convention

Use short, descriptive messages:
- `feat:` for new content or chapters
- `fix:` for corrections
- `data:` for data updates
- `style:` for formatting changes

## Getting Help

Open an issue on GitHub or contact the team lead.

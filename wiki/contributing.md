# Contributing to the 50by35 Monitoring Framework Book

## Who This Guide Is For

This guide is for anyone contributing chapters, edits, or code to this Quarto book,
including researchers, economists, and data analysts who may be new to Quarto.

## One-Time Setup

### 1. Install Git

Download from https://git-scm.com/. Verify with `git --version`.

### 2. Install Quarto

Download the latest installer from https://quarto.org/docs/get-started/.  
Verify with `quarto --version` (should be ≥ 1.4).

### 3. Install R

Download from https://cran.r-project.org/. Install **RStudio** as your IDE.

### 4. Install R packages

Open RStudio in the project folder and run:

```r
install.packages("renv")
renv::restore()
```

This installs all required packages from `renv.lock`.

### 5. Install Stata (only if you will write Stata code)

Stata must be installed and accessible from the command line.  
See `wiki/r-and-stata-usage.md` for path configuration.

### 6. Clone the repository

```bash
git clone https://github.com/GPID-WB/50by35.git
cd 50by35
```

## Workflow for Contributing

1. **Create a branch** for your work:
   ```bash
   git checkout -b your-name/chapter-topic
   ```

2. **Edit or create** your `.qmd` chapter in `chapters/`.

3. **Preview locally** before pushing:
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

## Commit Message Convention

Use short, descriptive messages:
- `feat:` for new content or chapters
- `fix:` for corrections
- `data:` for data updates
- `style:` for formatting changes

## Getting Help

Open an issue on GitHub or contact the team lead.

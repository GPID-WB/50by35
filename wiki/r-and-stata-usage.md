# R and Stata Usage Guide

## R Code Chunks

R code chunks are delimited with ` ```{r} ` and support Quarto chunk options prefixed with `#|`.

### Annotated example

````markdown
```{r}
#| label: fig-poverty-trend       # unique ID used for cross-referencing
#| fig-cap: "Poverty headcount rate over time"
#| echo: true                     # show source code in the output
#| warning: false                 # suppress warnings

library(tidyverse)

df |>
  ggplot(aes(x = year, y = poverty_rate)) +
  geom_line() +
  labs(x = "Year", y = "Poverty rate (%)")
```
````

### Key chunk options

| Option | Purpose |
|---|---|
| `label` | Unique identifier (required for cross-refs; use `fig-` or `tbl-` prefix) |
| `fig-cap` | Caption for figures |
| `echo` | Show (`true`) or hide (`false`) the source code |
| `eval` | Execute (`true`) or skip (`false`) the chunk |
| `warning` / `message` | Suppress R warnings or messages |
| `cache` | Cache chunk output (prefer `freeze: auto` at project level instead) |

---

## Stata Code Chunks

Quarto supports Stata natively via the built-in `stata` engine (Quarto ≥ 1.4). Stata must be installed on your machine and on your system `PATH`.

### Basic example

````markdown
```{stata}
#| label: tbl-summary
#| echo: true

* Summarize household income
summarize income [aw = weight]
tabulate region
```
````

### Verifying Stata is on your PATH

Open a terminal and run:

```bash
stata -q -e "display 1"
```

If Stata is not found, add it to your PATH. On macOS, add this to your `~/.zshrc` or `~/.bash_profile`:

```bash
export PATH="/Applications/Stata/StataMP.app/Contents/MacOS:$PATH"
```

Adjust the path to match your Stata version and installation location.

---

## Using `Statamarkdown` (Alternative Approach)

If the native engine is not working, the `Statamarkdown` R package provides an alternative that calls Stata via R:

```r
install.packages("Statamarkdown")
```

Set the Stata executable path once at the top of your document or in `.Rprofile`:

```r
Statamarkdown::stata_engine_path("/usr/local/stata/stata")   # adjust as needed
```

Code chunks still use ` ```{stata} ` — no syntax change is needed.

---

## The Freeze Workflow for Stata

Because Stata requires a paid license, the GitHub Actions CI runner cannot execute Stata code. The project relies on `freeze: auto` to handle this:

1. **Write or modify** a Stata chunk in a `.qmd` file.
2. **Render locally** with Stata installed:
   ```bash
   quarto render
   ```
3. **Commit both** the `.qmd` file and the updated `_freeze/` folder:
   ```bash
   git add chapters/your-chapter.qmd _freeze/
   git commit -m "feat: add Stata summary table for indicator X"
   git push
   ```
4. GitHub Actions will render the book using the committed frozen outputs — no Stata license needed on the server.

If you forget to commit `_freeze/`, the CI build will fail on Stata chunks.

---

## Reading Stata `.dta` Files into R

Use the `haven` package to read Stata data files directly into R:

```r
library(haven)

df <- read_dta("data/raw/household_survey.dta")

# haven preserves Stata value labels as factors
df <- df |>
  haven::as_factor()    # convert labelled columns to R factors

head(df)
```

To write a processed dataset back to `.dta` format:

```r
write_dta(df_processed, "data/processed/household_clean.dta")
```

`haven` preserves variable labels, value labels, and Stata data types, making it the recommended bridge between R and Stata workflows.

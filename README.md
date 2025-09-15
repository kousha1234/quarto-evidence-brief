# Evidence Brief — Quarto (R)

Parameterised evidence brief: inputs → analysis → HTML. Includes a synthetic dataset.  
Use as a template for RWE/HEOR quick analyses.

## Requirements
- Quarto: <https://quarto.org>
- R (4.3+) with packages: `readr`, `dplyr`, `ggplot2`, `broom`, `knitr`

## Reproducible env (renv)
Optionally create a project-local library:
```r
install.packages("renv")
renv::init(bare = TRUE)
renv::install(c("readr","dplyr","ggplot2","broom","knitr"))
renv::snapshot()
```

## Render with defaults
```bash
quarto render
```
Outputs go to `docs/` for GitHub Pages.

## Render with custom params
```bash
quarto render brief.qmd \\
  -P cohort_name="My Cohort" \\
  -P data_path="data/my_data.csv" \\
  -P outcome="y_event" -P treatment="treat" \\
  -P covariates="[age,sex,bmi]" -P model="logistic"
```

## Files
- `_quarto.yml` — site config, output to `docs/`  
- `brief.qmd` — parameterized analysis (tables + forest plot, code-folding, cross-refs)  
- `data/sim_rwe.csv` — synthetic cohort (id, treat, age, sex, bmi, y_event)  

## License
MIT © 2025 Kousha Sarpari

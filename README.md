# UN World Population Analysis (R / ggplot2)

Group final project for DATASCI 306 (Intro to Statistics & Data Science with R) at the University of Michigan, Fall 2024. A team of three analyzed UN World Population Prospects data, built 18+ visualizations exploring demographic trends across regions and countries, and trained a linear regression model to predict mean childbearing age — then compared our projections against the UN's official forecasts.

📄 **[Read the full report (PDF)](./finals.pdf)**

## Project overview

Working from the UN's 2024 World Population Prospects dataset, the project covers:

1. **Data import and cleaning** — Reading multi-sheet Excel data, renaming 65+ columns for readability, filtering label/separator rows, type-coercing 50+ text columns to numeric, and writing a filtered subset for downstream analysis.
2. **Replication** — Reproducing 6 charts from Our World in Data's UN population article (world population projections, regional facets, fertility rate over time, India vs. China, life expectancy, Ukraine net migration).
3. **Exploratory analysis** — 13+ original charts examining mortality, median age, net migration, teen pregnancy, mean childbearing age, and fertility rate, with country comparisons across wealth levels (US, Canada, Switzerland, India, Qatar, Burundi, Niger, South Sudan, Eswatini, and others).
4. **Machine learning** — A linear regression model predicting mean childbearing age from total fertility rate, life expectancy, and crude birth rate. Trained on an 80/20 split, achieved R² = 0.81 on training data, and compared projections to the UN's medium-variant forecast through 2100.

## My contributions

This was a three-person project (Trisha Divecha, Taylor Lane, Melissa Werkema). My specific contributions:

- **Median age analysis** — Built the multi-country median age chart and wrote the interpretation connecting median age to poverty levels and Qatar's economic history.
- **Net migration analysis** — Built both migration charts (net migration vs. under-5 mortality scatter, and net migration over time per country) and wrote the analysis tying Qatar's 2020 labor law changes to its migration reversal.
- **Teen pregnancy analysis** — Calculated teen pregnancy rates from raw birth data, built the trend-over-time and 2023-comparison charts, and wrote the interpretation connecting wealth, child marriage law enforcement, and contraceptive access.
- **ML model** — Contributed to feature selection, model training, and the UN comparison visualization.
- **Editing and analysis paragraphs** throughout the report.

## Tech

- **R** with the tidyverse (dplyr, ggplot2, readxl, stringr)
- **caret** for the train/test split and regression model
- **R Markdown** for the reproducible report

## Sample findings

- Median age correlates strongly with wealth: Niger, Burundi, and South Sudan all sit under 20, while Canada, the US, and Ireland are above 40.
- Net migration aligns with under-5 mortality almost cleanly — countries with high under-5 mortality (Niger, Burundi) see migration near zero, while wealthy, safe countries with permissive labor policies (Qatar pre-2020) saw the highest inflows.
- Qatar's 2020 elimination of strict labor laws flipped its net migration from strongly positive to negative — a real-world consequence of a single policy change visible in the data.
- Teen pregnancy rates correlate inversely with wealth, but the mechanism is enforcement: child marriage is technically banned in South Sudan, Niger, and Guatemala, but rates remain above 15% because the laws aren't enforced.
- Our regression model predicted mean childbearing age would stay ~3 years younger than the UN's medium-variant forecast — likely because the model doesn't account for social/political shifts the UN factors in.

## Running the analysis

The full code and report are in `finals.Rmd`. To regenerate:

```r
# Required packages
install.packages(c("tidyverse", "readxl", "stringr", "caret"))

# Open finals.Rmd in RStudio and knit
```

The data source is the UN's [World Population Prospects 2024](https://population.un.org/wpp/Download/Standard/MostUsed/) — the `data/finalData.xlsx` file referenced in the .Rmd should be placed in a `data/` folder.

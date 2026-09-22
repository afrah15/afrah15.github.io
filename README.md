# afrah15.github.io

## **1. What this repository is?**

## Palmer Penguins Morphological Analysis Website

This repository contains a reproducible Quarto website featuring two computational blog posts that examine physical attributes across Antarctic penguin species (*Adélie*, *Chinstrap*, and *Gentoo*). The repository demonstrates fully reproducible workflows across both Python and R using locked virtual environments (`uv` and `renv`).

------------------------------------------------------------------------

## **2. What to install first?**

## Required Tools & System Dependencies

Before rebuilding this project, ensure the following software dependencies are installed on your system:

- **Quarto:** `v1.4` or higher
- **uv:** `v0.12` or higher (Python project and package manager)
- **R:** `v4.3` or higher
- **Python:** `3.14` (managed and downloaded automatically via `uv`)

------------------------------------------------------------------------

## **3. The exact commands, in order.**

## Reproducible Rebuild Instructions

Follow these commands in exact order to clone the repository, restore both language environments, and render the static website.

### 1. Clone the Repository

Run from your terminal in your desired parent directory:

```{bash}
git clone git@github.com:afrah15/afrah15.github.io.git
cd afrah15.github.io
```

### 2. Restore the Python Environment

```{bash}
uv sync
```

This command creates the `.venv` virtual environment and installs all required Python packages (including `jupyter`, `ipykernel`, `pandas`, `seaborn`, `matplotlib`, and `palmerpenguins`) locked in `uv.lock`

### 3. Restore the R Environment

```{bash}
R -e "renv::restore()"
```

This command launches R at the top level, triggers `renv` auto-activation, and restores all R package dependencies locked in `renv.lock`

### 4. Render the Quarto Website

Run from the root directory in your shell terminal:

```{bash}
uv run quarto render
```

Using `uv run` ensures Quarto executes Python code chunks through the project's isolated `.venv` environment.

## 4. Where the built site lands?

## Output Location & Local Viewing

Once the rendering process completes:

- **Output Directory:** The built HTML site lands in the `docs/` directory at the root of the repository.

- **Local Preview:** To view the site locally, open `docs/index.html` directly in any standard web browser (or run `uv run quarto preview` from the repository root).

## 5. Where the data comes from?

## Data Provenance & Network Requirements

- **Data Source:** Both computational posts utilize the [Palmer Penguins Dataset](https://allisonhorst.github.io/palmerpenguins/?utm_source=gemini), collected by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER. Distributed under the [CC0 1.0 Universal License](https://creativecommons.org/publicdomain/zero/1.0/?utm_source=gemini).

- **Network Requirements:** **No network access is required** during the build/render phase. The dataset is bundled directly inside the installed R and Python package dependencies (`palmerpenguins`), which are brought in locally during `uv sync` and `renv::restore()`.

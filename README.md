# 134 AB Fixed Income and Financial Derivatives

This repository contains course materials, problem sets, and computational notebooks for **MATH 134A/134B Fixed Income and Financial Derivatives** discussion sections. The content has been modified and adapted from Tianhao Wang's original notes to provide comprehensive coverage of quantitative finance topics.




## Setup Instructions

### Prerequisites
- Python 3.8 or higher
- [Poetry](https://python-poetry.org/) for dependency management

### Installing Poetry

**macOS/Linux:**
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

**Windows (PowerShell):**
```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

### Project Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/zxmath/134-Fall-2025.git
   cd 134-Fall-2025
   ```

2. **Install dependencies using Poetry:**
   ```bash
   poetry install
   ```

3. **Activate the virtual environment:**
   ```bash
   poetry shell
   ```

4. **Launch Jupyter notebooks:**
   ```bash
   poetry run jupyter lab
   # or
   jupyter lab  # if you're already in the poetry shell
   ```

### Poetry Usage

**Adding new dependencies:**
```bash
# Add a regular dependency
poetry add numpy pandas matplotlib

# Add a development dependency
poetry add --group dev pytest black

# Add a specific version
poetry add "scipy>=1.9.0,<2.0.0"
```

**Managing environments:**
```bash
# Show current environment info
poetry env info

# Show dependency tree
poetry show --tree

# Update dependencies
poetry update

# Export requirements (if needed)
poetry export -f requirements.txt --output requirements.txt
```

**Running scripts:**
```bash
# Run Python scripts in the poetry environment
poetry run python script.py

# Run Jupyter notebooks
poetry run jupyter lab

# Run any command in the environment
poetry run <command>
```




## Dependencies

Key packages used in this project:
- **NumPy** - Numerical computing
- **Pandas** - Data manipulation and analysis
- **Matplotlib/Seaborn** - Data visualization
- **SciPy** - Scientific computing and statistics
- **Jupyter** - Interactive notebook environment
- **QuantLib** - Quantitative finance library (if applicable)

## Acknowledgments

This material is adapted from **Tianhao Wang's** original course notes and has been modified for the Fall 2025 semester. The content builds upon established quantitative finance literature and incorporates modern computational approaches to financial modeling.


## License

This educational material is provided for academic use. Please respect copyright and attribution requirements when using or redistributing the content.

---

For questions about the course content, please refer to the official course materials or contact the teaching staff.
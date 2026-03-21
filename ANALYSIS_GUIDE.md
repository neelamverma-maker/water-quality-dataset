# Water Quality Analysis Guide

## Overview

This guide provides instructions for using the water quality analysis scripts to process your drinking water quality dataset and generate comprehensive visualizations and compliance reports.

## Features

✅ **Data Loading** - Supports CSV and Excel formats  
✅ **Data Cleaning** - Handles BDL values, duplicates, and missing data  
✅ **Exploratory Analysis** - Summary statistics and data quality reports  
✅ **Distribution Plots** - Box plots, histograms, violin plots, Q-Q plots  
✅ **Correlation Analysis** - Heatmaps and correlation matrices  
✅ **Compliance Checking** - EPA MCL standards verification  
✅ **Outlier Detection** - IQR and Z-score methods  
✅ **Report Generation** - Comprehensive text report with findings

## Installation

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)

### Step 1: Clone/Download Repository
```bash
git clone https://github.com/neelamverma-maker/water-quality-dataset.git
cd water-quality-dataset
```

### Step 2: Create Virtual Environment (Recommended)
```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

## Usage

### Running the Analysis Script

```bash
python water_quality_analysis.py
```

This will execute all 8 analysis sections sequentially and generate output files in the `output/` directory.

### Output Files

After running the script, you'll find:

1. **01_distribution_analysis.png** - Box plots, histograms, violin plots  
2. **02_correlation_heatmap.png** - Correlation matrix between elements  
3. **03_compliance_analysis.png** - EPA MCL compliance charts  
4. **04_outlier_analysis.png** - Outlier detection visualizations  
5. **WATER_QUALITY_ANALYSIS_REPORT.txt** - Comprehensive text report

### Using Jupyter Notebook

For interactive analysis:

```bash
jupyter notebook Water_Quality_Analysis.ipynb
```

## Analysis Details

### 1. Data Cleaning

The script automatically:
- Removes duplicate samples  
- Handles BDL (Below Detection Limit) entries  
- Converts values to numeric format  
- Removes rows with NaN values  
- Provides data quality statistics

### 2. Exploratory Data Analysis

Generates:
- Summary statistics (mean, median, std dev, min, max, range)  
- Data quality report for each element  
- Initial insights into concentration levels

### 3. Distribution Visualizations

**Box Plots**: Show median, quartiles, and outliers  
**Histograms**: Display frequency distribution  
**Violin Plots**: Show full distribution shape  
**Q-Q Plots**: Test for normality

### 4. Correlation Analysis

- Computes Pearson correlation coefficients  
- Identifies strong correlations (|r| > 0.7)  
- Visualizes as heatmap

### 5. EPA Compliance Analysis

Checks against Maximum Contaminant Levels (MCLs):

| Element | MCL (mg/L) | Category | Health Impact |
|---------|-----------|----------|---------------|
| Arsenic (As) | 0.010 | Primary | Toxic |
| Lead (Pb) | 0.015 | Primary | Highly Toxic |
| Uranium (U) | 0.030 | Primary | Radioactive |
| Copper (Cu) | 1.3 | Primary (action level) | Essential but toxic in excess |
| Iron (Fe) | 0.3 | Secondary | Affects appearance |
| Manganese (Mn) | 0.05 | Secondary | Essential trace element |
| Molybdenum (Mo) | 0.05 | Secondary | Trace element |
| Lithium (Li) | - | None | Trace element |

**Primary Standards**: Protect public health  
**Secondary Standards**: Affect appearance, taste, odor

### 6. Outlier Detection

Two methods used:
1. **IQR Method** - Outliers beyond 1.5 × IQR from quartiles  
2. **Z-Score Method** - Values with |z| > 3

### 7. Report Generation

Generates comprehensive report including:
- Dataset overview  
- Summary statistics  
- Compliance results  
- Outlier summary  
- Key findings  
- Recommendations

## Customization

### Change Data File

Edit `main()` function in `water_quality_analysis.py`:

```python
def main():
    DATA_FILE = 'your_file.csv'  # or 'your_file.xlsx'
    OUTPUT_DIR = 'output'
```

### Modify EPA Standards

Edit the `compliance_analysis()` function:

```python
epa_standards = {
    'As/mg/L': 0.010,
    'Pb/mg/L': 0.015,
    # ... modify as needed
}
```

### Adjust Visualization Parameters

```python
# Change figure size
plt.figure(figsize=(16, 12))

# Modify colors
ax.bar(data, color='your_color')

# Change DPI for higher quality
plt.savefig(path, dpi=600)
```

## Troubleshooting

### Issue: "ModuleNotFoundError: No module named 'pandas'"

**Solution**: Ensure dependencies are installed
```bash
pip install -r requirements.txt
```

### Issue: "File not found" error

**Solution**: Ensure data file is in the same directory as the script, or provide full path
```python
DATA_FILE = '/full/path/to/Water Quality Data.csv'
```

### Issue: "Cannot open XLSX file"

**Solution**: Install openpyxl
```bash
pip install openpyxl
```

### Issue: Plots not saving

**Solution**: Ensure `output/` directory exists and is writable
```bash
mkdir output
```

## Data Requirements

Your CSV or Excel file should have:
- **Column names** matching element codes (As/mg/L, Cu/mg/L, etc.)
- **Numeric values** in mg/L concentration units
- **BDL entries** for Below Detection Limit values (automatically handled)

Example structure:
```
As/mg/L,Cu/mg/L,Fe/mg/L,Li/mg/L,Mn/mg/L,Mo/mg/L,Pb/mg/L,U/mg/L
0.003,0.05,0.2,0.1,0.01,BDL,0.008,0.01
0.005,BDL,0.15,0.08,0.015,BDL,0.012,0.009
```

## Performance

- **Small datasets** (< 10,000 rows): < 1 minute
- **Medium datasets** (10,000 - 100,000 rows): 1-5 minutes
- **Large datasets** (> 100,000 rows): 5-15 minutes

## Additional Resources

- [EPA Drinking Water Standards](https://www.epa.gov/ground-water-and-drinking-water/national-primary-drinking-water-regulations)
- [WHO Water Quality Guidelines](https://www.who.int/publications/i/item/9789241549950)
- [Pandas Documentation](https://pandas.pydata.org/)
- [Matplotlib Documentation](https://matplotlib.org/)

## License

This project is open-source. See LICENSE file for details.

## Support

For issues or questions:
1. Check the Troubleshooting section
2. Review the code comments
3. Consult pandas/matplotlib documentation
4. Open an issue on GitHub

## Citation

If you use this analysis in your work, please cite:

```
Water Quality Analysis Toolkit
Repository: github.com/neelamverma-maker/water-quality-dataset
```

---

**Last Updated**: 2026-03-21
**Version**: 1.0.0
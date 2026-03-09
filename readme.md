# Battery Data Analysis Tool

This repository contains a Python-based data analysis tool designed to process Battery Management System (BMS) logs. The tool performs the following tasks:
- Unit conversions
- Statistical aggregation (Min/Max/Avg)
- Visualization of voltage, temperature, and current trends

## How It Works

The script operates as a sequential analysis pipeline for two distinct datasets:

1. **Data Ingestion**: Loads CSV files containing BMS logs.
2. **Data Processing**: Performs unit conversions and statistical calculations.
3. **Data Visualization**: Generates plots to visualize trends in voltage, temperature, and current.

## Dependencies

To use this tool, ensure the following dependencies are installed:
- Python 3.x
- Pandas
- Matplotlib
- NumPy

You can install the required packages using the following command:
```bash
pip install -r requirements.txt
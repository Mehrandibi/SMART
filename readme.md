# Battery Data Analysis Toolkit

Python toolkit for analyzing **Battery Management System (BMS) datasets** including voltage, temperature, and current measurements.

Developed by **Mehran Dibaji** for battery analytics demonstrations and exploratory analysis.

The tool processes raw BMS logs, performs unit conversion, statistical aggregation, anomaly detection, and generates visualizations to understand **electrical and thermal behavior across battery packs**.

---

# Overview

Battery systems generate high-frequency telemetry including:

- string voltages
- temperature sensors
- current measurements
- timestamps

This repository provides a **structured analysis pipeline** to convert raw logs into meaningful insights and visualizations.

The workflow includes:

```

Raw BMS CSV Logs
↓
Unit Conversion
↓
Data Cleaning & Interpolation
↓
Statistical Aggregation
↓
Anomaly Detection
↓
Visualization & Diagnostics

```

---

# Key Features

### Voltage Analysis

- Per-string voltage tracking
- Min / Max / Average voltage computation
- Voltage deviation analysis
- Voltage heatmaps across battery strings

### Thermal Analysis

- Per-sensor temperature tracking
- Thermal delta computation
- Sensor outlier detection
- Thermal heatmaps

### Current Analysis

- Rolling average smoothing
- Current trend visualization

### Data Quality

- Timestamp gap analysis
- Linear interpolation of missing data

---

# Data Processing Pipeline

## 1 Data Ingestion

The script loads **CSV battery logs** using pandas.

Example datasets:

- End-of-Line (EOL) manufacturing tests
- Field telemetry logs (e.g., Anaheim–Riverside dataset)

```

df = pd.read_csv("battery_log.csv")

```

---

## 2 Unit Conversion

Raw BMS values are converted to physical units.

Temperature

```

T (°C) = BMS_TEMP / 10

```

Voltage

```

V (Volts) = BMS_STRING_V / 1000

```

Time

```

seconds = creationDateTime / 1000

```

---

## 3 Data Cleaning

Missing sensor values are interpolated using linear interpolation:

```

pivot.interpolate(method="linear")

```

This ensures continuous datasets for visualization and statistical analysis.

---

## 4 Statistical Aggregation

The script pivots the dataset so that each timestamp contains all strings or sensors.

Example voltage aggregation:

```

V_min
V_max
V_avg

```

Example temperature aggregation:

```

T_min
T_max
T_avg

```

---

## 5 Anomaly Detection

### Voltage Imbalance

Deviation from pack average:

```

ΔV = string_mean − pack_mean

```

Reported in **millivolts**.

### Thermal Outliers

Sensors exceeding **2 standard deviations** from group mean are flagged.

```

|T_sensor − T_mean| > 2σ

```

---

# Visualizations

The toolkit generates several diagnostic plots.

### Voltage Trends

```

Voltage vs Time (per string)
Min / Max / Avg Voltage

```

### Temperature Trends

```

Temperature vs Time (per sensor)
Min / Max / Avg Temperature

```

### Heatmaps

Voltage distribution across battery strings

Temperature distribution across sensors

### Current Analysis

Rolling average smoothing

```

window_size = 500

```

---

# Example Outputs

Typical outputs include:

```

Voltage imbalance (mV)
Average thermal delta
Sensor outlier detection
Heatmaps of pack behavior

```

These diagnostics help identify:

- cell imbalance
- thermal hotspots
- sensor anomalies
- operational trends

---

# Repository Structure

```

battery-analysis/
│
├── data_analysis.py
├── requirements.txt
└── README.md

```

### data_analysis.py

Main analysis pipeline including:

- data loading
- preprocessing
- aggregation
- anomaly detection
- plotting

---

# Installation

Install dependencies:

```

pip install pandas numpy matplotlib seaborn

```

---

# Running the Script

Run locally:

```

python data_analysis.py

```

Or execute in **Google Colab**.

The original script was developed in Colab for rapid experimentation.

---

# Configuration

To adapt the script to your dataset modify:

### CSV Paths

```

pd.read_csv("your_file.csv")

```

### Smoothing Window

```

window_size = 500

```

### Outlier Detection Sensitivity

```

threshold = 2

```

---

# Dependencies

| Package | Purpose |
|-------|--------|
| pandas | Data ingestion and manipulation |
| numpy | Statistical operations |
| matplotlib | Plotting |
| seaborn | Heatmap visualization |

---

# Example Applications

This analysis workflow can be used for:

- Battery manufacturing diagnostics
- End-of-Line (EOL) testing
- Field telemetry analysis
- Pack health monitoring
- Cell imbalance detection
- Thermal management validation

---

# Author

**Mehran Dibaji, PhD, SMIEEE**

AI Systems • Battery Analytics • Energy Systems

MIT Postdoctoral Researcher  
Former AI/ML Manager – Fluence Energy

---

# License

MIT License


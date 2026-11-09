# 🧪 Agentic MLOps & Model Context Protocol (MCP) Geospatial Evaluator

An autonomous MLOps evaluation framework engineered for internal geospatial machine learning workflows. The system implements **Model Context Protocol (MCP)** tool standards to perform block-spatial cross-validation, run spatial and temporal accuracy checks across land-use sectors, and compile scientific R&D evaluation reports.

---

## 🌟 Key Features & Tool Architecture

- **Model Context Protocol (MCP) Tool Standards:** Exposes native JSON tool definitions (`check_raster_integrity`, `run_spatial_temporal_evaluations`) compatible with MCP server interfaces and LLM agent function calling.
- **Raster Integrity Validation:** Checks dataset health, scans for NaN artifacts, verifies Coordinate Reference System (`EPSG:4326`) projections, and validates spatial resolution.
- **Block-Spatial & Diurnal Split Evaluation:** Calculates spatial RMSE, MAE, and $R^2$ metrics across held-out ground truth split by land-use sectors (Urban Core, Suburban, Parkland) and diurnal cycles (Peak Afternoon vs. Nighttime).
- **Autonomous R&D Report Synthesis:** Synthesizes raw metric telemetry into executive-ready scientific Markdown reports featuring formatted markdown tables and actionable feature engineering recommendations.

> **Design Note:** Implemented in native Python to guarantee zero-dependency, deterministic execution across CI/CD pipelines while maintaining 100% compatibility with external LLM function-calling wrappers (e.g., Anthropic Claude / OpenAI / Groq APIs).

---

## 📊 Sample Generated Scientific Report

The autonomous evaluation loop generates reports formatted as follows:

# 🧪 Automated ML R&D Evaluation Report

**Model Identifier:** `HyperScale-ThermalSim-v1`  
**Evaluation Methodology:** 5-Fold Block-Spatial Cross-Validation  
**Target Variable:** Meter-Level Surface Temperature ($T_{\text{fine}}$)

---

### 1. Data Integrity & Spatial Checks
* **Dataset Target:** `thermal_data.zarr`
* **NaN Artifact Count:** `0`
* **Coordinate Reference System:** `EPSG:4326 (WGS84 Projected)`
* **Grid Spatial Resolution:** `10m x 10m Grid`
* **Validation Status:** `PASSED`

---

### 2. Held-Out Ground Truth Accuracy Metrics
* **Overall Spatial RMSE:** `0.3760 °C`
* **Overall Spatial MAE:** `0.3397 °C`
* **Block Spatial Cross-Validation R² Score:** `0.9833`

#### Per-Region Land-Use Error Breakdown

| Region Sector | Spatial RMSE (°C) | Spatial MAE (°C) |
| :--- | :---: | :---: |
| **High-Density Urban Core** | 0.4727 | 0.4474 |
| **Suburban Greenbelt** | 0.2644 | 0.2518 |
| **Parkland Canopy Zone** | 0.2083 | 0.2022 |

---

### 3. Temporal & Diurnal Heat Analysis
* **Peak Afternoon Heat (12:00–15:00):** RMSE = `0.4852 °C`
* **Nighttime Thermal Cooling (00:00–04:00):** RMSE = `0.2104 °C`

---

### 4. Key Scientific Findings & Recommendations
1. **Urban Core Thermal Loads:** Model error peaks during peak afternoon hours (`0.4852 °C` RMSE) in high-density urban areas due to unmodeled spatial surface albedo variations.
2. **Feature Engineering Recommendation:** Ingest high-resolution building height and impervious surface ratios into the next downscaling training iteration to reduce urban core residual error.

---

## 🛠️ Tech Stack & Dependencies

- **Language:** `Python 3.10+`
- **Protocol:** `Model Context Protocol (MCP)` JSON Schemas
- **Evaluation Engine:** `scikit-learn`, `numpy`, `pandas`
- **Data Layer:** `xarray`, `Zarr` (compatible with Landsat 8/9 STAC rasters)
- **Formatting:** Markdown & JSON Telemetry Serialization

---

## 🚀 How to Run Locally

Clone the repository and run the evaluator script directly:

```bash
git clone [https://github.com/Ali-jawad14/agentic-geospatial-mcp-evaluator.git](https://github.com/Ali-jawad14/agentic-geospatial-mcp-evaluator.git)
cd agentic-geospatial-mcp-evaluator
python main.py

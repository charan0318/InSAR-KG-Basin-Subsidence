# 🌍 Time-Series InSAR Based Land Subsidence Analysis

## Krishna–Godavari Basin (India)

---

## 📌 Overview

This project presents a **time-series InSAR analysis** to detect and quantify land subsidence in the Krishna–Godavari Basin using Sentinel-1 SAR data.

The workflow integrates:

* **ASF HyP3** → Interferogram generation
* **MintPy** → Time-series inversion (SBAS)
* **QGIS** → Spatial filtering and hotspot extraction

The final output identifies **high-subsidence zones (>10 mm/year)** and provides a GIS-ready dataset for further analysis.

---

## 🛰️ Dataset

| Parameter       | Details                         |
| --------------- | ------------------------------- |
| Satellite       | Sentinel-1 (C-band SAR)         |
| Product Type    | Level-1 SLC                     |
| Mode            | IW (Interferometric Wide Swath) |
| Polarization    | VV + VH                         |
| Orbit Direction | Descending                      |
| Path            | 19                              |
| Time Period     | 2018 – 2022                     |
| No. of Scenes   | ~55                             |
| Interferograms  | ~111                            |

---

## ⚙️ Methodology

### 1. Interferogram Generation

* Generated using **ASF HyP3**
* GeoTIFF outputs (unwrapped phase, coherence, DEM, geometry)

---

### 2. Time-Series Processing (MintPy)

* Small Baseline Subset (**SBAS**) approach used
* Steps:

  * Load interferogram stack
  * Network inversion
  * Time-series estimation
  * Velocity calculation

---

### 3. GIS-Based Analysis (QGIS)

* Export velocity raster (mm/year)
* Apply filtering:

  * Range: **-20 to 0 mm/year**
* Threshold extraction:

  * **< -10 mm/year → high subsidence**
* Raster → Polygon conversion
* Polygon cleaning and dissolution
* Zonal statistics for quantification

---

## 📊 Key Outputs

| Output         | Description                     |
| -------------- | ------------------------------- |
| Velocity Map   | LOS deformation (mm/year)       |
| Filtered Map   | Noise-reduced deformation field |
| Threshold Map  | High subsidence regions         |
| Final Polygons | Clean subsidence zones          |

---

## 🧠 Scientific Notes

* Deformation is **relative to a reference pixel**
* Measurements are in **Line-of-Sight (LOS)** direction
* Negative values indicate **movement away from satellite (subsidence)**
* Temporal coherence masking applied during export
* Atmospheric corrections (ERA5/GACOS) were **not applied**

---

## 📍 Key Findings

* Significant subsidence observed in **coastal delta regions**
* Maximum subsidence ~ **−10 to −25 mm/year**
* Inland regions show relatively stable behavior
* Patterns consistent with:

  * sediment compaction
  * groundwater extraction
  * deltaic geomorphology

---

## 📁 Repository Structure

```
InSAR-KG-Basin-Subsidence/
│
├── mintpy/
│   └── insar_mintpy_workflow.ipynb
│
├── qgis/
│   └── processing_steps.txt
│
├── outputs/
│   ├── velocity_map.png
│   ├── filtered_map.png
│   ├── threshold_map.png
│   └── final_polygons.png
│
├── report/
│   └── final_report.pdf
│
└── README.md
```

---

## ▶️ How to Run

1. Open the notebook in **Google Colab**
2. Mount Google Drive
3. Update data paths if required
4. Run all cells sequentially

---

## 🚀 Applications

* Infrastructure risk assessment
* Coastal subsidence monitoring
* Oil & gas basin studies
* Groundwater management

---

## ⚠️ Limitations

* LOS displacement ≠ pure vertical deformation
* No atmospheric correction applied
* Results depend on coherence quality
* Reference point assumption affects interpretation

---

## 👨‍💻 Author

**Charan N**
B.Tech – Remote Sensing / GIS

---

## 📌 Acknowledgements

* ESA Sentinel-1 Mission
* ASF HyP3 Processing Platform
* MintPy Development Team

---

## ⭐ Final Note

This project demonstrates a complete **end-to-end InSAR workflow**, from SAR data processing to GIS-based interpretation, suitable for academic and research applications.

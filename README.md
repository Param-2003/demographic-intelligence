# 📊 Census Migration Data Analysis using PySpark & Looker Studio

This project analyzes migration patterns in India based on census data. We focus on understanding where people are migrating **to**, their **previous residences**, and provide a **gender-based breakdown** of these migrations.

A data engineering + analytics project that processes large-scale population and migration data using PySpark and produces insights for political campaign targeting and policy design.
---
### 🔍 Overview
This project explores the internal migration patterns in India using the census migration dataset. We leveraged **PySpark** for large-scale data processing, **matplotlib/seaborn** for preliminary visualizations, and **Looker Studio** for interactive dashboard creation. The data consisted of millions of rows with detailed breakdowns of migration by gender, region, and duration.

---

### 🧱 Project Structure

1. **Data Ingestion**
2. **Schema Validation and Cleaning**
3. **Transformations**
4. **Segmentation (Urban, Rural, Total)**
5. **Data Visualization (matplotlib + Looker Studio)**
6. **Geo Mapping (Looker Studio)**
7. **Documentation & Export**

---

### 📂 Dataset Summary

- **Primary File**: `indiaSummary.csv` (manually cleaned)
- **Columns**:
  - Last residence
  - Place of enumeration
  - Gender-wise migration count
  - Duration-wise migration count
  - Urban/Rural classifications

---

### ⚠️ Major Challenges Faced

| Issue | Description | Fix |
|------|-------------|-----|
| Multi-header rows | Original CSV had 3 header rows | Cleaned manually in Excel to preserve column alignment |
| PySpark misreading schema | Spark misaligned column headers and data | Used custom header logic and schema enforcement |
| Memory limit issues | Pandas crashed due to CSV size | Used PySpark for all processing, Pandas only for Looker export |
| Geo chart not working | Looker Studio didn’t render Indian map correctly | Cleaned `Last_Place_of_residence` and ensured matching with Google's geo names |

---

### 🧹 Data Cleaning Steps

- Dropped corrupt and null-filled rows
- Converted numeric columns to integers
- Trimmed whitespace in string fields
- Renamed inconsistent columns
- Filtered and grouped by:
  - **Rural**, **Urban**, **Total**
  - Gender-wise segmentation
  - Last residence types (states, UTs, international)

---

### 🔄 Transformations

- Used PySpark to group migration data:
  - By gender
  - By type of region (Urban, Rural, Total)
- Computed total migrations per place of enumeration
- Prepared Pandas DataFrames (`.toPandas()`) only for export & charts

---

### 📊 Visualizations

- **Seaborn Bar Charts**: Rural vs Urban Migration by last residence
- **Looker Studio**:
  - Uploaded filtered CSVs
  - Set geo-dimensions to state names
  - Built choropleth maps
  - Used filters by gender, region

---

### 🌍 Geo Visualization Fixes

- Matched state names in `Last_Place_of_residence` with Google’s supported names
- Ensured column type was set as `"Region"` in Looker
- Manually set "Zoom Area" to `"India"`

---

### 📦 Output Files

- `rural_migration.csv`
- `urban_migration.csv`
- `total_migration.csv`
- (Optional: `male_migration.csv`, `female_migration.csv`)

---

### 📁 Technologies Used

- PySpark
- Jupyter Notebook
- Seaborn / Matplotlib
- Looker Studio
- Excel (initial cleanup)

---

### ✅ Conclusion

This project demonstrates a real-world scenario of **large-scale migration analytics** using PySpark with **end-user dashboards** in Looker Studio. It reflects typical Big 4 data engineering pipelines involving ETL, transformation, and business insight generation.


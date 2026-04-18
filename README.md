# EXPERIMENT-19-AND-20-
#

## COVID-19 Dataset Analysis using Python

**Name:** AMEY WAGHMARE
**PRN:** 25070123009
**Batch:** A1 

---

# 📌 Introduction

COVID-19 dataset analysis helps in understanding the spread and impact of the pandemic across different countries.

Using Python, we can clean, process, and visualize this data to extract meaningful insights.

---

# 🔹 Objectives

* Perform data cleaning
* Convert data types
* Calculate active cases
* Analyze country-wise data
* Visualize global spread

---

# 🔹 Dataset Loading

```python
import pandas as pd
import numpy as np

data = pd.read_csv("/content/covid_19_data.csv")
```

---

# 🔹 Data Cleaning

## Remove Unnecessary Columns

```python
data = data.drop(['SNo','Last Update'], axis=1)
```

---

## Check Data Information

```python
data.info()
```

---

# 🔹 Data Type Conversion

```python
data['ObservationDate'] = data['ObservationDate'].astype('datetime64[ns]')
data['Confirmed'] = data['Confirmed'].astype('int64')
data['Deaths'] = data['Deaths'].astype('int64')
data['Recovered'] = data['Recovered'].astype('int64')
```

📘 Ensures consistency and proper analysis.

---

# 🔹 Feature Engineering

## Active Cases Calculation

```python
data['Active'] = data['Confirmed'] - data['Recovered'] - data['Deaths']
```

📘 Active = Confirmed − Recovered − Deaths

---

# 🔹 Data Exploration

## View Specific Rows

```python
data.iloc[50:100]
```

---

## Find Latest Date

```python
data['ObservationDate'].max()
```

---

## Filter Latest Data

```python
latest_data = data[data['ObservationDate'] == data['ObservationDate'].max()]
```

---

# 🔹 Country-wise Analysis

## Count Countries

```python
latest_data['Country/Region'].value_counts()
```

```python
latest_data['Country/Region'].nunique()
```

---

## Group Data by Country

```python
countries = latest_data.groupby("Country/Region")[["Confirmed","Deaths","Recovered","Active"]].sum()
countries = countries.reset_index()
```

---

## Example: Specific Countries

```python
countries[countries['Country/Region'] == "US"]
countries[countries['Country/Region'] == "India"]
```

---

# 🌍 Data Visualization

## World Map (Choropleth)

```python
import plotly.express as px

world_map = px.choropleth(
    countries,
    locations="Country/Region",
    locationmode="country names",
    color="Confirmed",
    color_continuous_scale="reds",
    range_color=[0, 1000000]
)

world_map
```

📘 Visualizes global distribution of confirmed cases.

---

# 🔝 Top 20 Countries Analysis

```python
top = latest_data.groupby("Country/Region")[["Confirmed", "Recovered"]].sum().reset_index()
top = top.sort_values(['Confirmed'], ascending=False)

top_20 = top.head(20)
```

📘 Identifies most affected countries.

---

# 🎯 Learning Outcomes

After this experiment, the student can:

* Clean and preprocess real-world dataset
* Perform feature engineering
* Analyze time-based data
* Group and aggregate data
* Visualize global trends

---

# 📚 Applications

* Pandemic tracking
* Healthcare analysis
* Government decision-making
* Data visualization dashboards
* Predictive modeling

---

# ✅ Conclusion

COVID-19 data analysis helps in understanding the global health situation.

Using Python, we can:

* Process large datasets
* Extract meaningful insights
* Visualize data effectively

This experiment demonstrates real-world data analysis and visualization techniques.

---

## ✍ Author

Dev Anand
B.Tech ENTC – Symbiosis Institute of Technology, Pune

---


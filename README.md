# OLIVER_PA4
I reviewed your uploaded **ECE 2112 Experiment 4 PDF and your `OLIVER_PA4 (1).ipynb`**. The README below matches the actual project: Pandas data wrangling, filtering, DataFrames, category means, and visualization.  

# ECE 2112 – Experiment 4: Data Wrangling and Data Visualization

## Project Overview

This repository contains my solution for **ECE 2112: Advanced Computer Programming and Algorithms – Experiment 4**.

The activity focuses on **data wrangling and data visualization** using Python, Pandas, and Matplotlib. The project uses an ECE Board Exam dataset to filter student records, create focused DataFrames, calculate category-based averages, and visualize the results.

## Student Information

* **Name:** Justin Ylerlee D. Oliver
* **Section:** 2ECE-B
* **Course:** ECE 2112 – Advanced Computer Programming and Algorithms
* **Experiment:** 4 – Data Wrangling and Data Visualization

## Objectives

This experiment demonstrates how to:

* Filter tabular data using multiple conditions
* Create DataFrames containing selected features
* Calculate mean values for categorical groups
* Create bar charts for data comparison
* Interpret results based only on the observed dataset

## Technologies Used

* **Python**
* **Pandas**
* **Matplotlib**
* **Jupyter Notebook / Google Colab**
* **Excel dataset**

## Files

```text
├── README.md
├── OLIVER_PA4 (1).ipynb
└── board2.xlsx
```

## Tasks

### A. Visayas Communication DataFrame

The `VisComm` DataFrame filters students who:

* Are from **Visayas**
* Are enrolled in the **Communication** track

The selected columns are:

```text
Name
Gender
Math
Electronics
Average
```

The resulting DataFrame contains **5 students**.

```python
VisComm = board.loc[
    (board["Hometown"] == "Visayas") &
    (board["Track"] == "Communication"),
    ["Name", "Gender", "Math", "Electronics", "Average"]
]

VisComm
```

The number of rows is obtained using:

```python
VisComm.shape[0]
```

### B. Visayas Female DataFrame

The `VisFemale` DataFrame filters students who:

* Are from **Visayas**
* Are **Female**

The selected columns are:

```text
Name
Track
GEAS
Electronics
Average
```

```python
VisFemale = board.loc[
    (board["Hometown"] == "Visayas") &
    (board["Gender"] == "Female"),
    ["Name", "Track", "GEAS", "Electronics", "Average"]
]

VisFemale
```

Students with an `Average` of at least **60** are then selected without modifying the original `VisFemale` DataFrame:

```python
VF = VisFemale[VisFemale["Average"] >= 60]

VF
```

The resulting filtered DataFrame contains **4 students**.

## Category-Average Visualization

The project calculates the mean `Average` for three categorical variables:

* Track
* Gender
* Hometown

```python
trackmean = board.groupby("Track")["Average"].mean().round(2)

gendermean = board.groupby("Gender")["Average"].mean().round(2)

hometownmean = board.groupby("Hometown")["Average"].mean().round(2)
```

### Mean Average by Track

| Track            | Mean Average |
| ---------------- | -----------: |
| Communication    |        67.97 |
| Instrumentation  |        65.22 |
| Microelectronics |        67.50 |

### Mean Average by Gender

| Gender | Mean Average |
| ------ | -----------: |
| Female |        66.62 |
| Male   |        67.18 |

### Mean Average by Hometown

| Hometown | Mean Average |
| -------- | -----------: |
| Luzon    |        68.08 |
| Mindanao |        66.68 |
| Visayas  |        65.75 |

## Visualization

The notebook creates a single figure containing three bar charts:

```python
plt.subplots(1, 3, figsize=(16, 5))

plt.subplot(1, 3, 1)
plt.bar(trackmean.index, trackmean.values)
plt.ylim(0, 100)
plt.title("Mean Average by Track")

plt.subplot(1, 3, 2)
plt.bar(gendermean.index, gendermean.values)
plt.ylim(0, 100)
plt.title("Mean Average by Gender")

plt.subplot(1, 3, 3)
plt.bar(hometownmean.index, hometownmean.values)
plt.ylim(0, 100)
plt.title("Mean Average by Hometown")

plt.tight_layout()
plt.show()
```

## Observations

Based on the calculated sample means:

* **Track:** Communication has a mean Average of **67.97**, Microelectronics has **67.50**, and Instrumentation has **65.22**.
* **Gender:** The mean Average for males is **67.18**, while females have **66.62**.
* **Hometown:** Luzon has a mean Average of **68.08**, followed by Mindanao at **66.68** and Visayas at **65.75**.

These observations describe differences found in the dataset and **do not establish that Track, Gender, or Hometown causes differences in board-exam scores**.

## How to Run

1. Download or clone this repository.
2. Open `OLIVER_PA4 (1).ipynb` using **Jupyter Notebook** or **Google Colab**.
3. Make sure `board2.xlsx` is available in the same working directory.
4. Run the notebook cells from beginning to end.
5. View the generated DataFrames, summary tables, and visualization.

## Learning Outcomes

Through this experiment, I practiced:

* DataFrame filtering
* Multiple-condition filtering
* Column selection
* Pandas `groupby()`
* Computing mean values
* Data visualization with Matplotlib
* Interpreting categorical data

## Course Requirement

This project was completed as part of **ECE 2112 – Advanced Computer Programming and Algorithms, Experiment 4**.

---

**Author:** Justin Ylerlee D. Oliver
**Section:** 2ECE-B

The README is ready to paste directly into your GitHub repository as **`README.md`**.

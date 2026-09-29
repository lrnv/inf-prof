# INF-PROF — Final project: exploring Chicago crime data with pandas

## Objectives

This project evaluates your ability to build a complete and reproducible data-analysis workflow with Python.

You should be able to:

1. import and inspect a real dataset;
2. identify data-quality problems;
3. transform dates and categorical variables;
4. summarize data with pandas;
5. create informative figures;
6. explain your choices and your results.

The objective is **not** to use as many pandas functions as possible. Prefer clear, readable code.

## Data

Use:

```text
Chicago_Cimes_2008_to_2011.csv
```

The dataset contains reported incidents recorded by the Chicago Police Department between 2008 and 2011.

The file is relatively large. You are allowed to use `usecols=` in `pd.read_csv()` if you want to load only the columns required for a specific analysis.

> Reported incidents are not the same thing as the true incidence of crime. Results should be described as patterns in the recorded dataset.

## Reproducibility rules

Your notebook must:

- run from top to bottom without manual edits;
- import all required packages near the beginning;
- use relative paths when possible;
- contain comments or Markdown explanations;
- display the results used to support your answers.

Do not manually edit values in the CSV file.

---

# Part 1 — Data preparation and core questions

## 1. Import and inspect

1. Import the dataset.
2. Display the first and last five rows.
3. Report the number of rows and columns.
4. Display column names and data types.
5. Identify columns containing missing values and report both:
   - the number of missing values;
   - the proportion of missing values.

## 2. Duplicates and identifiers

The `ID` column is intended to identify incidents.

1. Check whether duplicated IDs exist.
2. Report how many rows are affected.
3. Remove duplicate incidents while keeping one record per ID.
4. Explain the rule you used to decide which record to keep.

Do **not** replace the DataFrame index with `ID` unless doing so helps your analysis.

## 3. Invalid identifiers

At least one row contains an invalid value in `ID`.

1. Detect rows whose `ID` cannot be interpreted as a numeric identifier.
2. Display the suspicious row(s).
3. Remove them from the cleaned dataset.
4. Convert `ID` to an appropriate numeric type.

Your code should detect the problem rather than relying on a hard-coded row number.

## 4. Dates and times

Convert `Date` to a pandas datetime variable.

Create:

- `calendar_date`;
- `hour`;
- `weekday`;
- `month`.

Then answer:

1. At which hour are the most homicide incidents recorded?
2. Which weekday has the fewest recorded theft incidents?
3. Which primary crime type is most frequent on 25 December?

For every answer, show the pandas code and the resulting table or value.

## 5. Harmonizing location descriptions

The `Location.Description` field can be overly specific.

1. Identify all location descriptions containing the word `AIRPORT`.
2. Create a cleaned location variable in which all of these values are replaced by `"AIRPORT"`.
3. Keep the original column unchanged.
4. Report the number of records affected.

## 6. Crime counts and population

For **2008 only**, compare districts using the number of recorded incidents per 1,000 inhabitants:

\[
\text{incidents per 1,000} =
\frac{\text{number of recorded incidents}}{\text{district population}} \times 1000.
\]

Use the population table below.

| District | Name | Population |
|---:|---|---:|
| 1 | Central | 25,613 |
| 2 | Wentworth | 50,957 |
| 3 | Grand Crossing | 93,384 |
| 4 | South Chicago | 141,422 |
| 5 | Calumet | 92,729 |
| 6 | Gresham | 105,360 |
| 7 | Englewood | 91,600 |
| 8 | Chicago Lawn | 244,470 |
| 9 | Deering | 165,457 |
| 10 | Ogden | 137,120 |
| 11 | Harrison | 82,392 |
| 12 | Monroe | 69,677 |
| 13 | Wood | 60,517 |
| 14 | Shakespeare | 132,459 |
| 15 | Austin | 72,736 |
| 16 | Jefferson Park | 199,898 |
| 17 | Albany Park | 156,859 |
| 18 | Near North | 110,995 |
| 19 | Belmont | 107,516 |
| 20 | Lincoln | 102,512 |
| 21 | Prairie | 78,111 |
| 22 | Morgan Park | 111,545 |
| 23 | Town Hall | 98,391 |
| 24 | Rogers Park | 151,435 |
| 25 | Grand Central | 212,535 |

Create a DataFrame containing these populations, merge it with your incident counts, and produce a **sorted bar chart**.

In your interpretation, use wording such as *recorded incidents per 1,000 residents*. Do not interpret this quantity as an individual probability of becoming a victim.

## 7. Arrest proportion by crime type

For each `Primary.Type`:

1. count the number of incidents;
2. compute the proportion with `Arrest == True`;
3. keep only crime types with at least 100 recorded incidents;
4. sort the result by arrest proportion.

Present the result as a table or horizontal bar chart.

---

# Part 2 — Open exploratory analysis

Choose **one** `Primary.Type` and investigate it in more detail.

State clearly which crime type you selected.

Produce at least **three complementary analyses**, for example:

- change in monthly incident counts;
- distribution by hour or weekday;
- most common `Description` values;
- most common cleaned location descriptions;
- geographical distribution using latitude and longitude;
- comparison of arrests across time or locations.

For each analysis:

1. state the question;
2. write the pandas code;
3. create an appropriate table or figure;
4. write a short interpretation.

Do not simply generate plots without explaining what they show.

---

# Submission

Submit **one Jupyter notebook** on Amétice.

The notebook must contain:

- code;
- tables and figures;
- written answers and interpretations;
- enough explanation for another person to reproduce your analysis.

The due date is given in the public course README and on Amétice.

## Oral examination

During the oral examination, you may be asked to:

- run part of your notebook;
- explain a pandas operation;
- justify a visualization;
- interpret one result;
- modify a small part of the analysis live.

You are evaluated on both the result **and** your understanding of the code.

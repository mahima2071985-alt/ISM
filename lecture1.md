# Lecture 1 — Basics of Statistics

## 1. What statistics is

Statistics is a branch of applied mathematics. It is the backbone of data science, AI, ML, and information technology.

It is the science used to:

1. Collect data
2. Present and organize data
3. Analyse data
4. Infer from data
5. Take a decision from data

Statistics is data-driven decision making.

---

## 2. Types of data

Classify every variable before choosing a summary.

```
Data
├── Numerical (quantitative)
│   ├── Discrete     countable, finite possibilities
│   └── Continuous   not countable, infinite possibilities
└── Categorical (qualitative)
    └── defined categories
```

| Type | Meaning | Examples |
|---|---|---|
| Discrete | Counted items | Number of children, defects per hour |
| Continuous | Measured characteristics | Weight, voltage, height |
| Categorical | Named groups | Marital status, political party, eye color |

### Variables

| Kind | Subtype | Meaning | Example |
|---|---|---|---|
| Quantitative | Discrete | Countable, finite possibilities | Number of people |
| Quantitative | Continuous | Infinite possibilities | Height |
| Qualitative | Nominal | No ordering | Hair color, eye color, religion |
| Qualitative | Ordinal | Ordering is possible | Health: poor, reasonable, good, excellent |
| Quantitative | Interval | Differences are meaningful; no true zero; ratios are not meaningful | Temperature |
| Quantitative | Ratio | Differences and ratios are meaningful; true zero exists | Length |

### Worked classification

| Question | Type |
|---|---|
| Types of vehicle owned (two wheeler, four wheeler) | Categorical, nominal |
| Product satisfaction (unsatisfied, neutral, fairly satisfied, satisfied) | Categorical, ordinal |
| Magazines currently subscribed (0, 1, 2, 3, 4) | Discrete |
| Height in inches | Continuous, ratio |
| Weight in kilograms | Continuous, ratio |
| Temperature in °C or °F | Continuous, interval |

---

## 3. Levels of measurement

From lowest to highest: **nominal → ordinal → interval → ratio**.

**Nominal.** Distinct categories, no ranking. Gender, marital status, voting for a party.

**Ordinal.** Distinct categories with ranking. Differences between ranks are not treated as equal.

- Product satisfaction: satisfied, neutral, unsatisfied
- Faculty rank: professor, associate professor, assistant professor
- Student grades: A, B, C, D, F
- Medals: gold, silver, bronze

**Interval.** Ordered scale. The difference between measurements is meaningful. There is no true zero, so “twice as much” is not meaningful.

- Temperature in Fahrenheit and Celsius
- Months of the year (there is no month zero; January is not twice June)

**Ratio.** Ordered scale. Differences are meaningful and there is a true zero, so ratios are meaningful.

- Weight, age, salary, length

Which measure you may use depends on this scale. Mean and standard deviation belong to interval and ratio data. Mode works on nominal data. Median is especially useful for ordinal data.

---

## 4. Measures of central tendency

A single number that represents the center of a data set.

The three measures: **mean, median, mode**.

### Mean (arithmetic average)

The most common measure of center. It describes what is average or typical.

Ungrouped sample mean:

```
Ȳ = (Σ Y) / n
```

Grouped data (each score multiplied by its frequency):

```
Ȳ = (Σ fY) / N
```

**Example (ungrouped).** Minutes to get ready on 10 work days:

`39, 29, 43, 52, 39, 44, 40, 31, 44, 35`

Sum = 396, so mean = 396 / 10 = **39.6 minutes**.

**Properties**

- Every score contributes, so the mean is the most stable of the three measures.
- Extreme scores pull it.
- The sum of each score’s distance from the mean is zero. The mean is the balance point.
- The mean may not be an actual score in the data.
- It is easy to compute.

**Use the mean when**

- The data are quantitative and have no extreme or outlier observations.
- The scale is interval or ratio.
- Sampling stability is wanted.
- You will also compute standard deviation, coefficient of variation, or skewness.

### Mode

The category or score with the largest frequency (or percentage). It can be calculated for nominal, ordinal, and interval-ratio data.

**Example.** Server failures per day over two weeks:

`1, 3, 0, 3, 26, 2, 7, 4, 2, 3, 3, 6, 3`

The value 3 appears five times, more than any other value, so the mode is **3**. The most common occurrence is three server failures in a day. The value 26 does not change the mode.

**Properties**

- Works for qualitative and quantitative data.
- It may not be unique (bimodal, multimodal).
- Extreme values do not change it.

**Use the mode when**

- The data are measured on a nominal scale.
- The decision should follow the most frequent occurrence.

### Median

The score that splits the ordered distribution into two equal parts: half the cases at or below it, half at or above it. It is the 50th percentile (middle quartile).

1. **Odd number of values:** the middle-ranked value.
2. **Even number of values:** the average of the two middle-ranked values.

**Example 1 (odd).** Seven annualized returns, already ranked. The median is the 4th value: **22.4**.

**Example 2 (even).** Time to office, ordered:

`29, 31, 35, 39, 39, 40, 43, 44, 44, 52`

n = 10, so the median is the average of the 5th and 6th values: (39 + 40) / 2 = **39.5**.

**Properties**

- 50% of the data lies at or below the median and 50% at or above it.
- Extreme observations do not move it.

**Use the median when**

- The scale is ordinal (it also applies more widely, and is most useful there).
- Extreme observations should not influence the summary.
- The distribution is heavily skewed.

### Which measure to pick

| Situation | Prefer |
|---|---|
| Nominal categories | Mode |
| Ordinal ranks | Median |
| Interval or ratio, no outliers, roughly symmetric | Mean |
| Heavy skew or outliers | Median |
| “What happens most often?” | Mode |

---

## 5. Shape: symmetry and skew

| Shape | Tail | Relation |
|---|---|---|
| Symmetric | Balanced | mean = median = mode |
| Positively skewed (right) | Long right tail | mean > median > mode |
| Negatively skewed (left) | Long left tail | mean < median < mode |
| Bimodal | Two peaks | two distinct modes |
| Multimodal | Several peaks | more than two distinct modes |

For moderately skewed data, an empirical relation (supported by observation, not by theory) is:

```
mode ≈ 3 × median − 2 × mean
```

Use the mean for unskewed or moderately skewed data. Prefer the median for heavily skewed data.

### Why the center is not enough

Two groups can share the same center and still be different data.

Both groups below have n = 9, sum = 45, mean = 5, median = 5, mode = 5.

| | Values |
|---|---|
| Group 1 (X1) | 2, 8, 5, 3, 7, 8, 5, 2, 5 |
| Group 2 (X2) | 1, 15, 5, 5, 6, 3, 5, 2, 3 |

Group 2 is more spread out (it contains 15). The center alone cannot tell them apart. You also need a measure of variability.

---

## 6. Measures of variability

Variability (dispersion, spread) is the distance among scores, or the distance of a score from the mean.

It is used to:

- Describe the distribution
- Show how well a measure of central tendency represents the data

The measures in this lecture: **range, variance, standard deviation, quartile deviation**.

### Range

The distance from the smallest value to the highest value.

```
Range = highest score − lowest score
```

For continuous data, real limits are used:

```
Range = upper real limit of Xmax − lower real limit of Xmin
```

**Example.** Scores `7, 2, 7, 6, 5, 6, 2`. Range = 7 − 2 = **5**.

The range uses only two scores, so it is an imprecise measure of variability.

### Why you cannot average the raw deviations

The sum of deviations from the mean is always zero, because the mean is the balance point. A “mean deviation” computed from signed deviations is always 0. That cannot measure spread.

### Variance and standard deviation

Strategy:

1. Subtract the mean from each score (deviation).
2. Square each deviation (removes the sign).
3. Add the squared deviations. This total is the **sum of squares (SS)**.
4. Average the squared deviations. That average is the **variance** (spread in squared units).
5. Take the square root. That is the **standard deviation** (typical distance from the mean, back in the original units).

The standard deviation describes whether scores cluster near the mean or are widely scattered. It is the most common measure of variability. Variance is its companion: same information, squared units.

**Population** (divide by N). Greek letters.

```
σ² = SS / N
σ  = √σ²
```

**Sample** (divide by n − 1). Roman letters.

```
s² = SS / (n − 1)
s  = √s²
```

A sample has less variability than the population it comes from. Dividing by n would give a biased (too small) estimate of the population variance. Inferential statistics uses the sample to draw conclusions about the population, so the sample formulas use **n − 1**.

**Worked comparison** (both groups have mean 5, n = 9). The lecture computes the spread as SS / 8, which is the sample denominator n − 1.

| Group | SS | Sample SD |
|---|---|---|
| X1: 2, 8, 5, 3, 7, 8, 5, 2, 5 | 44 | √(44/8) = **2.345** |
| X2: 1, 15, 5, 5, 6, 3, 5, 2, 3 | 134 | √(134/8) = **4.093** |

Same center, different spread. X2 is more variable.

**Check yourself**

- A sample of four scores has SS = 24. Sample variance = 24 / (4 − 1) = **8**. (24/4 = 6 would be the population formula.)
- A sample systematically has less variability than the population. **True.**
- The standard deviation is the distance from the mean to the farthest point. **False.** It is the typical (root-mean-square) distance from the mean.

### Descriptive pair

Mean and standard deviation together describe a distribution. With both numbers you can reconstruct the measurement scale: where the center is, and how far scores typically sit from it.

---

## 7. Five-point summary

Five numbers that sketch a data set:

1. **Minimum**
2. **Q1** — first quartile, the 25% mark
3. **Median** — second quartile, the 50% mark
4. **Q3** — third quartile, the 75% mark
5. **Maximum**

With n ordered observations, positions used in the lecture:

```
Position of Q1 = (n + 1) / 4
Position of Q3 = 3(n + 1) / 4
```

If the position falls between two values, take the value halfway between them.

**Example.** Ordered data, n = 9:

`11, 12, 13, 16, 16, 17, 17, 18, 21`

- Position of Q1 = (9 + 1) / 4 = 2.5 → halfway between 12 and 13 → **Q1 = 12.5**
- Median = 5th value → **16**
- Position of Q3 = 3(9 + 1) / 4 = 7.5 → halfway between 17 and 18 → **Q3 = 17.5**
- Five-point summary: **11, 12.5, 16, 17.5, 21**

---

## 8. Interquartile range and quartile deviation

The interquartile range is the spread of the middle 50% of the data (the mid-spread). Extreme values do not affect it.

```
IQR = Q3 − Q1
Quartile deviation QD = IQR / 2
```

From the example above: IQR = 17.5 − 12.5 = **5**, and QD = 5 / 2 = **2.5**. That 2.5 is the variation inside the central 50% of the data.

---

## 9. Box-and-whisker plot and outliers

A box plot shows Q1, the median (Q2), and Q3 as a box, with whiskers toward the minimum and maximum.

```
IQR = Q3 − Q1

Lower fence (potential outlier) = Q1 − 1.5 × IQR
Upper fence (potential outlier) = Q3 + 1.5 × IQR

Lower major-outlier fence = Q1 − 3 × IQR
Upper major-outlier fence = Q3 + 3 × IQR
```

- A point below the lower 1.5 fence or above the upper 1.5 fence is a **potential outlier**.
- A point beyond the 3 × IQR fences is a **major outlier**.

**Example.** Ordered values `11, 12, 13, 16, 16, 17, 17, 18`, with Q1 − 1.5 × IQR = 5 and Q3 + 1.5 × IQR = 25. Every point lies between 5 and 25, so this set has no outliers.

---

## 10. One-page checklist

Before a calculation, name the variable: quantitative or categorical, discrete or continuous, and nominal, ordinal, interval, or ratio.

Then compute, as appropriate:

- [ ] Mean (ungrouped and, when frequencies are given, grouped)
- [ ] Median (odd n and even n)
- [ ] Mode (including the case of more than one mode)
- [ ] Shape: symmetric, right skew, or left skew, from mean vs median vs mode
- [ ] Range
- [ ] Sum of squares, population variance and σ, sample variance and s (denominator n − 1)
- [ ] Five-point summary: min, Q1, median, Q3, max
- [ ] IQR and quartile deviation
- [ ] Fences at 1.5 × IQR and 3 × IQR, then name any outliers
- [ ] A box plot, and a short comparison when two groups are given

Remember the decision rules:

- Mean for interval/ratio data that is roughly symmetric and free of outliers.
- Median for ordinal data, heavy skew, or outliers.
- Mode for nominal data and for “most frequent” decisions.
- Sample variance divides by n − 1.

---

## 11. Practice problems from the lecture

Work these by hand. For each one, state the five-point summary, the spread, the shape, and whether any point is an outlier.

### Q1. Office noise level (dBA), n = 77

```
55.3, 55.3, 55.3, 55.9, 55.9, 55.9, 55.9, 56.1, 56.1, 56.1, 56.1, 56.1, 56.1,
56.8, 56.8, 57.0, 57.0, 57.0, 57.8, 57.8, 57.8, 57.9, 57.9, 57.9, 58.8, 58.8,
58.8, 59.8, 59.8, 59.8, 62.2, 62.2, 63.8, 63.8, 63.8, 63.9, 63.9, 63.9, 64.7,
64.7, 64.7, 65.1, 65.1, 65.1, 65.3, 65.3, 65.3, 65.3, 67.4, 67.4, 67.4, 67.4,
68.7, 68.7, 68.7, 68.7, 69.0, 70.4, 70.4, 71.2, 71.2, 71.2, 73.0, 73.0, 73.1,
73.1, 74.6, 74.6, 74.6, 74.6, 79.3, 79.3, 79.3, 79.3, 83.0, 83.0, 83.0
```

Find the arithmetic mean, standard deviation, variance, and IQR. Draw a box plot. Comment on outliers.

### Q2. Total fat (grams per serving), 20 chicken sandwiches

```
7, 8, 4, 5, 16, 20, 20, 24, 19, 30, 23, 30, 25, 19, 29, 29, 30, 30, 40, 56
```

1. Mean, median, Q1, Q3.
2. Variance, standard deviation, range, IQR. Are there outliers?
3. Are the data skewed? If so, which way?
4. What can you conclude about the total fat of these sandwiches?

### Q3. Battery life (shots), digital cameras

```
300, 180, 85, 170, 380, 460, 260, 35, 380, 120, 110, 240
```

List the five-point summary.

### Q4. Quartiles and a box plot

```
82, 45, 64, 80, 82, 74, 79, 80, 80, 78, 80, 80, 48, 73, 80, 79, 81, 70, 78, 73
```

1. Obtain and interpret the quartiles.
2. Determine and interpret the IQR.
3. Find and interpret the five-number summary.
4. Identify potential outliers.
5. Construct and interpret a box plot.

### Q5. Waiting time (minutes) at two bank branches, noon to 1 p.m.

Commercial branch (n = 15):

```
4.21, 5.55, 3.02, 5.13, 4.77, 2.34, 3.54, 3.20, 4.50, 6.10, 0.38, 5.12, 6.46, 6.19, 3.79
```

Residential branch (n = 15):

```
9.66, 5.90, 8.02, 5.79, 8.73, 3.82, 8.01, 8.35, 10.49, 6.68, 5.64, 4.08, 6.17, 9.91, 5.47
```

1. Five-number summary for each branch.
2. Box plots, and the shape of each distribution.
3. Similarities and differences in waiting time.

---

## Formula sheet

```
Mean (ungrouped)     Ȳ = ΣY / n
Mean (grouped)       Ȳ = Σ(fY) / N

Median               odd n  → middle value
                     even n → average of the two middle values
Mode                 most frequent value

Right skew           mean > median > mode
Left skew            mean < median < mode
Symmetric            mean = median = mode
Moderate skew        mode ≈ 3×median − 2×mean

Range                max − min
Population variance  σ² = SS / N          σ = √σ²
Sample variance      s² = SS / (n − 1)    s = √s²

Q1 position          (n + 1) / 4
Q3 position          3(n + 1) / 4
IQR                  Q3 − Q1
Quartile deviation   IQR / 2

Potential outlier    < Q1 − 1.5×IQR   or   > Q3 + 1.5×IQR
Major outlier        < Q1 − 3×IQR     or   > Q3 + 3×IQR

Five-point summary   min, Q1, median, Q3, max
```

# Probability — Quick Formula Cheat Sheet

A compact, exam-oriented reference for probability, conditional probability, Bayes' theorem, and Naive Bayes classification.

> **GitHub note:** Formulas use GitHub-supported `$...$` and `$$...$$` math delimiters.

## 1. Basic Probability Formulas

| Concept | Left-hand side (what we calculate) | Right-hand side (how to calculate it) |
|---|---|---|
| Basic probability | $P(A)$ | $\frac{\text{Favorable outcomes}}{\text{Total possible outcomes}}$ |
| Complement | $P(A^c)$ | $1-P(A)$ |
| Addition — mutually exclusive events | $P(A\cup B)$ | $P(A)+P(B)$ |
| Addition — overlapping events | $P(A\cup B)$ | $P(A)+P(B)-P(A\cap B)$ |
| Multiplication — independent events | $P(A\cap B)$ | $P(A)\times P(B)$ |
| Multiplication — dependent events | $P(A\cap B)$ | $P(A)\times P(B\mid A)$ |
| Conditional probability | $P(A\mid B)$ | $\frac{P(A\cap B)}{P(B)},\quad P(B)>0$ |
| Bayes' theorem | $P(A\mid B)$ | $\frac{P(B\mid A)P(A)}{P(B)},\quad P(B)>0$ |
| Total probability (two cases) | $P(B)$ | $P(B\mid A)P(A)+P(B\mid A^c)P(A^c)$ |

## 2. Naive Bayes — Machine Learning

Naive Bayes applies Bayes' theorem to classification. It assumes that features are conditionally independent given the class.

| Purpose | Left-hand side (what we calculate) | Right-hand side (how to calculate it) |
|---|---|---|
| Posterior probability | $P(C\mid X)$ | $\frac{P(X\mid C)P(C)}{P(X)}$ |
| Naive Bayes score (proportional to posterior) | $P(C\mid X)$ | $P(C)\prod_{i=1}^{n}P(x_i\mid C)$ |
| Predicted class | $\hat{C}$ | $\arg\max_C P(C)\prod_{i=1}^{n}P(x_i\mid C)$ |

### Meaning of the symbols

- $A,B$: events.
- $A^c$: event that $A$ does not occur.
- $P(A\mid B)$: probability of $A$, given that $B$ occurred.
- $C$: candidate class, such as **spam** or **not spam**.
- $X$: all observed features.
- $x_i$: the $i$-th feature.
- $P(C)$: prior probability of class $C$.
- $P(x_i\mid C)$: probability of feature $x_i$ given class $C$.
- $\prod$: multiply the feature probabilities together.
- $\arg\max_C$: choose the class with the highest score.

### Important Naive Bayes note

The Naive Bayes score omits $P(X)$ because it is the same for every candidate class. Therefore, it does not change which class has the highest posterior probability. The score is proportional to the posterior, but is not necessarily itself a probability.

For numerical stability, implementations often calculate log-scores:

$$
\log P(C)+\sum_{i=1}^{n}\log P(x_i\mid C)
$$

Choose the class with the largest log-score. For count-based models, **Laplace smoothing** can help avoid zero probabilities.

## 3. How to Choose the Rule

| Wording in a question | Rule to consider |
|---|---|
| Chance of an event | Basic probability |
| Not A | Complement |
| A or B | Addition |
| A and B | Multiplication |
| A given B | Conditional probability |
| Update a probability using evidence | Bayes' theorem |
| Predict a class from features | Naive Bayes |

## 4. Key Reminders

- **Union** $A\cup B$ corresponds to **OR**.
- **Intersection** $A\cap B$ corresponds to **AND**.
- For mutually exclusive events, $P(A\cap B)=0$.
- Independence means $P(B\mid A)=P(B)$, when the conditional probability is defined.
- Mutually exclusive events with nonzero probabilities are not independent.
- In Bayes' theorem, distinguish $P(A\mid B)$ from $P(B\mid A)$: they are generally different.

---
*Study note: Check whether events overlap, are independent, or are dependent before selecting a formula.*

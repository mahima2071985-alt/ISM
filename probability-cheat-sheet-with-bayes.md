# Probability — Quick Formula Cheat Sheet

A compact, exam-oriented reference for probability, conditional probability, Bayes' theorem, and Naive Bayes.

> GitHub renders math using `$...$` for inline formulas and `$$...$$` for display formulas.

## 1. Basic Probability Formulas

| Concept | Left-hand side (what we calculate) | Right-hand side (how to calculate it) |
|---|---|---|
| Basic probability | $P(A)$ | $\frac{\text{Favorable outcomes}}{\text{Total possible outcomes}}$ |
| Complement | $P(A^c)$ | $1-P(A)$ |
| Addition — mutually exclusive events | $P(A\cup B)$ | $P(A)+P(B)$ |
| Addition — overlapping events | $P(A\cup B)$ | $P(A)+P(B)-P(A\cap B)$ |
| Multiplication — independent events | $P(A\cap B)$ | $P(A)\times P(B)$ |
| Multiplication — dependent events | $P(A\cap B)$ | $P(A)\times P(B\mid A)$ |
| Conditional probability | $P(A\mid B)$ | $\frac{P(A\cap B)}{P(B)},\ P(B)>0$ |
| Bayes' theorem | $P(B\mid A)$ | $\frac{P(A\mid B)P(B)}{P(A)},\ P(A)>0$ |
| Total probability (two cases) | $P(A)$ | $P(A\mid B)P(B)+P(A\mid B^c)P(B^c)$ |

## 2. Bayes' Theorem — Three Useful Forms

Bayes' theorem answers: **After observing evidence, how likely is a particular explanation or class?**

### Form 1: Basic Bayes' theorem

$$
P(B\mid A)=\frac{P(A\mid B)P(B)}{P(A)}
$$

- **Prior:** $P(B)$ — probability of $B$ before seeing the evidence.
- **Likelihood:** $P(A\mid B)$ — probability of evidence $A$ if $B$ is true.
- **Evidence:** $P(A)$ — overall probability of seeing $A$.
- **Posterior:** $P(B\mid A)$ — updated probability of $B$ after seeing $A$.

**Worked example: medical test**

Suppose:
- 1% of people have a condition: $P(D)=0.01$.
- The test is positive for 90% of people who have it: $P(+\mid D)=0.90$.
- The test is positive for 5% of people who do not have it: $P(+\mid D^c)=0.05$.

First calculate the overall probability of a positive test:

$$
P(+)=P(+\mid D)P(D)+P(+\mid D^c)P(D^c)
$$

$$
=(0.90)(0.01)+(0.05)(0.99)=0.0585
$$

Then apply Bayes' theorem:

$$
P(D\mid +)=\frac{P(+\mid D)P(D)}{P(+)}
=\frac{0.90\times0.01}{0.0585}\approx0.1538
$$

**Answer:** About **15.4%** of people with a positive result have the condition, given these assumptions.

### Form 2: Bayes' theorem with total probability expanded

When evidence $A$ can occur whether $B$ is true or false:

$$
P(B\mid A)=
\frac{P(A\mid B)P(B)}
{P(A\mid B)P(B)+P(A\mid B^c)P(B^c)}
$$

This is the same theorem, with $P(A)$ expanded using the **law of total probability**.

**Medical-test example:** The denominator is the overall chance of a positive test:

$$
P(+)= (0.90)(0.01)+(0.05)(0.99)=0.0585
$$

Therefore, the answer remains $P(D\mid +)\approx15.4\%$.

### Form 3: Bayes' theorem for multiple classes

If there are several possible classes $B_1,B_2,\ldots,B_n$:

$$
P(B_j\mid A)=
\frac{P(A\mid B_j)P(B_j)}
{\sum_{i=1}^{n}P(A\mid B_i)P(B_i)}
$$

The denominator adds the probability of the evidence across **all possible classes**.

**Worked example: item made by one of two factories**

- Factory 1 makes 60% of items; 2% of its items are defective.
- Factory 2 makes 40% of items; 5% of its items are defective.
- A randomly selected item is defective. Find the probability it came from Factory 2.

Let $F_1$ and $F_2$ identify the factories, and $D$ mean “defective.”

$$
P(D)=(0.02)(0.60)+(0.05)(0.40)=0.032
$$

$$
P(F_2\mid D)=\frac{P(D\mid F_2)P(F_2)}{P(D)}
=\frac{0.05\times0.40}{0.032}=0.625
$$

**Answer:** There is a **62.5%** chance the defective item came from Factory 2.

## 3. Naive Bayes — Machine Learning

Naive Bayes uses Bayes' theorem to predict a class from features. It assumes features are conditionally independent given the class.

### Main formulas

| Purpose | Left-hand side | Right-hand side |
|---|---|---|
| Posterior probability | $P(C\mid X)$ | $\frac{P(X\mid C)P(C)}{P(X)}$ |
| Naive Bayes score | $P(C\mid X)$ | $\propto P(C)\prod_{i=1}^{n}P(x_i\mid C)$ |
| Predicted class | $\hat{C}$ | $\arg\max_C P(C)\prod_{i=1}^{n}P(x_i\mid C)$ |

- $C$: candidate class, such as spam or not spam.
- $X$: all observed features; $x_i$ is feature number $i$.
- $P(C)$: prior probability of the class.
- $P(x_i\mid C)$: probability of feature $x_i$ given class $C$.
- $\prod$: multiply the feature probabilities.
- $\arg\max_C$: choose the class with the highest score.
- $\propto$: “proportional to”; the shared denominator $P(X)$ is omitted when comparing classes.

### Worked example: spam email

Suppose an email contains the words **“prize”** and **“win.”** Use these illustrative probabilities:

- $P(Spam)=0.40$
- $P(NotSpam)=0.60$
- $P(prize\mid Spam)=0.70$
- $P(win\mid Spam)=0.80$
- $P(prize\mid NotSpam)=0.10$
- $P(win\mid NotSpam)=0.05$

Calculate each class score:

$$
Score(Spam)=0.40\times0.70\times0.80=0.224
$$

$$
Score(NotSpam)=0.60\times0.10\times0.05=0.003
$$

Normalize the scores to estimate the spam probability:

$$
P(Spam\mid prize,win)=\frac{0.224}{0.224+0.003}\approx0.9868
$$

**Answer:** The model estimates about **98.7% probability of spam**, based on the illustrative probabilities and the Naive Bayes assumption.

For numerical stability, implementations may use log-scores:

$$
\log P(C)+\sum_{i=1}^{n}\log P(x_i\mid C)
$$

Choose the class with the highest log-score. Laplace smoothing can help prevent zero probabilities in count-based models.

## 4. How to Choose the Rule

| Wording in a question | Rule to consider |
|---|---|
| Chance of an event | Basic probability |
| Not A | Complement |
| A or B | Addition |
| A and B | Multiplication |
| A given B | Conditional probability |
| Update probability using evidence | Bayes' theorem |
| Predict a class from features | Naive Bayes |

## 5. Key Reminders

- **Union** $A\cup B$ corresponds to **OR**.
- **Intersection** $A\cap B$ corresponds to **AND**.
- For mutually exclusive events, $P(A\cap B)=0$.
- Independence means $P(B\mid A)=P(B)$, when defined.
- Mutually exclusive events with nonzero probabilities are not independent.
- $P(A\mid B)$ and $P(B\mid A)$ are generally different.

---
*Study note: Check whether events overlap, are independent, or are dependent before choosing a formula.*

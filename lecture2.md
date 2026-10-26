# Lecture 2 — Probability Basics

Session 2 topics: axioms of probability, probability basics, mutually exclusive events, and independent events.

## 1. Random experiment

A random experiment is any action whose outcome is not known in advance.

Examples from the lecture:

- Flip a coin. Does it land heads or tails?
- Wait at a bus stop. How long until the bus arrives?
- Give a lecture. How many students are listening?
- Send one of several waveforms over a channel. Which waveform arrives? Which one does the receiver decide was sent?
- Count how often a word appears in a text.
- Pull a card from a deck.
- Watch three phone calls and mark each as voice (v) or data (d).

## 2. Sample space

The sample space \(S\) is the set of all possible outcomes of the experiment.

| Experiment | Sample space |
|---|---|
| Throw one die | \(S = \{1, 2, 3, 4, 5, 6\}\) |
| Test a circuit: accepted (a) or rejected (r) | \(S = \{a, r\}\) |

Equally likely outcomes are outcomes that have the same probability. A fair die gives six equally likely outcomes.

## 3. Event

An event is a subset of the sample space. That includes the empty set and the whole sample space.

Each time the experiment runs, event \(A\) either occurs (the outcome is in \(A\)) or does not occur (the outcome is not in \(A\)).

**Example.** Die, \(S = \{1, 2, 3, 4, 5, 6\}\). “Even” is the event \(A = \{2, 4, 6\}\).

## 4. Complement, union, and intersection

**Complement \(A^c\).** Every outcome in \(S\) that is not in \(A\).

\[
P(A) = 1 - P(A^c)
\]

**Union \(A \cup B\).** Outcomes in \(A\), or in \(B\), or in both.

**Intersection \(A \cap B\).** Outcomes that are in both \(A\) and \(B\). On a Venn diagram this is the overlap.

## 5. Mutually exclusive events

Two events are mutually exclusive when they share no outcomes. If one occurs, the other cannot.

\[
P(A \cap B) = 0
\]

A coin landing heads or tails is mutually exclusive: both cannot happen on the same flip. On a Venn diagram the two regions do not overlap.

If mutually exclusive events \(A\) and \(B\) together make up the whole sample space (\(A \cup B = S\)), then

\[
P(A) + P(B) = 1
\]

## 6. Three ways to define probability

### Classical

When the outcomes are equally likely,

\[
\text{Probability of an event} = \frac{\text{number of favorable outcomes}}{\text{total number of possible outcomes}}
\]

Two dice have \(6 \times 6 = 36\) equally likely outcomes, so each pair has probability \(1/36\).

### Empirical (relative frequency)

The probability is the fraction of times a similar event happened in past trials.

\[
\text{Empirical probability} = \frac{\text{number of times the event occurs}}{\text{total number of observations}}
\]

This rests on the **law of large numbers**: over a large number of trials, the empirical probability approaches the true probability. More observations give a more accurate estimate.

### Axiomatic

Probability is a number assigned to each event so that these three properties hold. If \(S\) is the sample space and \(E\) is any event:

1. \(P(S) = 1\)
2. \(0 \leq P(E) \leq 1\)
3. If \(E_1 \cap E_2 = \emptyset\), then \(P(E_1 \cup E_2) = P(E_1) + P(E_2)\)

A proposed assignment is permissible only when every probability is between 0 and 1 and, for mutually exclusive outcomes that fill \(S\), the probabilities sum to 1.

## 7. Probability as a measure of likelihood

Probability runs from 0 to 1. Likelihood increases as the number increases.

| Value | Meaning |
|---|---|
| 0 | The event does not occur |
| 0.5 | The event is just as likely as it is unlikely |
| 1 | The event occurs |

## 8. The addition rule

The probability that \(A\) or \(B\) occurs (or both):

\[
P(A \cup B) = P(A) + P(B) - P(A \cap B)
\]

The overlap is subtracted once because it was counted in both \(P(A)\) and \(P(B)\).

If \(A\) and \(B\) are mutually exclusive, \(P(A \cap B) = 0\), so

\[
P(A \cup B) = P(A) + P(B)
\]

Rearrangement used often in the examples:

\[
P(A \cap B) = P(A) + P(B) - P(A \cup B)
\]

## 9. Independent and dependent events

| Kind | Meaning |
|---|---|
| Independent | One event occurring does not change the probability of the other |
| Dependent | One event occurring gives information about the other |

Repeated coin flips are independent: a head on the first flip does not change the second flip.

The test for independence:

\[
P(A \cap B) = P(A)\,P(B)
\]

If that equality fails, the events are dependent.

Independent events do not have to be mutually exclusive. They can happen together. If both probabilities are positive and the events are mutually exclusive, they cannot be independent: the intersection would have to be both 0 and \(P(A)P(B) > 0\).

### Side by side

| | Mutually exclusive | Independent |
|---|---|---|
| Meaning | Cannot happen together | One does not affect the other |
| Intersection | \(P(A \cap B) = 0\) | \(P(A \cap B) = P(A)P(B)\) |
| Venn diagram | The regions do not overlap | The regions may overlap |

## 10. Counting a committee

When each group of the same size is equally likely, use combinations. The number of ways to choose \(k\) items from \(n\) is

\[
\binom{n}{k} = \frac{n!}{k!(n-k)!}
\]

\[
P(\text{a particular kind of group}) = \frac{\text{number of favorable groups}}{\text{number of possible groups}}
\]

---

## 11. Worked examples

### Example 1. Is this assignment permissible?

Four mutually exclusive outcomes \(A, B, C, D\) fill the experiment. Each probability must lie in \([0, 1]\), and the four must sum to 1.

| | Assignment | Sum | Verdict |
|---|---|---|---|
| (a) | 0.38, 0.16, 0.11, 0.35 | 1.00 | Permissible |
| (b) | 0.31, 0.27, 0.28, 0.16 | 1.02 | Not permissible |
| (c) | 0.32, 0.27, −0.06, 0.47 | — | Not permissible (a probability is negative) |
| (d) | 1/2, 1/4, 1/8, 1/16 | 15/16 | Not permissible |
| (e) | 5/8, 1/6, 1/3, 2/9 | 97/72 > 1 | Not permissible |

### Example 2. Sum of two dice

There are 36 equally likely outcomes. Let \(X\) be the sum.

| Sum | Outcomes | Probability |
|---|---|---|
| 2 | (1,1) | 1/36 |
| 3 | (1,2), (2,1) | 2/36 |
| 4 | (1,3), (2,2), (3,1) | 3/36 |
| 5 | (1,4), (2,3), (3,2), (4,1) | 4/36 |
| 6 | (1,5), (2,4), (3,3), (4,2), (5,1) | 5/36 |
| 7 | (1,6), (2,5), (3,4), (4,3), (5,2), (6,1) | 6/36 |
| 8 | (2,6), (3,5), (4,4), (5,3), (6,2) | 5/36 |
| 9 | (3,6), (4,5), (5,4), (6,3) | 4/36 |
| 10 | (4,6), (5,5), (6,4) | 3/36 |
| 11 | (5,6), (6,5) | 2/36 |
| 12 | (6,6) | 1/36 |

(a) Greater than 8 means 9, 10, 11, or 12:

\[
\frac{4+3+2+1}{36} = \frac{10}{36} = \frac{5}{18}
\]

(b) Less than 6 means 2, 3, 4, or 5:

\[
\frac{1+2+3+4}{36} = \frac{10}{36} = \frac{5}{18}
\]

(c) Neither 7 nor 11:

\[
1 - \frac{6}{36} - \frac{2}{36} = \frac{28}{36} = \frac{7}{9}
\]

### Example 3. Pass both exams

\(P(S) = 2/3\) passes statistics. The probability of not passing mathematics is \(5/9\), so \(P(M) = 1 - 5/9 = 4/9\). The probability of passing at least one is \(P(S \cup M) = 4/5\).

\[
P(S \cap M) = \frac{2}{3} + \frac{4}{9} - \frac{4}{5} = \frac{30}{45} + \frac{20}{45} - \frac{36}{45} = \frac{14}{45}
\]

### Example 4. Investors in both

\(P(A) = 0.75\) invest in traditional annuities, \(P(B) = 0.45\) invest in the stock market, and \(P(A \cup B) = 0.85\).

\[
P(A \cap B) = 0.75 + 0.45 - 0.85 = 0.35
\]

So 35% invest in both.

### Example 5. Cable length

Specifications are \(2000 \pm 10\) mm, so a cable meets spec when its length \(X\) satisfies \(1990 \leq X \leq 2010\). A cable that is too small is as likely as a cable that is too large. \(P(\text{meets spec}) = 0.99\).

Let \(M\) be “meets specifications,” \(S\) be “too small” (\(X < 1990\)), and \(L\) be “too large” (\(X > 2010\)).

(a) The two defective cases split the remaining probability equally:

\[
P(S) = P(L) = \frac{1 - 0.99}{2} = 0.005
\]

A randomly selected cable is too large with probability **0.005**.

(b) Larger than 1990 mm means it meets spec or it is too large:

\[
P(X \geq 1990) = P(M) + P(L) = 0.99 + 0.005 = 0.995
\]

The same result from the complement:

\[
P(X \geq 1990) = 1 - P(S) = 1 - 0.005 = 0.995
\]

### Example 6. Maximum of a product

\(A\) and \(B\) are mutually exclusive and \(A \cup B = S\), so \(P(A) + P(B) = 1\).

When two numbers have a fixed sum, their product is largest when the numbers are equal. So \(P(A) = P(B) = 1/2\), and

\[
P(A)\,P(B) = \frac{1}{4}
\]

### Example 7. Are these dice events independent?

\[
\begin{align*}
A &= \{(1,2), (2,1), (2,2)\} \\
B &= \{(2,2), (2,3), (2,4), (2,5), (2,6), (3,2), (4,2), (5,2), (6,2)\}
\end{align*}
\]

\[
P(A) = \frac{3}{36},\quad P(B) = \frac{9}{36},\quad P(A \cap B) = P\{(2,2)\} = \frac{1}{36}
\]

\[
P(A)P(B) = \frac{3}{36} \times \frac{9}{36} = \frac{27}{1296} = \frac{1}{48} \neq \frac{1}{36}
\]

So \(A\) and \(B\) are dependent.

### Example 8. Majority of women on a committee

Choose 5 people from 8 men and 4 women (12 people). A majority of women in a group of 5 means at least 3 women: 1 man and 4 women, or 2 men and 3 women.

\[
\binom{12}{5} = 792
\]

\[
P(1\text{ man and }4\text{ women}) = \frac{\binom{8}{1}\binom{4}{4}}{\binom{12}{5}} = \frac{8}{792}
\]

\[
P(2\text{ men and }3\text{ women}) = \frac{\binom{8}{2}\binom{4}{3}}{\binom{12}{5}} = \frac{112}{792}
\]

\[
P(\text{majority women}) = \frac{8}{792} + \frac{112}{792} = \frac{120}{792} = \frac{5}{33}
\]

---

## 12. Checklist

- [ ] Name the sample space before naming an event
- [ ] Complement: \(P(A^c) = 1 - P(A)\)
- [ ] Union: add the two probabilities, then subtract the overlap
- [ ] Mutually exclusive: intersection is 0, so the subtraction term drops out
- [ ] Independent: intersection equals the product; otherwise the events are dependent
- [ ] A legal assignment has each probability in \([0, 1]\), and exhaustive mutually exclusive outcomes sum to 1
- [ ] Equally likely outcomes: count favorable outcomes and divide by the total
- [ ] Classical probability needs equally likely outcomes; empirical probability needs many trials

---

## 13. Practice problems

### Q1. Bank accounts

A survey finds that 40% of accounts are savings, 35% are current, and the rest are loan accounts.

1. Probability an account is a loan account. **0.25**
2. Probability it is not a savings account. **0.60**
3. Probability it is not a current account. **0.65**
4. Probability it is a current account or a loan account. **0.60**

### Q2. Do A and B contradict each other?

A speaks the truth in 80% of cases and B in 60%. They state the same fact. In what percentage of cases do they contradict each other?

They contradict when one tells the truth and the other does not:

\[
P = (0.80)(0.40) + (0.20)(0.60) = 0.32 + 0.12 = 0.44
\]

So they contradict in **44%** of cases.

### Q3. Internet and television

In a suburb, 60% of households get internet from the cable company, 80% get television, and 50% get both.

1. At least one of the two services: \(P(I \cup T) = 0.60 + 0.80 - 0.50 = 0.90\)
2. Exactly one service: internet only is \(0.60 - 0.50 = 0.10\), television only is \(0.80 - 0.50 = 0.30\), so **0.40**

### Q4. Two motors for a capsule

Ten motors have been made, and 2 will not operate satisfactorily. Two motors are chosen at random. Find the probability that

1. both motors operate satisfactorily
2. one operates satisfactorily and the other does not

### Q5. Coffee and soda

55% of adults regularly drink coffee, 45% regularly drink carbonated soda, and 70% regularly consume at least one of the two.

1. Probability an adult regularly consumes both.
2. Probability an adult does not regularly consume at least one of the two (consumes neither).

### Q6. Mathematics or chemistry

A student is picked from 80 students. 30 take mathematics, 20 take chemistry, and 10 take both. Find the probability that the student takes mathematics or chemistry.

### Q7. Find the three probabilities

\(P(A \cup B) = 7/8\), \(P(A \cap B) = 1/4\), and \(P(A') = 5/8\). Find \(P(A)\), \(P(B)\), and \(P(A \cap B')\).

### Q8. Equal probabilities

\(P(A) = P(B)\) and \(P(A^c \cap B^c) = P(A \cap B) = 1/6\). Find

1. \(P(A)\)
2. \(P(A^c \cup B^c)\)
3. the probability that exactly one of \(A\) or \(B\) occurs

### Q9. Insurance deductibles

Homeowner policies have four deductible levels: none (N), low (L), medium (M), and high (H). Auto policies have three: low, medium, and high. The table gives the proportion of people who hold both policies. The slide’s example is that low homeowner and low auto is 0.06, the row-L and column-L cell. Columns are N, L, M, H and rows are L, M, H. None exists only for the homeowner policy, so read columns as homeowner and rows as auto.

| Auto \ Homeowner | N | L | M | H |
|---|---|---|---|---|
| L | 0.04 | 0.06 | 0.05 | 0.03 |
| M | 0.07 | 0.10 | 0.20 | 0.10 |
| H | 0.02 | 0.03 | 0.15 | 0.10 |

An individual with both policies is selected at random.

1. Medium auto deductible and high homeowner deductible.
2. Low auto deductible. Low homeowner deductible.
3. The same category for both.
4. Different categories for the two policies.
5. At least one deductible level is low.
6. Neither deductible level is low.

---

## Formula sheet

```
Classical            favorable outcomes / total equally likely outcomes
Empirical            times the event occurs / number of observations

Axioms               P(S) = 1
                     0 ≤ P(E) ≤ 1
                     if E1 ∩ E2 = ∅, then P(E1 ∪ E2) = P(E1) + P(E2)

Complement           P(A) = 1 − P(Aᶜ)
Addition             P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
Mutually exclusive   P(A ∩ B) = 0, so P(A ∪ B) = P(A) + P(B)
Independent          P(A ∩ B) = P(A) P(B)

Intersection         P(A ∩ B) = P(A) + P(B) − P(A ∪ B)
Exactly one          P(A) + P(B) − 2 P(A ∩ B)

Combinations         C(n, k) = n! / (k! (n − k)!)
```

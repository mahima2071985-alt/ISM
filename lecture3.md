# Lecture 3 — Conditional Probability and Total Probability

Session 3 topics: conditional probability, independent events, and the law of total probability.

New information can change a probability. A probability is assigned from what is known at the time. If you later learn that an event has occurred, some of those probabilities are revised.

**Example.** Let \(B\) be “a person has a particular disease.” A negative blood test is new information. The probability of the disease should fall, but not usually to zero, because the test is not perfect.

## 1. Conditional probability

\(P(B \mid A)\) is the probability of \(B\) given that \(A\) has occurred. Read the bar as “given,” not as division. \(A\) is the conditioning event. This is defined only when \(P(A) \neq 0\).

\[
P(B \mid A) = \frac{P(A \cap B)}{P(A)}
\]

\[
P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) \neq 0
\]

The same identities rearranged are the multiplication rule:

\[
P(A \cap B) = P(A)\,P(B \mid A) = P(B)\,P(A \mid B)
\]

For three events,

\[
P(A \cap B \cap C) = P(A)\,P(B \mid A)\,P(C \mid A \cap B)
\]

If you know the conditional probability and the probability of the condition, multiply to get the joint probability. If you know the joint and the condition, divide to get the conditional probability.

When \(B\) is contained in \(A\) (\(B \subseteq A\)), every outcome in \(B\) is already in \(A\), so \(A \cap B = B\) and \(P(A \cap B) = P(B)\).

## 2. Independent events

\(A\) and \(B\) are statistically independent when one does not change the probability of the other:

\[
P(A \mid B) = P(A), \qquad P(B \mid A) = P(B)
\]

Substitute into the definition and the test becomes

\[
P(A \cap B) = P(A)\,P(B)
\]

If the equality fails, the events are dependent. Draws **with replacement** (or from separate bags) are independent. Draws **without replacement** are dependent, because the first draw changes what remains.

## 3. Law of total probability

Let \(A_1, A_2, \ldots, A_k\) be mutually exclusive and exhaustive: they do not overlap, and their union is the whole sample space \(S\).

\[
S = A_1 \cup A_2 \cup \cdots \cup A_k, \qquad A_i \cap A_j = \emptyset \text{ for } i \neq j
\]

For any event \(B\),

\[
P(B) = \sum_{i=1}^{k} P(B \mid A_i)\,P(A_i)
\]

On a tree, the first branches are the \(A_i\), with probabilities \(P(A_i)\). The next branches are \(B\) given each \(A_i\). Each path ends at \(B \cap A_i\), and the path probability is the product \(P(A_i)\,P(B \mid A_i)\). Add the paths.

**Why it works.** \(B = B \cap S\), and \(S\) is the union of the \(A_i\), so

\[
B = (B \cap A_1) \cup (B \cap A_2) \cup \cdots \cup (B \cap A_k)
\]

Those pieces do not overlap, so

\[
P(B) = \sum_{i=1}^{k} P(B \cap A_i)
\]

The multiplication rule replaces each joint probability: \(P(B \cap A_i) = P(A_i)\,P(B \mid A_i)\).

Once \(P(B)\) is known, a conditional probability the other way is

\[
P(A_i \mid B) = \frac{P(B \mid A_i)\,P(A_i)}{P(B)}
\]

The numerator is one path. The denominator is the sum of all the paths.

## 4. Counting formulas used with these probabilities

\[
\binom{N}{n} = \frac{N!}{n!\,(N-n)!}
\]

\[
P^{N}_{n} = \frac{N!}{(N-n)!}
\]

\[
P(A) = 1 - P(A^c)
\]

\[
P(A \cup B) = P(A) + P(B) - P(A \cap B)
\]

---

## 5. Worked examples

### Example 1. Loan default by age

|  | Young | Middle-aged | Senior | Total |
|---|---:|---:|---:|---:|
| No default | 10503 | 27368 | 259 | 38130 |
| Default | 3586 | 4851 | 120 | 8557 |
| Total | 14089 | 32219 | 379 | 46687 |

Let \(A\) be “does not default” and \(B\) be “middle-aged.” The lecture rounds the proportions:

\[
P(A) = \frac{38130}{46687} \approx 0.82, \quad
P(B) = \frac{32219}{46687} \approx 0.69, \quad
P(A \cap B) = \frac{27368}{46687} \approx 0.59
\]

(a) No default given middle-aged:

\[
P(A \mid B) = \frac{0.59}{0.69} \approx 0.85
\]

(b) Middle-aged given no default:

\[
P(B \mid A) = \frac{0.59}{0.82} \approx 0.72
\]

The exact ratios from the counts are \(27368/32219 \approx 0.849\) and \(27368/38130 \approx 0.718\).

### Example 2. A compact disc player is an audio component

\(A\) is “the next repair is an audio component,” \(P(A) = 0.6\). \(B\) is “it is a compact disc player,” \(P(B) = 0.05\). A compact disc player is an audio component, so \(B \subseteq A\) and \(A \cap B = B\).

\[
P(B \mid A) = \frac{P(B)}{P(A)} = \frac{0.05}{0.6} = 0.0833
\]

### Example 3. Visa and MasterCard

\(P(A) = 0.5\) has a Visa card, \(P(B) = 0.5\) has a MasterCard, and \(P(A \cap B) = 0.25\).

(a) MasterCard given Visa:

\[
P(B \mid A) = \frac{0.25}{0.5} = 0.5
\]

(b) No MasterCard given Visa. Visa but not MasterCard has probability \(P(A) - P(A \cap B)\):

\[
P(B^c \mid A) = \frac{0.5 - 0.25}{0.5} = 0.5
\]

(c) No Visa given MasterCard:

\[
P(A^c \mid B) = \frac{0.5 - 0.25}{0.5} = 0.5
\]

(d) Visa given at least one card. At least one card is \(A \cup B\), and \(A \cap (A \cup B) = A\):

\[
P(A \cup B) = 0.5 + 0.5 - 0.25 = 0.75
\]

\[
P(A \mid A \cup B) = \frac{0.5}{0.75} \approx 0.67
\]

### Example 4. One card from each bag

Bag 1 has 5 cards: I, L, J, A, U. Bag 2 has 6 cards: L, R, H, E, C, A. One card is drawn from each bag, so the draws are independent.

(a) J and R:

\[
\frac{1}{5} \times \frac{1}{6} = \frac{1}{30}
\]

(b) Both letters are L:

\[
\frac{1}{5} \times \frac{1}{6} = \frac{1}{30}
\]

(c) Both letters are vowels. Bag 1 vowels are I, A, U (3 of 5). Bag 2 vowels are E, A (2 of 6):

\[
\frac{3}{5} \times \frac{2}{6} = \frac{1}{5}
\]

The solution slide writes \(2/5 \times 2/6 = 2/15\). Bag 1 has three vowels, I, A, and U, so the product is \(1/5\).

### Example 5. Three adults drawn with replacement

Of 300 adults, 272 are right-handed, so 28 are left-handed. Selection is with replacement, so the draws are independent.

\[
P(\text{one right-handed}) = \frac{272}{300} = 0.907, \qquad
P(\text{one left-handed}) = \frac{28}{300} = 0.093
\]

(a) All three right-handed:

\[
\left(\frac{272}{300}\right)^3 = 0.745
\]

(b) All three left-handed:

\[
\left(\frac{28}{300}\right)^3 = 0.0008
\]

(c) At least one right-handed is the complement of all three left-handed:

\[
1 - 0.0008 = 0.9992
\]

### Example 6. Two independent email features

\(P(A) = 0.6\) the email contains “offer.” \(P(B) = 0.4\) it contains a suspicious link. The features are independent.

(a) Both:

\[
P(A \cap B) = (0.6)(0.4) = 0.24
\]

(b) At least one:

\[
P(A \cup B) = 0.6 + 0.4 - 0.24 = 0.76
\]

(c) Neither:

\[
P((A \cup B)^c) = 1 - 0.76 = 0.24
\]

### Example 7. Does the next customer fill the tank?

At a gas station, 40% use regular (\(A_1\)), 35% use plus (\(A_2\)), and 25% use premium (\(A_3\)). The probability of filling the tank (\(B\)) is 0.30 for regular, 0.60 for plus, and 0.50 for premium.

\[
\begin{align*}
P(B) &= (0.40)(0.30) + (0.35)(0.60) + (0.25)(0.50) \\
&= 0.12 + 0.21 + 0.125 \\
&= 0.455
\end{align*}
\]

### Example 8. Binary channel

A 1 is transmitted 40% of the time, so a 0 is transmitted 60% of the time. A transmitted 0 is received correctly with probability 0.90, and a transmitted 1 is received correctly with probability 0.95.

Let \(A\) be “1 transmitted,” so \(P(A) = 0.4\) and \(P(A^c) = 0.6\). Let \(B\) be “1 received.”

\[
P(B \mid A) = 0.95, \quad P(B^c \mid A) = 0.05, \quad
P(B^c \mid A^c) = 0.90, \quad P(B \mid A^c) = 0.10
\]

(a) Probability a 1 is received, by total probability:

\[
P(B) = (0.95)(0.4) + (0.10)(0.6) = 0.38 + 0.06 = 0.44
\]

(b) Probability a 1 was transmitted, given that a 1 was received:

\[
P(A \mid B) = \frac{P(B \mid A)\,P(A)}{P(B)} = \frac{0.95 \times 0.4}{0.44} = 0.863
\]

### Example 9. Click on an advertisement

| Device | \(P(\text{device})\) | \(P(\text{click} \mid \text{device})\) |
|---|---:|---:|
| Desktop | 0.5 | 0.04 |
| Tablet | 0.2 | 0.06 |
| Mobile | 0.3 | 0.10 |

\[
P(\text{click}) = (0.04)(0.5) + (0.06)(0.2) + (0.10)(0.3) = 0.020 + 0.012 + 0.030 = 0.062
\]

### Example 10. Poisonous plant in a park

| Forest | Share of land | Poisonous plants |
|---|---:|---:|
| A | 0.50 | 0.20 |
| B | 0.30 | 0.40 |
| C | 0.20 | 0.70 |

\[
P(\text{poisonous}) = (0.20)(0.50) + (0.40)(0.30) + (0.70)(0.20) = 0.10 + 0.12 + 0.14 = 0.36
\]

### Example 11. Mining job finished on time

\(A\) is “finished on time.” \(B\) is “it rains,” with \(P(B) = 0.45\), so \(P(B^c) = 0.55\).

\[
P(A \mid B) = 0.42, \qquad P(A \mid B^c) = 0.90
\]

Rain and no rain partition the sample space:

\[
P(A) = (0.45)(0.42) + (0.55)(0.90) = 0.189 + 0.495 = 0.684
\]

---

## 6. Checklist

- [ ] \(P(B \mid A)\) is “\(B\) given \(A\).” The condition goes in the denominator.
- [ ] Multiplication builds a joint probability. Division recovers a conditional probability.
- [ ] If \(B \subseteq A\), then \(A \cap B = B\).
- [ ] Independence means \(P(A \cap B) = P(A)P(B)\). With replacement keeps the probability the same. Without replacement changes it.
- [ ] “At least one” is often \(1\) minus “none.”
- [ ] Total probability: partition first, then weight each conditional probability by \(P(A_i)\), then add.
- [ ] To reverse the condition, divide that one path by the total probability.

---

## 7. Practice problems

### Marbles, bulbs, and flights

1. A jar has 5 red, 6 blue, and 2 white marbles. Two marbles are selected. Find the probability that both are red (a) with replacement and (b) without replacement.
2. A batch of 6400 light bulbs has 80 defectives. Twelve bulbs are selected without replacement. Find the probability that all 12 are good.
3. Of 100 flights, 20 departed late. 45 departed from airport A, and 9 of those were late. 55 departed from airport B, and 11 of those were late. Are “departed from A” and “departed late” independent?
4. \(P(A) = 1/3\), \(P(B) = 1/2\), and \(P(A \cap B) = 1/4\). Find \(P(A \mid B)\), \(P(B \mid A)\), \(P(A^c \mid B)\), \(P(B^c \mid A)\), and \(P(A \mid B^c)\).
5. Three students have probabilities \(1/4\), \(1/2\), and \(1/3\) of passing, independently. Find the probability that (i) all pass, (ii) at least one passes, (iii) at least two pass.

### From the lecture, with the printed answers

**Secretaries.** Four secretaries handle 20%, 60%, 15%, and 5% of the files. Their probabilities of misfiling are 0.05, 0.1, 0.1, and 0.05. The probability that a misfiled report is blamed on the first secretary is **0.1143**.

**Class attendance.** A class is 70% boys and 30% girls. 5% of boys and 3% of girls are irregular. The probability that a randomly selected student is irregular is **0.044**. The joint probability that the student is a girl and irregular is \(0.30 \times 0.03 = 0.009\), which is the figure printed on the slide. The probability that an irregular student is a girl is the conditional probability \(0.009 / 0.044\).

**Machines.** Machines A, B, and C produce 60%, 30%, and 10% of the items. Defective rates are 2%, 3%, and 4%.

1. Probability the item is not defective and was produced by C: **0.096**
2. Probability the item was produced by C or B: **0.4**

**Incomplete deck.** The ace of diamonds is missing, so 51 cards remain.

1. Probability the card is a club: **13/51**
2. Probability the card is a queen: **4/51**
3. Are “club” and “queen” independent? **No**

**Tools.** Company A produces 30% of the tools. Companies B and C produce the remaining 70%. Non-defective rates are 98% at A, 95% at B, and 97% at C. The slide asks what percent B and C should produce so that a tool picked at random is non-defective with probability 96%, and prints **0.164**.

**Shopping.** 500 respondents:

| Enjoys shopping for clothing | Male | Female | Total |
|---|---:|---:|---:|
| Yes | 136 | 224 | 360 |
| No | 104 | 36 | 140 |
| Total | 240 | 260 | 500 |

1. Given the person is female, the probability she does not enjoy shopping is \(36/260 = 0.1385\). The slide prints **0.1384**.
2. Given the person enjoys shopping, the probability the person is male is \(136/360 = 0.378\). The slide prints **0.56**.

**Two cards.** A standard 52-card deck. The first two cards are dealt.

1. Both queens, without replacement: **0.0045**
2. First card a 10, and the second a 5 or a 6: **0.012**
3. Both queens, with replacement: **0.0059**

---

## Formula sheet

```
Conditional          P(B|A) = P(A ∩ B) / P(A)          P(A) ≠ 0
                     P(A|B) = P(A ∩ B) / P(B)          P(B) ≠ 0

Multiplication       P(A ∩ B) = P(A) P(B|A) = P(B) P(A|B)
Three events         P(A ∩ B ∩ C) = P(A) P(B|A) P(C|A ∩ B)

Independent          P(A|B) = P(A)  and  P(A ∩ B) = P(A) P(B)
Contained            if B ⊆ A, then A ∩ B = B

Total probability    P(B) = Σ P(B|Ai) P(Ai)
                     Ai mutually exclusive and exhaustive

Reverse the condition
                     P(Ai|B) = P(B|Ai) P(Ai) / P(B)

Complement           P(A) = 1 − P(Aᶜ)
Addition             P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
Combinations         C(N, n) = N! / (n! (N − n)!)
Permutations         P(N, n) = N! / (N − n)!
```

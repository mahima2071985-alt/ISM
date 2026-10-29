Here is your Probability Formula Cheat Sheet, including the left-hand side (what we calculate), the right-hand side (how we calculate it), and Naive Bayes for machine learning exams.

## Probability — Quick Formula Cheat Sheet

| Concept                       | Left-hand side (what we want) | Right-hand side (how to calculate)                                      |
| ----------------------------- | ----------------------------- | ----------------------------------------------------------------------- |
| Basic probability             | \\(P(A)\\)                    | \\(\dfrac{\text{Favorable outcomes}}{\text{Total possible outcomes}}\\) |
| Complement                    | \\(P(A^c)\\)                  | \\(1-P(A)\\)                                                            |
| Addition — mutually exclusive | \\(P(A\cup B)\\)              | \\(P(A)+P(B)\\)                                                         |
| Addition — overlapping events | \\(P(A\cup B)\\)              | \\(P(A)+P(B)-P(A\cap B)\\)                                              |
| Multiplication — independent  | \\(P(A\cap B)\\)              | \\(P(A)\times P(B)\\)                                                   |
| Multiplication — dependent    | \\(P(A\cap B)\\)              | \\(P(A)\times P(B\mid A)\\)                                             |
| Conditional probability       | \\(P(A\mid B)\\)              | \\(\dfrac{P(A\cap B)}{P(B)}\\)                                          |
| Bayes' Theorem                | \\(P(A\mid B)\\)              | \\(\dfrac{P(B\mid A)P(A)}{P(B)}\\)                                      |
| Total probability             | \\(P(B)\\)                    | \\(P(B\mid A)P(A)+P(B\mid A^c)P(A^c)\\)                                 |

## Naive Bayes — Machine Learning

Naive Bayes uses Bayes' Theorem and assumes that features are conditionally independent given the class.

| Purpose                    | Formula                                                                |
| -------------------------- | ---------------------------------------------------------------------- |
| Posterior probability      | \\(\displaystyle P(C\mid X)=\frac{P(X\mid C)P(C)}{P(X)}\\)             |
| Naive Bayes classification | \\(\displaystyle P(C\mid X)\propto P(C)\prod\_{i=1}^{n}P(x_i\mid C)\\) |
| Predicted class            | \\(\displaystyle \hat C=\arg\max_C P(C)\prod\_{i=1}^{n}P(x_i\mid C)\\) |

Here:

- \\(C\\) = class we want to predict, such as spam or not spam.
- \\(X\\) = all observed features.
- \\(x_i\\) = an individual feature.
- \\(P(C)\\) = prior probability of the class.
- \\(P(x_i\mid C)\\) = probability of a feature given the class.
- \\(\prod\\) = multiply the feature probabilities.
- \\(\arg\max\\) = choose the class with the highest score.

Important: The Naive Bayes classification formula omits \\(P(X)\\) because it is the same for every candidate class, so it does not affect which class has the highest probability.

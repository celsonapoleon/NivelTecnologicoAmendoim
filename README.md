# Fuzzy Inference System for Technological Level Assessment in Peanut Production

[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![MatLab](https://img.shields.io/badge/Tech-MatLab-blue)
![Fuzzy Logic](https://img.shields.io/badge/Concept-Fuzzy_Logic-brightgreen)

## Overview

This repository contains a **Fuzzy Inference System (FIS)** application developed in **MatLab**. The main objective of this tool is to identify a **Technological Level Index (TLI)** adopted by rural producers in peanut production. By analyzing data from different aspects of production, the system uses fuzzy logic to provide a comprehensive assessment of the technological level implemented.

## Context and Motivation

The development of this FIS arose from a scientific research project dedicated to identifying the indicators and the technological level index of peanut producers located in the interior of the **State of São Paulo**, the main peanut producing and exporting region in Brazil. The research involved data collection through questionnaires applied to **25 producers** in the region of Tupã and surrounding areas.

The structured questionnaire contained **62 questions**, organized into **eight thematic groups**: Demographics; Soil and Climate; Planting; Inputs; Machinery; Equipment; Harvesting and Storage; and Management and Marketing. From these, **five groups** were selected as the basis for defining the technological indicators and estimating the innovation indices:

* **Self-Propelled Sprayer** (Machinery)
* **Equipment**
* **Inputs**
* **Storage** (Harvesting and Storage)
* **Management** (Management and Marketing)

The research also involved statistical analyses, including **simple linear regression** and **Ordinary Least Squares (OLS) estimation**, according to the following formulas:

$\qquad i. \quad y_i = \beta_0 + \beta_1 x_i + \epsilon_i$

$\qquad ii. \quad \hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x$

$\qquad iii. \quad \hat{\beta}_1 = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n}(x_i - \bar{x})^2} \quad or \quad \hat{\beta}_1 = \frac{Cov(x,y)}{Var(x)}$

$\qquad iv. \quad let \quad S_{xx} = \sum_{i=1}^{n}(x_i - \bar{x})^2$

$\qquad v. \quad \hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$

$\qquad vi. \quad SSR = \sum_{i=1}^{n}(\hat{y}_i - \bar{y})^2$

(DOANE; SEWARD, 2014; MALMIR et al., 2017; SICHE et al., 2007)

The application of this FIS aims to provide a practical and intuitive tool, based on the results of this research, so that researchers, extension agents, and producers themselves can assess the level of technology adoption in peanut production.

## Main Features

* **Graphical Interface in MatLab:** A user interface developed in the MatLab environment to facilitate data input and visualization of the technological level index results.
* **Fuzzification of Input Variables:** The input data for the five indicators are converted into fuzzy linguistic variables using **trapezoidal Membership Functions (MFs)**:
    1.  **Self-Propelled Sprayer:** Low (MF1), High (MF2) - Domain: $[a_1, b_1]$
        * Low (MF1): `trapmf([-0.82 -0.18 0.4 0.6])`
        * High (MF2): `trapmf([0.4 0.6 1.1 1.9])`
    2.  **Equipment:** Low (MF1), Medium (MF2), High (MF3) - Domain: $[a_2, b_2]$
        * Low (MF1): `trapmf([-0.375 -0.04167 0.04167 0.4])`
        * Medium (MF2): `trapmf([0.3 0.4 0.6 0.7])`
        * High (MF3): `trapmf([0.5862 0.6662 1.609 9.068])`
    3.  **Inputs:** Low (MF1), Medium (MF2), High (MF3) - Domain: $[a_3, b_3]$
        * Low (MF1): `trapmf([-0.3 -0.04 0.294973544973545 0.398])`
        * Medium (MF2): `trapmf([0.3 0.398 0.599 0.69973544973545])`
        * High (MF3): `trapmf([0.604 0.7 1.04 1.38])`
    4.  **Storage:** Simple (MF1), Medium (MF2), Better (MF3), Optimal (MF4) - Domain: $[a_4, b_4]$
        * Simple (MF1): `trapmf([-0.3 -0.0333 0.2 0.3])`
        * Medium (MF2): `trapmf([0.2 0.3 0.4 0.6])`
        * Better (MF3): `trapmf([0.4 0.6 0.7 0.8])`
        * Optimal (MF4): `trapmf([0.7 0.8 1.033 1.3])`
    5.  **Management:** Low (MF1), Medium (MF2), High (MF3) - Domain: $[a_5, b_5]$
        * Low (MF1): `trapmf([-0.3 -0.0417 0.3 0.4])`
        * Medium (MF2): `trapmf([0.3 0.4 0.6 0.7])`
        * High (MF3): `trapmf([0.6 0.7 1.042 1.375])`
* **Fuzzy Rule Base:** Implements a base of **216 inference rules** ("IF-THEN") that relate the fuzzified input variables to the output variable. The rules were defined based on the characteristics of the input variables and the metrics structured for the assessment of the technological level.
* **Output Variable:** The **Technological Level** is defined by five linguistic terms with trapezoidal membership functions:
    * Very Low (MF1): `trapmf([-0.225 -0.025 0.1 0.2])`
    * Low (MF2): `trapmf([0.1 0.25 0.3 0.4])`
    * Medium (MF3): `trapmf([0.3 0.4 0.6 0.8])`
    * High (MF4): `trapmf([0.5 0.7 0.85 0.9])`
    * Very High (MF5): `trapmf([0.8 0.9 1.025 1.225])`
* **Fuzzy Inference (Mamdani):** The system uses the Mamdani linguistic inference method to aggregate the outputs of the fuzzy rules.
* **Defuzzification (Centroid):** The centroid method is employed to convert the fuzzy output set into a representative numerical value of the Technological Level Index. This value is presented as a percentage, facilitating the interpretation of the technology adoption level.
* **ANFIS/FIS Architecture:** The system was structured in MatLab software using the ANFIS (Adaptive Neuro-Fuzzy Inference System) / FIS (Fuzzy Inference System) architecture.

## How to Use

1.  **Prerequisites:** Ensure you have **MatLab** installed on your system.
2.  **Download:** Clone or download this repository.
3.  **Open in MatLab:** Navigate to the repository folder in MatLab and open the main application file (usually with the extension `.m` or `.fig`, depending on whether it has a graphical interface).
4.  **Data Input:** Use the graphical interface (if available) to enter the values corresponding to the five input indicators for the producer you want to evaluate.
5.  **Execute:** Run the application to obtain the Technological Level Index (TLI) as a percentage value.
6.  **Interpretation:** The output value represents the technological level of the producer, ranging from "Very Low" to "Very High", as defined by the output variable's membership functions.

## Contribution

Contributions are welcome! If you have suggestions for improvements, identified any issues, or wish to add new features, feel free to open an issue or submit a pull request.

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for more details.

## Contact Information
[Prof. Celso/São Paulo State University (UNESP)]
[celso.silva@unesp.br] [celsonapoleon@gmail.com]
[[Seu LinkedIn/Outro Link](https://www.linkedin.com/in/celsonapoleon/)]
## References

* DOANE, D. P.; SEWARD, L. E. *Applied Statistics in Business and Economics*. 8th ed. McGraw-Hill Education, 2014.
* MALMIR, M.; ZAREI, M.; GHORBANI, M. A. Developing a model for evaluating the technological innovation capability of agricultural SMEs in Iran. *Journal of Agricultural Science and Technology*, v. 19, n. 1, p. 173-186, 2017. ([Link to the article, if available])
* SICHE, R.; AGUILAR, M. A.; GONZÁLEZ, J. L. An indicator of sustainable development based on fuzzy logic. *Ecological Economics*, v. 60, n. 1, p. 155-166, 2007. 

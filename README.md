# Haiti

This repository contains the code used for the analysis presented in Langlet et al. (2021).

Note that the scripts will not run in the absence of the cleaned data. These scripts are presented only in the interest of reproducibility to detail the procedure used. See the data availability section below for more information.

## Abstract

In low-resource settings, detection of healthcare-acquired outbreaks in neonatal units relies on astute clinical staff to observe unusual morbidity or mortality from sepsis as microbiological diagnostics are often absent.  We aimed to generate reliable (and automated) early warnings for potential clusters of neonatal late-onset sepsis using retrospective data that could signal the start of an outbreak in an NCU in Port au Prince, Haiti, using routinely collected data on neonatal admissions.
We constructed smoothed time series for late-onset sepsis cases, late-onset sepsis rates, NCU mortality, maternal admissions, neonatal admissions, and neonatal antibiotic consumption. An outbreak was defined as a statistical increase in any of these time series indicators. We created three outbreak alarm classes: 1) thresholds: weeks in which the late-onset sepsis cases exceeded four, the late-onset sepsis rates exceeded 10% of total NCU admissions and the NCU mortality exceeded 15%; 2) differential: late-onset sepsis rates and NCU mortality were double the previous week, and 3) aberration: using the improved Farrington model for late-onset sepsis rates and NCU mortality. We validated pairs of alarms by calculating the sensitivity and specificity of the weeks in which each alarm was launched and comparing each alarm to the weeks in which a single GNB positive blood culture was reported from a neonate. The threshold and aberration alarms were the strongest predictors for current and future NCU mortality and current LOS rates (p<0.0002). The aberration alarms were also those with the highest sensitivity, specificity, negative predictive value, and positive predictive value.
In the absence of microbiological diagnostics in NCUs in low-resource settings, applying these simple algorithms to routinely collected data show great potential to facilitate early warning for possible healthcare-acquired outbreaks of LOS in neonates. The methods used in this study require validation across other low-resource settings.

## Data availability

MSF has a managed access system for data sharing that respects MSF’s legal and ethical obligations to its patients to collect, manage and protect their data responsibility. Ethical risks include, but are not limited to, the nature of MSF operations and target populations being such that data collected are often highly sensitive. Data are available on request in accordance with MSF's data sharing policy (available [here](http://fieldresearch.msf.org/msf/handle/10144/306501)). Requests for access to data should be made to [data.sharing@msf.org](mailto:data.sharing@msf.org).

The time series at the basis of this work and the intermediate products (indicators/alarms) are available upon request.

# Methodology and code structure

The repository contains three scripts that should be executed in the following order. A more detailed description of their role is presented below.

1. **Aberrations.Rmd** This R notebook is used to first explore the time series data and detect possible aberrations in the mortality and late-onset sepsis cases. These are possible outbreak alarms.
2. **Analysis.ipynb** This code is used to generate the rest of the alarm time series, the full indicator time series, and the tables presented in the article.
3. **Plotting.ipnyb** This R notebook loads the output of the previous two scripts and generates the plots used in the article.

For each notebook, the required packages are imported in the first code snippet.

#### Aberrations.Rmd

This R notebook first presents an introduction to the data (e.g. some plots of the time series and some basic analysis to deduce the average length of an outbreak). The main output of this notebook, however, is the aberration alarms generated using the mortality and late-onset sepsis time series. Possible outbreaks are tagged using unusually high values in these time series. See paper for more details.

#### Analysis.ipynb

This Jupyter notebook is used to construct the indicator time series and evaluate the ability of each alarm to predict each indicator. See paper for more details.

#### Plotting.ipnyb

This R plot uses the plotting functions from the [surveillance package](https://cran.r-project.org/web/packages/surveillance/index.html) to generate plots of each indicator in combination with every possible alarm.

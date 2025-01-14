# Cost-effectiveness Analysis of Alternative Infant and Neonatal Rotavirus Vaccination Schedules in Malawi

This repo contains the codes for **[medRxiv__link](https://doi.org/10.1101/2024.11.22.24317751)**

This study compares the cost-effectiveness of 5 rotavirus vaccine strategies in Malawi from 2025-2034.

#### Vaccine strategies:

#### 1. No vaccination

#### 2. Rotarix 2-dose schedule (administered at 6 and 10 weeks)

#### 3. Rotarix 3-dose schedule (administered at 6, 10, and 14 weeks)

#### 4. Rotarix 3-dose schedule (administered at 6, 10, and 40 weeks)

#### 5. Next-generation neonatal (RV3-BB) 3-dose schedule (administered at 1, 6, and 10, weeks)

These strategies were evaluated from the government and societal perspectives. ICERs were calculated and cost-effectiveness was also evaluated using the net-benefit framework.

## File descriptions

TDMdata.Rdata contains the simulated epidemiological data generated using the model in [Pitzer et al. 2024]([url]\(https://www.nature.com/articles/s41541-024-01008-6\)). It includes the yearly number of moderate-to-severe and non-severe cases for 5 age groups (<1yr, 1-<2yrs, 2-<3yrs, 3-<4yrs, 4-<5yrs) over the ten-year time horizon for all 5 vaccine strategies.

Rota_CEA_Case_1.Rmd runs the CEA and generates figures for Scenario 1 from the paper which compares all vaccine strategies using Malawi's current Rotarix 6/10 strategy as the baseline.

Rota_CEA_Case_2.Rmd runs the CEA and generates figures for Scenario 2 from the paper which compares only available vaccine strategies using no vaccination as the baseline. The neonatal vaccine is excluded from this analysis because it is not on the market yet.

Rota_CEA_sens10.Rmd runs a price sensitivity analysis to determine the maximum price per dose that the neonatal vaccine could cost while remaining cost-effective compared to the Rotarix 6/10 strategy, given a fixed willingness-to-pay.

Rota_CEA_sens14.Rmd runs a price sensitivity analysis to determine the maximum price per dose that the neonatal vaccine could cost while remaining cost-effective compared to the Rotarix 6/10/14 strategy, given a fixed willingness-to-pay.

## Data & Parameter Descriptions

**Table 1. Description Key for dataset names in TDMdata.Rdata**

There are 54 data frames contained within TDMdata. Rdata Each data frame has ten columns for the timeframe of the simulation (2025-2034) and has 1000 rows that represent each simulation. The data frames with an age, disease severity, and vaccine strategy designation contain the number of cases that occurred per year of that disease severity, for that age group, and given that vaccine strategy was used. The data frames with ‘NumDoses’ and a vaccine strategy designation contain the number of doses of that vaccine strategy that were administered each year.

| ***Age Groups***       |                                        |
| ---------------------- | -------------------------------------- |
| Yr0                    | 0 to <1 years old                      |
| Yr1                    | 1 to <2 years old                      |
| Yr2                    | 2 to <3 years old                      |
| Yr3                    | 3 to <4 years old                      |
| Yr4                    | 4 to <5 years old                      |
| ***Disease Severity*** |                                        |
| MS                     | Moderate-to-severe cases               |
| NS                     | Non severe cases                       |
| ***Vaccine Strategy*** |                                        |
| NoVac                  | No vaccination                         |
| 6\_10                  | Rotarix 6/10 schedule                  |
| 6\_10\_14              | Rotarix 6/10/14 schedule               |
| 6\_10\_40              | Rotarix 6/10/40 schedule               |
| 1\_6\_10               | Neonatal 1/6/10 schedule               |
| ***Vaccine Doses***    |                                        |
| NumDoses               | Number of doses administered each year |

For example, “Yr0MS6_10_14” is a data frame that contains the number of moderate-to-severe cases in the 0-<1 age group that occurred each year when the Rotarix 6/10/14 strategy was implemented over 1000 simulations.

**Table 2. Input parameters for cost-effectiveness analysis**

| **Parameter**                                             | **Variable Name**      | **Estimate**  | **Uncertainty Distribution** | **Source**               |
| --------------------------------------------------------- | ---------------------- | ------------- | ---------------------------- | ------------------------ |
| ***Treatment probabilities for moderate-to-severe RVGE*** |                        |               |                              |                          |
| Probability of seeking treatment                          | pr\_seek               | 0.8           | Beta(2600,650)               | (Omore, et al., 2013)    |
| Probability of not seeking treatment                      | pr\_no\_treat          | 0.2           | 1-  Beta(2600,650)           | (Omore, et al., 2013)    |
| Probability of care - inpatient                           | pr\_inpat              | 0.6           | Beta(1432,955)               | (Omore, et al., 2013)    |
| Probability of care - outpatient                          | pr\_outpat\_MS         | 0.4           | 1 - Beta(1432,955)           | (Omore, et al., 2013)    |
| Probability of death - inpatient (CFR inpatient)          | pr\_death\_inpat       | 0.011         | Beta(6.74,606.29)            | (Asare, et al., 2022)    |
| Probability of death - outpatient (CFR outpatient)        | pr\_death\_outpat      | 0.0055        | CFR inpatient\*Unif(0,1)     | (Asare, et al., 2022)    |
| Probability of death - no treatment (CFR no treatment)    | pr\_death\_notreat     | 0.025         | Beta(6.63,258.72)            | (Asare, et al., 2022)    |
| ***Treatment probabilities for non-severe RVGE***         |                        |               |                              |                          |
| Probability of care - outpatient                          | pr\_outpat\_NS         | 0.55          | Beta(833,681)                | (Omore, et al., 2013)    |
| Probability of no care                                    | pr\_no\_treat\_NS      | 0.45          | 1 - Beta(833,681)            | (Omore, et al., 2013)    |
| Probability of death – non-severe                         | NA                     | 0             | Fixed                        | Assumption               |
| ***Vaccine-related costs\****                             |                        |               |                              |                          |
| Cost of vaccine (per dose) - Rotarix                      | costRotarix            | 1.94 USD      | Fixed                        | (UNICEF, 2024)           |
| Cost of vaccine (per dose) - Neonatal                     | costNeonatal           | 1.32 USD      | Fixed                        | (Hamidi, et al., 2021)   |
| Cost of delivery of vaccine (per dose)                    | delRotarix             | 0.58 USD      | Fixed                        | (Pencenka, et al., 2018) |
| Cost of switching - Neonatal                              | cost\_switching        | 1,024,365 USD | Fixed                        | (Owusu, et al., 2023)    |
| Vaccine wastage rate                                      | wastage                | 0.05          | Fixed                        | (Wolfson, et al., 2008)  |
| ***Treatment costs\****                                   |                        |               |                              |                          |
| Cost of treatment† - inpatient, moderate-severe           | cost\_in\_trt          | 62.39 USD     | Gamma(1.39,43.54)            | (Barzeev, et al., 2016)  |
| Cost of treatment - outpatient, moderate-severe           | cost\_out\_trt\_MS     | 22.20 USD     | Gamma(15.18, 1.46)           | (Barzeev, et al., 2016)  |
| Cost of treatment - outpatient, non-severe                | cost\_out\_trt\_NS     | 11.10USD      | Gamma(7.56,1.47)             | (Barzeev, et al., 2016)  |
| Household cost‡ - inpatient, moderate-severe              | cost\_in\_trt\*\*      | 15.20 USD     | Gamma(0.81,18.76)            | (Barzeev, et al., 2016)  |
| Household cost - outpatient, moderate-severe              | cost\_out\_trt\_MS\*\* | 9.44 USD      | Gamma(0.79,11.94)            | (Barzeev, et al., 2016)  |
| Household cost - outpatient, non-severe                   | cost\_out\_trt\_NS\*\* | 0.68 USD      | Gamma(0.24,2.87)             | (Barzeev, et al., 2016)  |
| ***Disability-adjusted life-year (DALY) parameters***     |                        |               |                              |                          |
| DALY weight - moderate-to-severe                          | daly\_wt\_MS           | 0.281         | Beta(18.59,47.57)            | (Barzeev, et al., 2016)  |
| DALY weight - non-severe                                  | daly\_wt\_NS           | 0.202         | Beta(17.96,70.93)            | (Barzeev, et al., 2016)  |
| Duration of infection                                     | dur\_inf               | 6 days        | Fixed                        | (Barzeev, et al., 2016)  |
| Life expectancy at birth                                  | life\_exp              | 63 years      | Fixed                        | (World Bank, 2021)       |
| ***Economic evaluation***                                 |                        |               |                              |                          |
| ½ \* Gross domestic product (GDP) per capita - Malawi     | WTPnum                 | 335 USD       | Fixed                        | (World Bank, 2022)       |
| Discount rate                                             | discount               | 0.03          | Fixed                        | (WHO, 2019)              |

*All costs are inflated by 3% per year to reflect predicted 2025 prices
†Per case costs to the government used in both government and societal perspective analysis
‡Per case direct and indirect costs (including loss of productivity) to the household used in the societal perspective analysis
**Uncomment lines in the code to run the societal perspective. Case 1 Lines 223-6, Case 2 Lines 184-7, Sens10 Lines 150-3, and Sens14 Lines 150-3.
![image](https://github.com/user-attachments/assets/a2098873-857a-475d-a36a-a34e86f14764)


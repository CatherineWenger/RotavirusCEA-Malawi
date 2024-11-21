# Cost-effectiveness Analysis of Alternative Infant and Neonatal Rotavirus Vaccination Schedules in Malawi

This repo contains the codes for __medRxiv__link__

This study compares the cost-effectiveness of 5 rotavirus vaccine strategies in Malawi from 2025-2034.

### Vaccine strategies: 
### 1. No vaccination 
### 2. Rotarix 2-dose schedule (administered at 6 and 10 weeks)
### 3. Rotarix 3-dose schedule (administered at 6, 10, and 14 weeks)
### 4. Rotarix 3-dose schedule (administered at 6, 10, and 40 weeks)
### 5. Next-generation neonatal (RV3-BB) 3-dose schedule (administered at 1, 6, and 10, weeks)

These strategies were evaluated from the government and societal perspectives. ICERs were calulated and cost-effectiveness was also evaluated using the net-benefit framework.

## File descriptions
TDMdata.Rdata contains the simulated epidemiological data generated using the model in [Pitzer et al. 2024]([url](https://www.nature.com/articles/s41541-024-01008-6)). It includes the yearly number of moderate-to-severe and non-severe cases for 5 age groups (<1yr, 1-<2yrs, 2-<3yrs, 3-<4yrs, 4-<5yrs) over the ten-year time horizon for all 5 vaccien strategies. 

Rota_CEA_Case_1.Rmd runs the CEA and generates figures for Scenario 1 from the paper which compares all vaccine strategy using Malawi's current Rotarix 6/10 strategy as the baseline.

Rota_CEA_Case_2.Rmd runs the CEA and generates figures for Scenario 2 from the paper which compares only available vaccine strategies using no vaccination as the baseline. The neonatal vaccine is excluded from this analysis because it is not on the market yet.

Rota_CEA_sens10.Rmd runs a price sensitivity analysis to determine, at a fixed willingness-to-pay, what is the maximum price per dose that the neonatal vaccine could cost while remaining cost-effective compared to the Rotarix 6/10 strategy.

Rota_CEA_sens14.Rmd runs a price sensitivity analysis to determine, at a fixed willingness-to-pay, what is the maximum price per dose that the neonatal vaccine could cost while remaining cost-effective compared to the Rotarix 6/10/14 strategy.

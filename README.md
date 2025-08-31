# Commodity-Price-MonteCarlo-Simulation-R-
Monte Carlo simulation in R to forecast commodity price distributions and visualize multiple scenarios to discuss the feasibility of introducing Carbon Credit Allocation into Germany electricity market.

# Wind Farm Valuation in Germany: Carbon Credit Allocation Analysis  
  
**Supervised by Helyette Geman & Roza Galeeva**  

----------------------------------------------------------------------------------------

## Table of Contents  

- [Project Overview](#project-overview)  
- [Background & Problem Statement](#background--problem-statement)  
- [Methodology](#methodology)  
- [Key Takeaways](#key-takeaways)  
- [Deliverables](#deliverables)  
- [File Structure](#file-structure)  
- [Acknowledgments](#acknowledgments)  

----------------------------------------------------------------------------------------

## Project Overview  
- **Issue**  
  1. Germany adopts a 100% auction system for carbon credits with no free allocation, which limits wind farm profitability  
  2. This raises concerns for investment attractiveness and policy efficiency in renewable energy markets
- **Goal**  
- Evaluate how introducing carbon credit allocation (0%, 20%, 50%, 80%) impacts wind farm valuation, and compare valuation differences under spot price trading and forward contracts (1Y, 3Y, 5Y) to identify the allocation rate that provides the most balanced outcome for both investors and policy makers.  

----------------------------------------------------------------------------------------

## Background & Problem Statement    
- **Cap-and-Trade System**  
- Adopted in the US (California), EU, and East Asia (China, South Korea, Japan)  
- Companies exceeding the emission cap must purchase carbon credits to offset extra emissions  
- Some governments allocate credits for free, allowing companies to sell unused credits for profit  
- **German Market Context**  
- Germany uses a 100% auction system: all credits must be purchased at market price 
- Wind power has a very low emission factor (0.015 t/MWh), but still affected by credit pricing
- **Problem Statement**  
- Should Germany introduce a partial allocation system and What is the optimal allocation rate (20%, 50%, 80%) for improving wind farm valuation and ensuring investment stability?  

----------------------------------------------------------------------------------------

## Methodology  
- **Dataset Selection**  
- 5 years of daily and monthly electricity and carbon credit prices from Bloomberg Terminal
- Electricity spot: LPXBHR01; Forward (1Y, 3Y, 5Y): ELGBYR1, ELGBYR3, ELGBYR5.  
- Carbon prices: EEXX04EA (spot), MOZ25/27/29 (forward).  
- **Analysis Process**
- **Formula**
- Assume our research subject is a medium-sized wind farm in Germany, and we use NPV as the metric to evaluate its profitability
- Total revenue = Electricity sales revenue + Carbon credit revenue
- Electricity sales revenue = Generation (500 MWh) * Price
- Carbon credit revenue = Price * Carbon credit allocated
- Carbon credit allocated = Allocation rate * Generation *  EmFac (0.015 tCO₂/MWh)
- **Spot Price Simulation**  
- Monte Carlo (1000 paths, 10 years, monthly).  
- Compare NPV under 0%, 20%, 50%, 80% allocation.  
- **Forward Contract Simulation**  
- Contracts (1Y, 3Y, 5Y) combined with spot after expiry.  
- Compare NPV distributions across allocation rates.  
- **Confidence Interval Comparison**  
- Error bar plots comparing: Spot vs Forward (without allocation), With vs without allocation (spot), Different allocation rates under forward contracts  
- **Tools**  
- R (Geometric Brownian Motion, Monte Carlo Simulation)  
- R Markdown for reproducible outputs and visualizations 

----------------------------------------------------------------------------------------

## Key Takeaways  
- **Findings**  
- 1. **Spot Price**  
     Without allocation, NPV is low 
     Allocation significantly increases NPV
     Higher rates (20% → 50% → 80%) improve NPV, but with rising variance  
  2. **Forward Contracts**  
     Longer contracts increase revenue stability  
     3Y contracts generate the highest NPV 
     Allocation boosts NPV, with 50% rate showing the best balance, because the increase from 50% to 80% are marginal compared to 20% → 50%  
  3. **Comparison (Spot vs Forward)**  
     Forward contracts reduce variance, offering more stable outcomes  
     Allocation improves valuation but adds sensitivity under forward pricing  
     At 0% allocation, contract length has little effect  
- **Recommendations**  
- Introducing carbon credit allocation enhances wind farm profitability in Germany
- 50% allocation rate is an optimal balance for policy and investment  
- Forward contracts with allocation provide stable and predictable returns  
- Findings support both policy reform and corporate investment strategies

----------------------------------------------------------------------------------------

## Deliverables  
- This repository includes:  
  - [Project Code and Graphic Output](./code%20and%20output/)  
  - [Dataset – Carbon & Electricity Prices](./data/)  
  - [Final Presentation Slides](./Final%20Presentation%20Slides.pptx)  

----------------------------------------------------------------------------------------

## File Structure  
- |-code and output/  
   --commodity market.Rmd  
   --Graphic Outputs.pdf  
   --Project Code and Output.pdf  
- |-data/  
   --carbon credit and electricity price.xlsx  
   --european_wholesale_electricity_price.xlsx  
- |-Final Presentation Slides.pptx  
- |-README.md  

----------------------------------------------------------------------------------------

## Acknowledgments  
- **Data Source**: Bloomberg Terminal  
- **JHU Advisors**: Helyette Geman, Roza Galeeva  

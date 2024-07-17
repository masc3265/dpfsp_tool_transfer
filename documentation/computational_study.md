## Computational Study

The high number of parameters enables numerous analyses to synthesize cause-and-effect relationships. Some promising analyses are listed below:

1. Analysis of the effect of transfers on the Pareto front
2. Analysis of changes in the tightness of eligibility constraints starting from 1 up to $\phi$ eligible factories
3. Analysis of the effect of an increase in the emission price
4. Analysis of the effect of limiting the transfer options
5. Analysis of the effect of varying the product and tool weight
6. Analysis of the effect of increasing the number of factories or machines

Due to the page limit the focus is set to examine the impact of tool transfers, of the carbon emission price, and the limitation of transfer options. Since the impact of tool transfers is analyzed via random instances with varying eligibility, only the procedure for analyzing the impact of the carbon emission price and the limitation of tool transfers is explained in more detail below. 

### Emission Price Variation

The emission price is tested on four different factor levels, namely 0, 89, 195 and $680\frac{€}{tCO_2e}$, with 89 \EUR{}/t representing the average carbon emission price in the EU from January to September 2023 [(see Trade Economics)](https://tradingeconomics.com/commodity/carbon).
The remaining factor levels are price estimates that account for the needs of future generations in the pricing process [Umweltbundesamt 2020](https://www.umweltbundesamt.de/sites/default/files/medien/1410/publikationen/2020-12-21_methodenkonvention_3_1_kostensaetze.pdf). These prices are based on the idea of a pure time preference rate. The price with a pure rate of time preference (RZPR) of 0% leads to a balance between current and future losses. A pure time preference rate of 1%, on the other hand, represents a devaluation of future damage in that only 74% of the damage caused to the next generation (in 30 years) is taken into account and only 55% of the damage caused to the generation after next (in 60 years). The Federal Environment Agency recommends an emissions price of $680\frac{€}{tCO_2}e$ for 2020 with a pure time preference rate of 0%. With a time preference rate of 1%, the price still amounts to $195\frac{€}{tCO_2e}$. 

Since the emission price only affects the factory allocation decision, the impact is measured by the number of job reallocations in the lexicographic cost solution following an increase in emission price from 0\EUR{}/t to 680\EUR{}/t.

### Limited Transfer Options

The number of transfer options is limited to a percentage [0.2, 0.4, 0.6, 0.8, 1] of the total number of jobs across all factories. Consequently in an instance with $n = 12$ jobs and a transfer limit of 20%, a maximum of $\\lceil12\cdot 0,2\rceil = \lceil2.4\rceil = 3$ jobs can be transferred across all factories.  

### Experimental Settings

The Pareto front is assessed with the bisection $\epsilon$-constraint method according to [Chircop and Zammit-Mangion](https://www.um.edu.mt/library/oar/handle/123456789/112261), promising an even distribution of solutions in the Pareto front.
Utilizing the lexicographic solutions, an additional 28 Pareto solutions are identified using the bisection $\epsilon$-constraint method, with each run limited to 10 minutes. Consequently, a total of 30 Pareto solutions are determined in each run. The calculations are made with version 10.0.2 of Gurobi on an AMD EPYC 7513 with 18 cores at 2.6\,GHz and 32GB RAM.


## Problem Instances

Due to the NP-hardness of the DPFSP, only small instances with the following characteristics are solved optimally.  

Number of factories:  $F = [2, 3, 4]$

Number of jobs: $n = [8, 10, 12, 14]$

Number of machines: $m = [2, 3, 4, 5]$

Number of speed factors: V = $[1, 1.25, 1.5, 1.75, 2]$

Concerning the factories and customer locations Europe is used as reference. First, the countries of factories are selected via roulette wheel selection based on the manufacturing industry's GDP without replacement. The roulette wheel selection is used because it is assumed that economically strong countries are preferred when selecting a location. Based on this, a random city within the selected country is chosen as the factory location. The customer location corresponds to a random city in the individual European countries. Given the longitude and latitude of the cities the delivery and transfer distances are calculated using the Open Source Routing Machine. Distances are used since the API uses car as driving mode. Furhter, it is assumed that transports are carried at full truckloads so that the costs and emissions are allocated proportionately to the tool or product weight. The due dates are assumed to be factory-dependent and are calculated as follows:

```math
d_{j,f}=\max\left\{0,\sum_{i=1}^m\left(p^1_{j,i,f}+p^{setup}_{j,i,f}\right)\cdot\left(1+\frac{rand}{2\cdot f}\right)+t^{min}_{j,f}-\left(t_{j,f}-t^{min}_{j}\right)\right\} \quad \forall j,f
```
Here, $`t^{min}_{j}`$ is the minimum delivery time to a customer across all factories, $`t_{j,f}`$ is the delivery time from factory $f$ to customer $j$, and $rand$ is a random number between 0 and 1. Consequently, longer delivery times result in shorter due dates for production.

The priority of a customer $j$ is drawn from the interval $[1, 10]$. The emission price is set at $89\frac{€}{t}$ corresponding to the average emission price from 01.2023 to 09.2023 [Trade Economics](https://tradingeconomics.com/commodity/carbon).

The factory eligibility constraints are more difficult to initialize, as the number of eligible factories for a job is likely to vary depending on the company. For instances with $f = 2$, one factory is randomly selected as eligible for each job. In instances with $f=\lbrace3, 4\rbrace$ factories, the eligibility is randomly set to one or two factories per job, which are randomly selected.

### Transportation Parameters

- Transportation costs per kilometer: $1.56€$
- Emission factor for Diesel consumption: $3.24\frac{kgCO_2}{l}$
- Fuel consumption: $\frac{0.345l}{km}$
- Payload: 25000
- Compensation factor for empty runs: 1.15
- TruckSpeed: 80
- Tool weights: [25kg, 50kg, 100kg, 1000kg, 5000kg, 25000kg]
- Product weights: [25kg, 50kg, 100kg, 1000kg, 5000kg, 25000kg]

### Production Parameters

Concerning electricity prices and emission factors in each factory, the experiment is based on data from EU-27 countries. As the country of a factory is selected with the roulette wheel selection, the factory is then associated with the countries emission factor and electricity price. A job's processing and setup times are taken randomly from the interval $[1h, 10h]$ or $[0.5h, 1.5h]$, with the processing time of an operation fluctuating by a maximum of ( $\pm 30\%$ ) across factories to realistically limit heterogeneity.That means processing times are drawn randomly from the intervall $[1h, 10h]$ or $[0.5h, 1.5h]$ for each operation of each job in the first factory. The processing times in the remaining factories are based on the first factory with an variation of $\pm 30$\%. Otherwise the exact same operation of a job could last 1h or 10h in two different factories, which is not that realistic in our opinion. Moreover, the processing times are adjustable via a discrete set of speed factors. Increasing the processing speed leads similar to [Wang and Wang (2018)](https://doi.org/10.1109/TSMC.2017.2788879) to an increase in the base power consumption. The base power consumption at the lowest speed factor $P_{j,i,f}^1$ is discrete and drawn from $[2kW, ..., 5kW]$ and increases with an increase of the speed factor $V = [1, 1.25, 1.5, 1.75, 2]$ according to $P_{j,i,f}^v = P_{j,i,f}^1 \cdot v^2$.

- Minimum power consumption: 2 kW
- Maximum power consumption: 5 kW
- Minimum processing time: 1 hour
- Maximum processing time: 10 hours
- Processing time variability: ±30%
- Minimum setup time: 0.5 hours
- Maximum setup time: 1.5 hours
- Minimum setup power consumption: 3.5 kW
- Maximum setup power consumption: 4.5 kW

### Data 

1. EEA (2024). Greenhouse gas emission intensity of electricity generation in Europe. https://www.eea.europa.eu/en/analysis/indicators/greenhouse-gas-emission-intensity-of-1
2. Eurostat (2024). Electricity price statistics. https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Electricity_price_statistics#Electricity_prices_for_non-household_consumers
3. Statista (2024). Europäische Union: Anteile der Wirtschaftssektoren am Bruttoinlandsprodukt (BIP) der Mitgliedstaaten im Jahr 2022. https://de.statista.com/statistik/daten/studie/249080/umfrage/anteile-der-wirtschaftssektoren-am-bruttoinlandsprodukt-bip-der-eu-laender/
4. GeoNames. Cities with a population of 15000 or greater. https://download.geonames.org/export/dump/
5. Trade Economics (2023). EU Carbon Permits. https://tradingeconomics.com/commodity/carbon







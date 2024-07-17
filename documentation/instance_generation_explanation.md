
## Problem Instances

Due to the NP-hardness of the DPFSP, only small instances with the following characteristics are solved optimally.  

Number of factories:  $F = [2, 3, 4]$

Number of jobs: $n = [8, 10, 12, 14]$

Number of machines: $m = [2, 3, 4, 5]$

Number of speed factors: V = $[1, 1.25, 1.5, 1.75, 2]$

Concerning the factories and customer locations Europe is used as reference. Consequently, random European cities are used for factories and customers, with factories selected via roulette wheel selection based on the manufacturing industry's GDP. Given the longitude and latitude of the cities the delivery and transfer distances are calculated using the Open Source Routing Machine. Distances are used since the API uses car as driving mode. Furhter, it is assumed that transports are carried at full truckloads so that the costs and emissions are allocated proportionately to the tool or product weight. The due dates are assumed to be factory-dependent and are calculated as follows:

```math
d_{j,f}=\max\left\{0,\sum_{i=1}^m\left(p^1_{j,i,f}+p^{setup}_{j,i,f}\right)\cdot\left(1+\frac{rand}{2\cdot f}\right)+t^{min}_{j,f}-\left(t_{j,f}-t^{min}_{j}\right)\right\} \quad \forall j,f
```
Here, $`t^{min}_{j}`$ is the minimum delivery time to a customer across all factories, $`t_{j,f}`$ is the delivery time from factory $f$ to customer $j$, and $rand$ is a random number between 0 and 1. Consequently, longer delivery times result in shorter due dates for production.

### Transportation Parameters###

- Transportation costs per kilometer: $1.56€$
- Emission factor for Diesel consumption: $3.24\frac{kgCO_2}{l}$
- Fuel consumption: $\frac{0.345l}{km}$
- Payload: 25000
- Compensation factor for empty runs: 1.15
- TruckSpeed:80,
- Tool weights: [25kg, 50kg, 100kg, 1000kg, 5000kg, 25000kg]
- Product weights: [25kg, 50kg, 100kg, 1000kg, 5000kg, 25000kg]

### Production Parameters###

Concerning electricity prices and emission factors in each factory, the experiment is based on data from EU-27 countries. As the country of a factory is selected with the roulette wheel selection, the factory is then associated with the countries emission factor and electricity price. A job's processing and setup times are taken randomly from the interval $[1h, 10h]$ or $[0.5h, 1.5h]$, with the processing time of an operation fluctuating by a maximum of ( $\pm 30\%$ ) across factories to realistically limit heterogeneity.That means processing times are drawn randomly from the intervall $[1h, 10h]$ or $[0.5h, 1.5h]$ for each operation of each job in the first factory. The processing times in the remaining factories are based on the first factory with an variation of $\pm 30$\%. Otherwise the exact same operation of a job could last 1h or 10h in two different factories, which is not that realistic in our opinion. Moreover, the processing times are adjustable via a discrete set of speed factors. Increasing the processing speed leads similar to Wang and Wang (2018) to an increase in the base power consumption. The base power consumption at the lowest speed factor $P_{j,i,f}^1$ is discrete and drawn from $[2kW, ..., 5kW]$ and increases with an increase of the speed factor $V = [1, 1.25, 1.5, 1.75, 2]$ according to $P_{j,i,f}^v = P_{j,i,f}^1 \cdot v^2$.

- Minimum Power Consumption: 2 kW
- Maximum Power Consumption: 5 kW
- Minimum Processing Time: 1 hour
- Maximum Processing Time: 10 hours
- Processing Time Variability: ±30%
- Minimum Setup Time: 0.5 hours
- Maximum Setup Time: 1.5 hours
- Minimum Setup Power Consumption: 3.5 kW
- Maximum Setup Power Consumption: 4.5 kW
- Minimum Idle Power Consumption: 0.5 kW
- Maximum Idle Power Consumption: 1.5 kW







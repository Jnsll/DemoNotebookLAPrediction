# DemoNotebookLAPrediction
A notebook to make Loop Aggregation prediction. Extracted from and linked with https://github.com/Jnsll/LAPrediction.

## Context
Modflow, a hydrological simulator, is used to predict the underground watertable mouvements in order to assess the vulnerability of a geographical site (i.e. watershed). However, a simulation can last more than 20 hours and we need to run numerous simulations (i.e., across a lot of different sites and/or chronicles). We developped an approach named `Loop Aggregation` which reduces the execution time of the simulation while preserving acceptable results.
The loop aggregation technique reduces the execution time by reducing the number of computations done inside the iterative loop of the simulator. For instance, instead of computing the position of the watertable every day over a 50 year period, only the computations corresponding to one every `p` days will be done. `p` can take the value inside the following list : [2, 7, 15, 21, 30, 45, 50, 60, 75, 90, 100, 125,150,182,200,250,300,330,350,550,640,750,1000,1500,2000,2250,3000,3182,3652]. `p` is named the `aggregation rate` (it is named `Rate` in the data). The higher `p` is, the less computations is done and the faster the simulation is.
To know to what extend we can "approximate", meaning to which value of `p`, we can reduce the execution time, we need to check that the results produced by the approximate simulation are still scientifically acceptable. To do so, an `acceptability indicator` (i.e. named in the data `HError`) has been elaborated and is computed for every approximate simulation (for every simulation using a different value of `p`).
When the value of the `acceptability indicator` is below the threshold of `0.1`, that means that the approximate simulation is `valid` and we can use the `loop aggregation` approach on the simulator with the corresponding aggregation rate.
When HError > 0.1, the approximate simulation is invalid. We can use this rate for applying the `loop aggregation` technique.


## Goal:
Using the data we have already generated, we would like to predict the maximal value of the aggregation rate (i.e. pmax) leading to the fastest approximate simulation being valid, meaning the rate for which HError is below 0.1 and the closest to 0.1, in the context of a new chronicle or a new site. The goal is to use some Machine Learning techniques to do so.


## Data

TO DO : description of the data

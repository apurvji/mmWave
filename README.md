# Millimeter Wave Blockage Modeling

Work towards my thesis at NYU

We present a simplified model for the key QoS parameters such as blockage probability, frequency, and duration in mmWave cellular systems. Our model considers an open park-like area with dynamic blockage due to mobile blockers and self-blockage due to user's own body. A typical user is at the center and the BSs are distributed uniformly around the user. The user is considered blocked when all potential BSs around the UE are blocked simultaneously. 

# Understand the Code
## SimulationLOS.m
The MATLAB simulations considers random waypoint mobility model for blockers. The main file is [SimulationLOS.m](SimulationLOS.m).

It takes around 1 hour to run for a single iteration. We obtained results for 10,000 iterations using [NYU HPC](HPC_Matlab.md) (high performance computing)

Note: SimulationLOS.m uses the following the functions- [Generate_Mobility.m](Generate_Mobility.m) (copied from [here)](https://www.mathworks.com/matlabcentral/fileexchange/30939-random-waypoint-mobility-model), [BlockageSimFn.m](BlockageSimFn.m), [find_blockage_distance.m](find_blockage_distance.m).

The results are analysed using [processData8.m](processData8.m)

## TheoryLOS.m
The [TheoryLOS.m](TheoryLOS.m) implements the theoretical results of LOS blockage. Finally, [plotResults.m](plotResults.m) takes the data from csv files and plots the nice figures comparing theory and simulation :)

# Results
Our results tentatively show that the density of BS required to provide acceptable quality of experience to AR/VR applications is much higher than that obtained by capacity requirements alone. This suggests that the mmWave cellular networks may be blockage limited instead of capacity limited. 

Also, the optimal height of BSs would be lower as compared to microwave BSs. 

# Future Work

The following extensions are planned for future work

* **Generalized blockage model:** We can add a simple model for static blockage in our analysis of dynamic and self-blockage. 
* **Capacity analysis:** The data rates of a typical user can be evaluated using the generalized blockage model. We are interested in evaluating whether 5G mmWave is capacity limited or blockage limited.
* **Fallback to 4G LTE:** We plan to explore the potential solution to blockages as switching to 4G LTE. Whether 4G would be able to handle the huge intermittent 5G traffic.
* **Deterministic networks:** We have considered a random deployment of BSs in our analysis. However, in most cases, the deployments of BSs are based on a deterministic hexagonal grid. Therefore, a blockage model for the deterministic networks is more practical.
* **Backhoul capacity analysis:** With the UEs switching between BSs in case of blockage events, the backhoul capacity requirements for the BS may have high fluctuations. It is interesting to study that random process.
* **Correlated blockage:** We assumed the dynamic blockages of all the BSs are independent (So the overall blockage probability is the product of the blockage probabilities of all the BS-UE links). However, when blockage of multiple BSs are correlated (depends on blocker location;) we might get a higher blockage probability.



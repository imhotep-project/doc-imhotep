# 2. Experiments

## 2.1 Sensitivity experiments (single runs, WP1)

### Summary
![nomenclature tab](./img/imhotep-nomenclature.png)
_If you need to copy or modify this table, the [.doc source is available here](https://docs.google.com/document/d/1bAdjA8vK-TqqfxYqMXz69SUwyC0q7RlbeJqpd-5bzxo/edit?usp=sharing)_.

### Spinup 
Experiment IMHOTEP.02 is the spinup of the WP1 experiments. It ran from 1968 to 2018, starting from climatological initial state.  All other WP1 experiments are initialized from a restart file from IMHOTEP.02 on 1980-01-01.

### Atmospheric forcing
The IMHOTEP ocean simulations are _forced_ by the JRA55 atmoshperic reanalysis. JRA55 is the reanalysis that is being widely used for the OMIP exercise. It provides a forcing set from 1958 to present time (unlike other datasets such as DF5, the DRAKKAR forcing set, that are unavailable after 2015). As any reanalysis, JRA55 has some known biases that should be kept in mind when interpreting the IMHOTEP ocean simulations. More on JRA55 [here](https://climatedataguide.ucar.edu/climate-data/jra-55).

### Other technical details 
An extensive technical doc and details about the NEMO configuration for each simulation have been provided by JM Molines and can be found [here](https://github.com/molines/IMHOTEP/tree/master/eORCA025).

---
## 2.2 Ensemble experiments (WP2))

### Summary
Three ensembles of 10 members each have been produced over 1980-2018. Their names follow the same conventions as in WP1, but start with "E" for Ensemble: EGAI, ES, EAI. 

### Spinup and initialization of the ensembles
![WP2 spinup and init](./img/WP2_spinup_init.png)

### Atmospheric forcing
The IMHOTEP ocean simulations are _forced_ by the JRA55 atmoshperic reanalysis. JRA55 is the reanalysis that is being widely used for the OMIP exercise. It provides a forcing set from 1958 to present time (unlike other datasets such as DF5, the DRAKKAR forcing set, that are unavailable after 2015). As any reanalysis, JRA55 has some known biases that should be kept in mind when interpreting the IMHOTEP ocean simulations. More on JRA55 [here](https://climatedataguide.ucar.edu/climate-data/jra-55).

---
### Other technical details 
An extensive technical doc and details about the NEMO configuration for each simulation have been provided by JM Molines and can be found [here](https://github.com/molines/IMHOTEP/tree/master/eORCA025/ENSEMBLE_SIMULATIONS).

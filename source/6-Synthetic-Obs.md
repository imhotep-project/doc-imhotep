# 6. Synthetic observations

## 6.1 Synthetic along-track altimetry

### What is it? Where to get the data ?
“Synthetic observations" of along-track SSH have  been extracted from the simulated gridded SSH fields from experiment IMHOTEP-GAIc at every single time and locations where a true SLA observation exists in the AVISO database for the along-track altimetry from the TOPEX, Jason-1, Jason-2 and Jason-3 satellite series.

The dataset of the synthetic along-track model SSH is available for the altimetry period 1993-2018 on Zenodo here: [DOI:xxxx](). It is provided there with a time-mean model SSH (gridded model field) over same period (1993-2018) that could be used as a proxy of "MDT" (cf Fig. 6.1).

### What variable does the model provide?

The model SSH from the NEMO-based IMHOTEP simulations is equivalent to the quantity called “ADT”
 in the usual altimetry terms (cf Fig. 6.1):

* In the model, the ocean at rest would be following the geoid (the
iso-gravity surface). And in the model, the gravity is taken constant
(9.80665 m/s2) over the globe , which is itself considered a perfect sphere
(Rt=6371229 m ).

* In the model in practice it is the SSH gradient which is used in the
computation of the horizontal surface pressure. And so SSH is known to
within a constant.

* Note also that the model does not see the atmospheric surface pressure
(set to constant). The atmospheric surface pressure is only taken into
account by the model in the surface flux computation (bulk formulation)

![SSH scheme](./img/SSHscheme.png)
_Fig.6.1 Altimetry vocabulary_.

### Comments on the SSH global mean in the model

* In a Bussinesq model like NEMO, the global mean of SSH has no physical meaning: the global mean of SSH in the model can vary because of the forcing terms E-P-R +(SSS corrective term) -Sea ice..

* In previous simulations such as OCCIPUT, we had to remove the global mean SSH of the model at each time in the outputs before analysing the SLA.

* In the IMHOTEP simulations we alternatively chose to control the global mean SSH on the fly in the model,  by correcting the the freshwater budget so that its global mean is reset to zero at every timestep.

* __However__, in the computation of this correction,  only the terms E-P-R-(-SSS corrective term) are taken into account. The seasonal contribution of sea ice to the freshwater budget is not ( positive contribution when sea ice melts, negative when it freezes).  This means that the global mean SSH in the model is almost reset to almost zero every timesteps but not exactly zero. The delta is due to the sea ice melting/refreezing term. One might need to remove this delta in the global mean depending on the application targeted.

### In practice, how does the synthetic along-track data look like ?

* The along-track files are in netcdf format as produced by the obs operator of the NEMO system model which is called the "feedbak" format (similar to the AVISO format).

* Below is an example of header. The variables that you are interested in are mainly `SLA_SSH` which is the SSH as simulated by the NEMO model in the IMHOTEP simulations. You might also want to look at `SLA_OBS` which is the true observed SLA from AVISO. The model has interpolated its simulated SSH fields to get a model SSH value at every single observation of SLA given in the AVISO files.

You'll find an example notebook to illustrate in practice how to open and plot those files [here](https://github.com/imhotep-project/imhotep-synthetic-obs/blob/main/tools/2023-07-19_check_SLA.ipynb).

```
----------------------------------------------------------------------------------------
regi915@jean-zay3:OBS>>ncdump -h eORCA025.L75-IMHOTEP.GAIc_y2018m06d30_slafb_fdbk.496.nc
netcdf eORCA025.L75-IMHOTEP.GAIc_y2018m06d30_slafb_fdbk.496 {
dimensions:
    N_OBS = 1429621 ;
    N_LEVELS = 1 ;
    N_VARS = 1 ;
    N_QCF = 2 ;
    N_ENTRIES = 2 ;
    N_EXTRA = 1 ;
    STRINGNAM = 8 ;
    STRINGGRID = 1 ;
    STRINGWMO = 8 ;
    STRINGTYP = 4 ;
    STRINGJULD = 14 ;
variables:
    char VARIABLES(N_VARS, STRINGNAM) ;
    	VARIABLES:long_name = "List of variables in feedback files" ;
    char ENTRIES(N_ENTRIES, STRINGNAM) ;
    	ENTRIES:long_name = "List of additional entries for each variable in feedback files" ;
    char EXTRA(N_EXTRA, STRINGNAM) ;
    	EXTRA:long_name = "List of extra variables" ;
    char STATION_IDENTIFIER(N_OBS, STRINGWMO) ;
    	STATION_IDENTIFIER:long_name = "Station identifier" ;
    char STATION_TYPE(N_OBS, STRINGTYP) ;
    	STATION_TYPE:long_name = "Code instrument type" ;
    double LONGITUDE(N_OBS) ;
    	LONGITUDE:long_name = "Longitude" ;
    	LONGITUDE:units = "degrees_east" ;
    	LONGITUDE:_Fillvalue = 99999.f ;
    double LATITUDE(N_OBS) ;
    	LATITUDE:long_name = "Latitude" ;
    	LATITUDE:units = "degrees_north" ;
    	LATITUDE:_Fillvalue = 99999.f ;
    double DEPTH(N_OBS, N_LEVELS) ;
    	DEPTH:long_name = "Depth" ;
    	DEPTH:units = "metre" ;
    	DEPTH:_Fillvalue = 99999.f ;
    int DEPTH_QC(N_OBS, N_LEVELS) ;
    	DEPTH_QC:long_name = "Quality on depth" ;
    	DEPTH_QC:Conventions = "q where q =[0,9]" ;
    	DEPTH_QC:_Fillvalue = 0 ;
    int DEPTH_QC_FLAGS(N_OBS, N_LEVELS, N_QCF) ;
    	DEPTH_QC_FLAGS:long_name = "Quality flags on depth" ;
    	DEPTH_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    double JULD(N_OBS) ;
    	JULD:long_name = "Julian day" ;
    	JULD:units = "days since JULD_REFERENCE" ;
    	JULD:Conventions = "relative julian days with decimal part (as parts of day)" ;
    	JULD:_Fillvalue = 99999.f ;
    char JULD_REFERENCE(STRINGJULD) ;
    	JULD_REFERENCE:long_name = "Date of reference for julian days" ;
    	JULD_REFERENCE:Conventions = "YYYYMMDDHHMMSS" ;
    int OBSERVATION_QC(N_OBS) ;
    	OBSERVATION_QC:long_name = "Quality on observation" ;
    	OBSERVATION_QC:Conventions = "q where q =[0,9]" ;
    	OBSERVATION_QC:_Fillvalue = 0 ;
    int OBSERVATION_QC_FLAGS(N_OBS, N_QCF) ;
    	OBSERVATION_QC_FLAGS:long_name = "Quality flags on observation" ;
    	OBSERVATION_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    	OBSERVATION_QC_FLAGS:_Fillvalue = 0 ;
    int POSITION_QC(N_OBS) ;
    	POSITION_QC:long_name = "Quality on position (latitude and longitude)" ;
    	POSITION_QC:Conventions = "q where q =[0,9]" ;
    	POSITION_QC:_Fillvalue = 0 ;
    int POSITION_QC_FLAGS(N_OBS, N_QCF) ;
    	POSITION_QC_FLAGS:long_name = "Quality flags on position" ;
    	POSITION_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    	POSITION_QC_FLAGS:_Fillvalue = 0 ;
    int JULD_QC(N_OBS) ;
    	JULD_QC:long_name = "Quality on date and time" ;
    	JULD_QC:Conventions = "q where q =[0,9]" ;
    	JULD_QC:_Fillvalue = 0 ;
    int JULD_QC_FLAGS(N_OBS, N_QCF) ;
    	JULD_QC_FLAGS:long_name = "Quality flags on date and time" ;
    	JULD_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    	JULD_QC_FLAGS:_Fillvalue = 0 ;
    int ORIGINAL_FILE_INDEX(N_OBS) ;
    	ORIGINAL_FILE_INDEX:long_name = "Index in original data file" ;
    	ORIGINAL_FILE_INDEX:_Fillvalue = -99999 ;
    float SLA_OBS(N_OBS, N_LEVELS) ;
    	SLA_OBS:long_name = "Sea level anomaly" ;
    	SLA_OBS:units = "Metres" ;
    	SLA_OBS:_Fillvalue = 99999.f ;
    float SLA_Hx(N_OBS, N_LEVELS) ;
    	SLA_Hx:long_name = "Model interpolated SSH - MDT" ;
    	SLA_Hx:units = "Metres" ;
    	SLA_Hx:_Fillvalue = 99999.f ;
    float SLA_SSH(N_OBS, N_LEVELS) ;
    	SLA_SSH:long_name = "Model Sea surface height" ;
    	SLA_SSH:units = "Metres" ;
    	SLA_SSH:_Fillvalue = 99999.f ;
    int SLA_QC(N_OBS) ;
    	SLA_QC:long_name = "Quality on sea level anomaly" ;
    	SLA_QC:Conventions = "q where q =[0,9]" ;
    	SLA_QC:_Fillvalue = 0 ;
    int SLA_QC_FLAGS(N_OBS, N_QCF) ;
    	SLA_QC_FLAGS:long_name = "Quality flags on sea level anomaly" ;
    	SLA_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    	SLA_QC_FLAGS:_Fillvalue = 0 ;
    int SLA_LEVEL_QC(N_OBS, N_LEVELS) ;
    	SLA_LEVEL_QC:long_name = "Quality for each level on sea level anomaly" ;
    	SLA_LEVEL_QC:Conventions = "q where q =[0,9]" ;
    	SLA_LEVEL_QC:_Fillvalue = 0 ;
    int SLA_LEVEL_QC_FLAGS(N_OBS, N_LEVELS, N_QCF) ;
    	SLA_LEVEL_QC_FLAGS:long_name = "Quality flags for each level on sea level anomaly" ;
    	SLA_LEVEL_QC_FLAGS:Conventions = "NEMOVAR flag conventions" ;
    	SLA_LEVEL_QC_FLAGS:_Fillvalue = 0 ;
    int SLA_IOBSI(N_OBS) ;
    	SLA_IOBSI:long_name = "ORCA grid search I coordinate" ;
    int SLA_IOBSJ(N_OBS) ;
    	SLA_IOBSJ:long_name = "ORCA grid search J coordinate" ;
    int SLA_IOBSK(N_OBS, N_LEVELS) ;
    	SLA_IOBSK:long_name = "ORCA grid search K coordinate" ;
    char SLA_GRID(STRINGGRID) ;
    	SLA_GRID:long_name = "ORCA grid search grid (T,U,V)" ;
    float MDT(N_OBS, N_LEVELS) ;
    	MDT:long_name = "Mean dynamic topography" ;
    	MDT:units = "Metres" ;
    	MDT:_Fillvalue = 99999.f ;

// global attributes:
    	:title = "NEMO observation operator output" ;
    	:Convention = "NEMO unified observation operator output" ;
```

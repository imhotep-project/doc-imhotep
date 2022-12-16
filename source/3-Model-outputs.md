# 3. Model outputs

---
## 3.1 How to get access ?
* The project is on-going and the IMHOTEP simulations are prepared and produced on Jean-Zay@IDRIS (french national HPC). The outputs are stored on Jean-Zay and reprensent ~200 To for WP1 (the global sensitivity runs).
* To get access to the data, contact first Thierry Penduff (IGE), William Llovel (LOPS), Jean-Marc Molines (IGE), Stephanie Leroux (Datlas).

---
## 3.2 Where to find the primary outputs on Jean Zay?
The primary outpus are the model outputs produced and archived at run time.

### Location of primary outputs:
* _On Jean-Marc's `$STORE` space:_
```
cd  /gpfsstore/rech/cli/rcli002/eORCA025.L75
```
For WP1 experiments: you'll find the directories `eORCA025.L75-IMHOTEP.<exp>-S/<freq>/<year>`where `exp`: S, GAI, AI ..., `freq`: 1d 5d 1m 1y, `year`is the year.

For WP2 ensemble experiments:
 You'll find the directories: `eORCA025.L75-IMHOTEP.<exp>.<mbr>-S/<freq>/<year>`where 
`exp`: ES, EGAI, EAI ..., `mbr` : 001 à 010, `freq`: 1d 5d 1m 1y.

* _Some more on the ``$STORE/common` space:_

Note that experiment SC (WP1) is located there:
```
/gpfsstore/rech/cli/commun/IMHOTEP/eORCA025.L75-IMHOTEP.SC-S
```
Also, you'll find some untar files of the experiment 02 (WP1 spinup) here:
```
/gpfsstore/rech/cli/commun/IMHOTEP/eORCA025.L75-IMHOTEP.02-S
```

### Which variables are available?
* _For WP1 experiments:_
```
1h :  Basic surface fields.

1h_gridTsurf:
       sosstsst:long_name = "sea surface temperature" ;
       sosaline:long_name = "sea surface salinity" ;
       sossheig:long_name = "sea surface height" ;


1d: All 3D fields, + atmospheric fluxes + iceberg fluxes.

1d_ICBT.nc
        berg_melt:long_name = "icb melt rate of icebergs" ;
        berg_buoy_melt:long_name = "icb buoyancy component of iceberg melt rate" ;
        berg_eros_melt:long_name = "icb erosion component of iceberg melt rate" ;
        berg_conv_melt:long_name = "icb convective component of iceberg melt rate"

1d_flxT.nc
        somixhgt:long_name = "Turbocline depth (Kz = 5e-4)" ;
        sohefldo:long_name = "Net Downward Heat Flux" ;
        soshfldo:long_name = "Shortwave Radiation" ;
        qns_oce:long_name = "non-solar heat flux at ocean surface (including E-P)" ;
        qns:long_name = "non solar Downward Heat Flux" ;
        solhflup:long_name = "Latent Downward Heat Flux over open ocean" ;
        solwfldo:long_name = "Longwave Downward Heat Flux over open ocean" ;
        sosbhfup:long_name = "Sensible Downward Heat Flux over open ocean" ;
        sowaflup:long_name = "Net Upward Water Flux" ;
        sosfldow:long_name = "Downward salt flux" ;
        wdmp:long_name = "Surface Water Flux: Damping correction" ;
        sohumspe:long_name = "air Specific Humidity" ;
        sotemair:long_name = "Air temperature" ;
        sowapre:long_name = "Total precipitation" ;
        fwfisf:long_name = "Ice shelf melting" ;
        sowinsp:long_name = "wind speed module" ;
        sornf:long_name = "River Runoffs" ;

1d_fwbscalar.nc
       fwprv:long_name = "Fresh Water imbalance" ;

1d_gridT.nc
        e3t:long_name = "T-cell thickness" ;
        votemper:long_name = "temperature" ;
        vosaline:long_name = "salinity" ;

1d_gridTsurf.nc
        sosstsst:long_name = "sea surface temperature" ;
        sosaline:long_name = "sea surface salinity" ;
        sossheig:long_name = "sea surface height" ;
        botpres:long_name = "Sea Water Pressure at Sea Floor" ;
        sosshths:long_name = "thermosteric sea surface height" ;
        sosshhas:long_name = "halosteric sea surface height" ;
        somxl010:long_name = "Mixed Layer Depth (dsigma = 0.01 wrt 10m)" ;

1d_gridU.nc
        e3u:long_name = "U-cell thickness" ;
        vozocrtx:long_name = "ocean current along i-axis" ;
        sozotaux:long_name = "Wind Stress along i-axis" ;

gridUsurf.nc
        vozocrtx:long_name = "ocean surface current along i-axis" ;

1d_gridV.nc
        e3v:long_name = "V-cell thickness" ;
        vomecrty:long_name = "ocean current along j-axis" ;
        sometauy:long_name = "Wind Stress along j-axis" ;

1d_gridVsurf.nc
        vomecrty:long_name = "ocean surface current along j-axis" ;

1d_gridW.nc
        vovecrtz:long_name = "ocean vertical velocity" ;
        voavt:long_name = "vertical eddy diffusivity" ;
        avtiwm:long_name = "internal wave-induced vertical diffusivity" ;

1d_icemod.nc : very buisy  (too much !)
        simsk:long_name = "Fraction of time steps with sea ice" ;
        simsk15:long_name = "Ice mask (0 if ice conc. lower than 15%, 1 otherwise)" ;
        snvolu:long_name = "snow volume" ;
        snthic:long_name = "Snow thickness" ;
        sithic:long_name = "Sea-ice thickness" ;
        sivolu:long_name = "Sea-ice volume per area" ;
        siconc:long_name = "Sea-ice area fraction" ;
        sisali:long_name = "Sea ice salinity" ;
        sitemp:long_name = "Mean ice temperature" ;
        sntemp:long_name = "Mean snow temperature" ;
        sittop:long_name = "temperature at the ice surface" ;
        sitbot:long_name = "temperature at the ice bottom" ;
        sitsni:long_name = "temperature at the snow-ice interface" ;
        sivelu:long_name = "X-component of sea ice velocity" ;
        sivelv:long_name = "Y-component of sea ice velocity" ;
        sivelo:long_name = "Sea-ice speed" ;
        utau_ai:long_name = "X-component of atmospheric stress on sea ice" ;
        vtau_ai:long_name = "Y-component of atmospheric stress on sea ice" ;
        utau_oi:long_name = "X-component of ocean stress on sea ice" ;
        vtau_oi:long_name = "Y-component of ocean stress on sea ice" ;
        sidive:long_name = "Divergence of the sea-ice velocity field" ;
        sishea:long_name = "Maximum shear of sea-ice velocity field" ;
        sistre:long_name = "Compressive sea ice strength" ;
        normstr:long_name = "Average normal stress in sea ice" ;
        sheastr:long_name = "Maximum shear stress in sea ice" ;
        isig1:long_name = "1st principal stress component for EVP rhg" ;
        isig2:long_name = "2nd principal stress component for EVP rhg" ;
        isig3:long_name = "convergence measure for EVP rheology (must be around 1)" ;
        qt_oce_ai:long_name = "total heat flux at the ocean   surface: interface oce-(ice+atm)" ;
        qt_atm_oi:long_name = "total heat flux at the oce-ice surface: interface atm-(ice+oce)" ;
        qtr_ice_top:long_name = "solar heat flux transmitted through the ice surface" ;
        qemp_ice:long_name = "Downward Heat Flux from E-P over ice" ;
        albedo:long_name = "Mean albedo over sea ice and ocean" ;
        hfxcndbot:long_name = "Net conductive heat flux at the ice bottom (neg = ice cooling)" ;
        hfxsensib:long_name = "Net sensible heat flux under sea ice (neg = ice cooling)" ;
        sfxice:long_name = "ice-ocean salt flux from ice growth/melt (neg = growth)" ;
        vfxice:long_name = "ice-ocean mass flux from ice melt/growth (neg = growth)" ;
        vfxsnw:long_name = "ice-ocean mass flux from snw melt/growth (neg = growth)" ;
        siextentn:long_name = "Sea ice extent North" ;
        sivoln:long_name = "Sea ice volume North" ;
        siarean:long_name = "Sea ice area North" ;
        siextents:long_name = "Sea ice extent South" ;
        sivols:long_name = "Sea ice volume South" ;
        siareas:long_name = "Sea ice area South" ;

1m: Same fields as 1d output. They were computed by XIOS with no extra cost. Doing so, avoid the computation of monthly mean at the post processing step, hence allow a faster workflow.  
In addition, 1m output also have the average of second order moments computed at each time step.

1m_PRODU.nc
        vout:long_name = "product_of_sea_water_x_velocity_and_temperature" ;
        vous:long_name = "product_of_sea_water_x_velocity_and_salinity" ;
        vozocrtx_sqd:long_name = "product_of_sea_water_x_velocity_and_sea_water_x_velocity" ;

1m_PRODV.nc
        vovt:long_name = "product_of_sea_water_y_velocity_and_temperature" ;
        vovs:long_name = "product_of_sea_water_y_velocity_and_salinity" ;
        vomecrty_sqd:long_name = "product_of_sea_water_y_velocity_and_sea_water_y_velocity"

1m_PRODW.nc
        vowt:long_name = "product_of_upward_sea_water_velocity_and_temperature" ;
        vows:long_name = "product_of_upward_sea_water_velocity_and_salinity" ;


1y :  Same as 1m when annual segment of production were possible. This turned to be impossible for recent years, because of the OBS module that ran out of memory due to the large
amount of data .  In this latter case, annual means were computed from daily monthly means. 
```
* _For WP2 experiments:_
Similar to WP1 except than the 3-d fields are saved at 5d frequency instead of 1d.

## 3.3 Secondary outputs shared on Jean Zay
The secondary outputs are computed from the primary outputs _after_ run time. Because some computations can take time and produce large amount of data, it is good practice to make those secondary datasets available to other members of the IMHOTEP projects, as long as they are documented.

Below is the list of secondary outputs available on the `/common/` directory of the project on the `$STOREDIR`. __Any other contribution welcome !!__
```
cd /gpfsstore/rech/cli/commun/IMHOTEP
tree -L 1
.
|-- CMEMS-SSS
|-- ENSTATS_1d
|-- ENSTATS_1m
|-- ENSTATS_1y
|-- eORCA025.L75-IMHOTEP.02
|-- eORCA025.L75-IMHOTEP.SC-S
|-- ESA-SSS
|-- MOCZ
`-- SMOS-L3
```

* `MOCZ` is the Meridional Overturning Circulation (z coordinate) computed from the cdftool `cdfmoc` (see script `compute_mocz_1m_ens.sh`below):
```
cd /gpfsstore/rech/cli/commun/IMHOTEP/MOCZ
tree -L 1
.
|-- 1m
|   |-- EGAI
|   |-- ES
|-- compute_mocz_1m_ens.sh
```

* `ENSTATS_1y`is the directory where ensemble stats at 1y frequency were computed (only sss at the moment)
```
cd /gpfsstore/rech/cli/commun/IMHOTEP/ENSTATS_1y
tree -L 1
.
|-- EAI
|-- EGAI
|-- ensstats_1Y.sh
`-- ES
```

* Same for `ENSTATS_1m` and `ENSTATS_1d` at 1m and 1 d frequency. Note that for 1D, only a few years were computed so far.

* ESA-CCI obs product for Sea Surface Salinity: `/gpfsstore/rech/cli/commun/IMHOTEP/ESA-SSS`

* to be continued !


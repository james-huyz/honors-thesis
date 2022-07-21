# honors-thesis
James Hu's planetary geoscience project for the degree of Bachelor of Science with Honors, Department of the Geophysical Sciences, University of Chicago, 2022

## Title of paper
Constraining Mars obliquity in the Amazonian and Hesperian periods using elliptic crater orientations

## Abstract of paper
The obliquity of Mars oscillates chaotically over >100 Ma time scales, meaning that its historical obliquity is not well characterized through physical simulations. Mars’s past obliquity governs its past climate, including its surface volatile dynamics, atmospheric collapse, and low-latitude ice migration. This study attempts to constrain Mars’s past obliquity by adapting an existing technique that compares the azimuth distributions of simulated craters under different obliquity scenarios with those of actual craters. We traced 1,678 elliptic craters collectively from the late Amazonian volcanic (lAv) and Amazonian–Hesperian volcanic (AHv) units and compared their azimuth distributions with those of $10^6$ simulated craters per obliquity scenario. We then performed a $\chi^2$ test to measure the extent of mismatch between the simulated data from each obliquity scenario and the actually collected data. We found that the mean obliquities associated with the lAv unit, representing the past ~0.9 Ga, and AHv unit, representing the past ~2.0 Ga, were 68° (60.8°–71.3° standard error interval) and 8° (6.2°–10.6° standard error interval), respectively. Applying 1,000 random inter-analyst error perturbations, we found (in our median result) that the mean obliquities associated with the lAv and AHv units were 60° (57.2°–64.5° standard error interval) and 16° (11.8°–17.9° standard error interval), respectively. This result’s geologic implications include that, relative to today (~25° obliquity), Mars saw, over the past ~2.0 Ga, more frequent polar glaciation, polar atmospheric collapse, and desiccation of deep aquifers and saw, over the past ~0.9 Ga, greater sublimation of water ice, the migration to lower latitudes of water ice, higher water vapor pressure, and more frequent polar dust storms. Future work may collect a larger set of craters, apply this study’s methods to Holo et al. (2018)’s dataset and vice versa, account for poke-throughs of older craters on younger terrain, and investigate why our method implies an unphysical result for the intervening ~1.0 Ga period between the ages of the units.

## MATLAB script descriptions
**hu_01_get_crater_data.m**: Read crater coordinate data from shapefiles and trace ellipses using Gal (2003)'s script. Export data as in five columns (latitude, azimuth, diameter, ellipticity, longitude).

**hu_02_get_azimuth_diffs.m**: Identify the coordinates of second analyst's traced craters; generate list of craters in original traced set that are close to those in second; if there are multiple craters in this list choose the one with the highest resemblance; check how different the craters are in terms of azimuth (add this to an array); make an array with crater azimuth difference.

**hu_03_get_pois.m**: This is the first script in Sam Holo's forward model for the effect of obliquity on elliptic crater orientations. The input file is name '14mag_imp_info' and contains an ensemble of encounter inclinations and speeds from n-body output. The output of this script is an ensemble of elliptic crater locations and diameters, as well as impactor velocity vectors at the time of impact and the impact angle. This output can be ingested and processed by apply_obliquity.m.

**hu_04_apply_obliquity.m**: This is the second script in Sam Holo's forward model for the effect of obliquity on elliptic crater orientations. It takes the output ensemble from get_pois.m (get "pre-obliquity-impacts"), applies each integer degree obliquity to the ensemble, and saves the key parameters: latitude, diameter, and orientation of the elliptic craters.

**hu_05_apply_lat_dist.m**: Modify the output of Sam Holo's forward model to conform to the latitudinal distribution of actually observed craters.

**hu_06_get_mismatch.m**: Calculate the degree of mismatch (rdc chi-2 statistic) between the crater orientation probability distribution function of each constant-obliquity simulation (0-90°) and the crater orientation probability distribution function as determined from the actually observed craters. Then determine the constant obliquity with the lowest mismatch.

**hu_07_plot_age_obliquity.m**: Plot the past and present obliquity of Mars, numerically integrated and statistically constrained, from multiple sources.

**hu_08_perturb_data_iaerr.m**: Create inter-analyst-perturbed crater azimuth arrays.

**hu_09_get_mismatch_var_ecrit.m**: Redo step 6 (with simplifications) for various e_crit values, i.e., 1.00, 1.05, 1.10, and 1.15.

**hu_10_plot_distributions.m**: Plot distributions of crater latitudes, azimuths, and ellipticities.

## Acknowledgements
My adviser Edwin Kite (2021-22) and his former postdoc Sam Holo (2018)

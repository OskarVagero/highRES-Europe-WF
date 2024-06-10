# Philosophical views of justice and their implications in energy systems modelling

[![Documentation Status](https://readthedocs.org/projects/highres-europe-wf/badge/?version=latest)](https://highres-europe-wf.readthedocs.io/en/latest/?badge=latest)

This repository contains the model framework for the paper titled _Philosophical views of justice and their implications in energy systems modelling_ and information on how to re-create the results.

The modelling framework is based on [highRES](https://github.com/highRES-model/highRES-Europe-WF). Here we describe the main differences from previously published version. Documentation is available [here](https://highres-europe-wf.readthedocs.io/en/latest/).

## Abstract

What constitutes socially just or unjust energy systems or transitions can be derived from the philosophy and theories of justice. Assessments of justice and utilising them in modelling lead to great differences based on which justice principles are applied. From the limited research so far published in the intersection between energy systems modelling and justice, we find that comparisons between the two principles of utilitarianism and egalitarianism dominate in assessments of distributive justice, with the latter most often considered representing a 'just energy system'. The lack of recognition of alternative and equally valid principles of justice, resting on e.g. capabilities, responsibilities and/or opportunities, leads to a narrow understanding of justice that fails to align with the views of different individuals, stakeholders and societies. More importantly, it can lead to the unjust design of future energy systems and energy systems analysis.

In this work, we contribute to the growing amount of research on justice in energy systems modelling by assessing the implications of different philosophical views on justice on modelling results. Through a modelling exercise with a power system model for Europe (highRES), we explore different designs of a future net-zero European energy system, and its distributional implications based on the application of different justice principles. In addition to the utilitarian and egalitarian approach, we include, among others, principles of 'polluters pay' and 'ability-to-pay', which take historical contributions of greenhouse gas emissions and the socio-economic conditions of a region into account.

We find that socially just energy systems look significantly different depending on the justice principles applied. The results may stimulate a greater discussion among researchers on the implications of different constructions of justice in modelling, expansion of approaches, and demonstrate the importance of transparency and assumptions when communicating such results.

## Installation
Although we have tried to generalise the workflow, it does require some manual configuration with the proper paths and folder structure. 

1. Clone the repository
2. Install a minimal snakemake environment with mamba `mamba create -c bioconda -c conda-forge -n snakemake snakemake-minimal pandas zstd`
3. Activate the snakemake environment `conda activate snakemake`
4. Download the required data from [Zenodo](www.google.com)
5. Configure the workflow with the Snakefile and config.yaml so that the paths fit your setup. 
6. Run the snakemake workflow `snakemake --cores 16 --use-conda

## Model description
highRES has been used in a number of other peer-reviewed papers. [Price and Zeyringer, 2022](https://doi.org/10.1016/j.softx.2022.101003) is the associated software publication, whereas [Price et al., 2023](https://doi.org/10.1016/j.energy.2022.125450) is the most recent publication within the European framework. 

### Spatial extent and resolution
highRES is able to run at different spatial resolutions, based on the purpose of the analysis. For example, [Price et al., 2023](https://doi.org/10.1016/j.energy.2022.125450) have analysed the UK electricity system, and as such represent the UK at a higher spatial resolution, while countries located further away from the UK are clustered together. [Roithner and Hvidsten](https://www.nordicenergy.org/project/the-role-of-hard-to-reach-energy-users-in-reaching-balticsnordics-climate-targets-a-multidisciplinary-analysis/) have focused on Norway. For our purposes, we focus on the wider European electricity system, and model each country as one node.

The baseline for cross-border transmission capacities is based on reported historical interconnection from ENTSO-E as well planned new interconnectors from figure 3.1 in the [Ten-Year Network Development Plan 2020](https://eepublicdownloads.blob.core.windows.net/public-cdn-container/tyndp-documents/TYNDP2020/FINAL/entso-e_TYNDP2020_Main_Report_2108.pdf). To allow some flexibility towards 2050, we allow for a three-fold increase in capacities.

<img src="https://github.com/OskarVagero/highRES-Europe-WF/blob/MENOFS/analysis/figures/transmission_lines_MENOFS.png" width=50% height=50%>

### Weather and demand data
Weather data for the performance of variable renewable energy is generated through the xarray-based Python library Atlite [80], which converts climate data (in our case [ERA5 weather-reanalysis from ECMWF](https://doi.org/10.1002/qj.3803) ) to time series in a 30x30km grid cell. With investments in variable renewable energy at a country level, as in our case, the grid cells form an average for the full spatial extent of each country. To address the fact that the average capacity factor for solar PV, onshore and offshore wind will be reduced by poorly-performing grid cells (e.g. with low wind speeds) which in reality would not be considered for the deployment of these technologies, we apply a so-called cut-off factor. The cut-off factor excludes grid cells with an average capacity factor lower than a set threshold. For solar, onshore and offshore wind, this threshold is set to 0.09, 0.15 and 0.20 respectively, based on [ref]. 

Although previous studies have shown the issue of weather year variability (see e.g. [Grochowicz et al., 2023](https://doi.org/10.1016/j.eneco.2022.106496), [Pfenninger and Staffell](https://doi.org/10.1016/j.energy.2016.08.060) or [Staffell and Pfenninger](https://doi.org/10.1016/j.energy.2017.12.051) and that using a single year of weather data may largely skew the results, we only utilise historical data from 2010 as the main focus of this work on differences in analysis given different interpretations of justice. 

The model balances supply and demand at an hourly resolution for all nodes in the model. Demand time series are originally based on historical data from the [European Network of Transmission System Operators for Electricity (ENTSO-E) Transparency Platform](https://transparency.entsoe.eu/dashboard/show), but need to be adjusted to account for inconsistencies and missing data. This has previously been done by [van der Most](https://doi.org/10.1016/j.rser.2022.112987), who used climate data and applied a logistic smooth transmission regression (LSTR) model to the ENTSO-E dataset to correlate historical electricity demand to temperature and generate daily electricity demand for a set of European countries. Subsequently, [Frysztacki, van der Most and Neumann](https://doi.org/10.5281/zenodo.10820928) used hourly profiles from the [Open Power Systems Database](https://doi.org/10.25832/time_series/2020-10-06) to disaggregate the daily electricity demand to an hourly resolution, on a country level. We further take this data and scale it by a factor of two, based on a suggested possible increase in electricity demand by (source), while leaving the shape of the load curve untouched. 


### Techno-economic assumptions




Any kind of questions can be directed to oskar.vagero@its.uio.no.
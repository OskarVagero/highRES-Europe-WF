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

Any kind of questions can be directed to oskar.vagero@its.uio.no.
# README and Guidance OpportunityMap Preprocessing

This readme follows the template created by Social Science Data Editors. See [References](#references).

## Overview

<figure>

<img src="images/Opportunity%20Map%20Project%20Pipeline.png" alt="OpportunityMap Pipeline"/>

<figcaption aria-hidden="true">

OpportunityMap Pipeline

</figcaption>

</figure>

The code in this replication package generates the samples datasets used to produce the results results shown on the interactive websites OpportunityMap.nl (for the Dutch version see KansenKaart.nl) and OpportunityGap.nl (for the Dutch version see KansenKloof.nl).

## What are OpportunityMap NL and OpportunityGap NL?

[OpportunityMap](https://opportunitymap.nl/) and [OpportunityGap](https://opportunitygap.nl/) form part of a research project by the [Netherlands Opportunity Lab](https://github.com/Netherlands-Opportunity-Lab/) which studies intergenerational mobility in the Netherlands. The aim of this research project is to document to what extent the circumstances in which a child grows up are associated with outcomes from birth through adulthood. Child sex, migration background parental income, wealth, education, the number of parents in the household, and the place where a child grows up, are considered predictor variables, which measure circumstances beyond a child’s control.

The scripts in this replication package create the sample datasets used for the [OpportunityMap](https://opportunitymap.nl/) and [OpportunityGap](https://opportunitygap.nl/) analyses which are described [here](https://github.com/sodascience/kansenkaart_analysis) and [here](https://github.com/Netherlands-Opportunity-Lab/Kansenkloof-NL-Analysis), respectively.

In total we study 91 (including 20 correlates) outcomes that are measured at birth and in the final (eighth) grade of primary school, and at ages 16, 21, and 34-35. These data can be used to provide granular insights into how, when, and where the opportunity gap in the Netherlands opens up.

## Data Availability and Provenance Statements {#data-availability-and-provenance-statements}

The analysis combines several Dutch administrative data registers. The data use is subject to the European Union’s General Data Protection Regulation (GDPR) and Dutch law. The research is conducted within the secure remote access microdata CCenvironment of Statistics Netherlands.

Researchers interested in obtaining access to the data employed in this analysis are required to submit a research proposal, a publication plan, a GDPR-ground and purpose, and an application form, Access will be granted only to institutions with a valid authorization by Statistics Netherlands. All relevant information on how to obtain data access through Statistics Netherlands and institutional authorization can be found [here](https://www.cbs.nl/en-gb/our-services/customised-services-microdata/microdata-conducting-your-own-research/applying-for-access-to-microdata).

### License for Code

The code is licensed under a GPL v3 license. See LICENSE.txt for details.

Over and above the legal restrictions imposed by this license, if you use this software for an academic publication then you are obliged to provide proper attribution. This can be to this code directly,

XXXX (Zenodo)

### Summary of Availability

-   Some data **cannot be made** publicly available.

### Data Source

All the results in the paper use confidential microdata from the Statistics Netherlands (CBS).

To gain access to the microdata, follow the directions in section [Data Availability and Provenance Statements](#data-availability-and-provenance-statements).

To replicate the analyses, you must request the following datasets from Statistics Netherlands.

-   Sample construction: gbapersoontab; gbaadresobjectbus; kindoudertab; vslpostcodebus; vslgwbtab

-   Predictors: IPI; inpatab; inhatab; vehtab; gbapersoontab; gbahuishoudensbus

-   Outcomes: inpatab; IPI; hoogsteopltab; spolisbus; secmbus; zvwzorgkostentab; vehtab; eigendomtab; schtab; kindoudertab; levcyclwoonnietwoonbus;jdgbeschermbus; inschrwpotab; doodoorztab; gbaoverlijdentab.

### Samples

The Opportunity Map Preprocessing generates multiple samples, each defined by the age at which outcomes are measured. This is reflected in the sample names. A more detailed description of samples can be found [here](./resources/documentation/Samples.md).

| Outcome Group | Description |
|-----------------------|------------------------------------------------|
| `newborns` | Outcomes measured at/around birth |
| `prim8` | Outcomes measured in the last year of primary school (grade 8) |
| `age16` | Outcomes measured at age 16 |
| `age21` | Outcomes measured at age 21 |
| `age35` | Outcomes measured at age 34-35 |

### Code

Code for the samples creation is provided as part of this replication package. It is available [here]((Zenodo%20link)). Description follows in [Description of scripts](#description-of-scripts).

## Dataset list

| Location | List of data files | Notes |
|------------------|---------------------------|---------------------------|
| /resources | Consumentenprijzen\_\_prijsindex_2015_100_07012021_123946.csv | Consumer price index with base year 2015 |
|  | Gemeenten en COROP vanaf 1981.xlsx | Historical list of municipalities and COROP regions |
|  | Hoftiezer_Geboortegewicht curves.xlsx | Birth weight reference curves by Hoftiezer et al. |
|  | LANDAKTUEELREF10.sav | CBS land classification reference data |
|  | create_cbs_countries.R | Script to generate CBS country classifications |
|  | gemeenten_corop_1981.xlsx | Duplicate or cleaned version of COROP-municipality mapping |
|  | r_packages_cbs.csv | List of R packages used for CBS scripts |
|  | r_version_cbs.txt | R version used for CBS-related analysis |
|  | set_cbs_versions.R | Script to define CBS version settings |
|  | sources.txt | Text file listing data sources |
|  | vo_advisering.xlsx | Data on secondary school advising (VO advisering) |

## Computational requirements

### Software Requirements

-   R 3.4.3

    -   renv (1.1.4): Run renv::restore() to install the right versions of all dependencies

### Memory and Runtime Requirements

#### Summary

Approximate time needed to reproduce the analyses on a standard (2025) desktop machine:

-   Not feasible to run on a desktop machine, as described below.

#### Details

The code was last run on the ODISSEI Secure Supercomputer (OSSC).

Computation took \### hours.

## Description of scripts {#description-of-scripts}

### **Sample Creation**

To create a sample dataset use `create_cohort_data.R`, change the desired input configuration to one of the following:

-   `config/newborns.yml`

-   `config/prim8.yml`

-   `config/age16.yml`

-   `config/age21.yml`

-   `config/age25.yml`,

    and run the entire file. The sample dataset will be written to the scratch folder.

### **Flowchart Sample Creation**

<figure>

<img src="images/Opportunity%20Map%20Preprocessing%20Flowchart.png" alt="OpportunityMap Preprocessing Flowchart"/>

<figcaption aria-hidden="true">

OpportunityMap Preprocessing Flowchart

</figcaption>

</figure>

### **1. Configuration**

The configuration files for each of the samples can be found in the [`config`](./config) folder. Here sample-dependent values are defined, such as:

-   Sample name and birthdate range filters (`child_birth_date_min` and `child_birth_date_max`)

-   Residency rules, including age ranges and slack days for registration gaps (`child_live_age`, `child_live_slack_days`)

-   Measurement ages for childhood address and outcome definitions (`childhood_home_age`, `outcome_age`) - Reference years for parental income and wealth data

-   Other year ranges for sample-specific outcomes

-   CPI base year used for deflating income

-   File paths to raw CBS microdata and auxiliary resources such as price indices, migration codes, and regional mappings

### 2. **Pipeline**

Here, the pipeline steps are outlined in short. For a more detailed description see [Pipeline description](./resources/documentation/COMPONENTS.md)

#### 1. **Define sample**

-   Select the cohort based on the filtering birthdate criteria
-   Match to parents
-   Link to childhood home address
-   Add geographical area variables to the address
-   Write `01_cohort.rds` to the scratch folder

#### 2. **Add predictors**

-   Add parent income and define parental income rank
-   Add parent wealth and define parental wealth rank
-   Add parent education for newborns and prim8 samples
-   Create third generation migration background variable and define migration background
-   Add type of household data
-   Write `02_predictor.rds` to the scratch folder

#### 3. **Add outcomes**

-   Add sample-specific outcomes
-   Write `03_outcomes.rds` to the scratch folder

#### 4. **Post-processing**

-   Select variables of interest
-   Define income and wealth groups based on ranks
-   Write `kansenkaart_data.rds` to the scratch folder

## Instructions to Replicators

-   Clone this repository to a folder on your machine
-   Edit the file locations in the `config` files to point to the right files
-   Open the `.Rproj` file, install the `renv` package
-   Run `renv::restore()` to install the right versions of all dependencies

# References {#references}

Lars Vilhuber, Connolly, M., Koren, M., Llull, J., & Morrow, P. (2022). A template README for social science replication packages (v1.1). Social Science Data Editors. <https://doi.org/10.5281/zenodo.7293838>

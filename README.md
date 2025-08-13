# README and Guidance OpportunityMap Preprocessing

This readme follows the template created by Social Science Data Editors. See [References](#references).

## Overview

The code in this replication package generates the samples datasets used to produce the results results shown on the interactive websites OpportunityMap.nl (for the Dutch version see KansenKaart.nl) and OpportunityGap.nl (for the Dutch version see KansenKloof.nl).

## What are OpportunityMap NL and OpportunityGap NL?

[OpportunityMap](https://opportunitymap.nl/) and [OpportunityGap](https://opportunitygap.nl/) form part of a research project by the [Netherlands Opportunity Lab](https://github.com/Netherlands-Opportunity-Lab/) which studies intergenerational mobility in the Netherlands. The aim of this research project is to document to what extent the circumstances in which a child grows up are associated with outcomes from birth through adulthood. Child sex, migration background parental income, wealth, education, the number of parents in the household, and the place where a child grows up, are considered predictor variables, which measure circumstances beyond a child’s control.

The scripts in this replication package create the sample datasets used for the [OpportunityMap](https://opportunitymap.nl/) and [OpportunityGap](https://opportunitygap.nl/) analyses which are described [here](https://github.com/sodascience/kansenkaart_analysis) and [here](https://github.com/Netherlands-Opportunity-Lab/Kansenkloof-NL-Analysis), respectively.

In total we study 91 (including 20 correlates) outcomes that are measured at birth and in the final (eighth) grade of primary school, and at ages 16, 21, and 34-35. These data can be used to provide granular insights into how, when, and where the opportunity gap in the Netherlands opens up.

## Data Availability and Provenance Statements

The analysis combines several Dutch administrative data registers. The data use is subject to the European Union’s General Data Protection Regulation (GDPR) and Dutch law. The research is conducted within the secure remote access microdata CCenvironment of Statistics Netherlands.

Researchers interested in obtaining access to the data employed in this analysis are required to submit a research proposal, a publication plan, a GDPR-ground and purpose, and an application form, Access will be granted only to institutions with a valid authorization by Statistics Netherlands. All relevant information on how to obtain data access through Statistics Netherlands and institutional authorization can be found [here](https://www.cbs.nl/en-gb/our-services/customised-services-microdata/microdata-conducting-your-own-research/applying-for-access-to-microdata).

### Summary of Availability

-   Some data **cannot be made** publicly available.

### License for Data

The results are licensed under the CC BY-SA 4.0. See LICENSE.txt for details.

Over and above the legal restrictions imposed by this license, if you use the results for an academic publication then you are obliged to provide proper attribution. This can be to this code directly,

XXXX (Zenodo)

or to the paper that describes it

Lam, H., Ravesteijn, B., van de Kraats, C. & van Kesteren, E.-J. (2025). How, When, and Where Does the Opportunity Gap Open Up in the Netherlands? \[Unpublished manuscript\].

or (ideally) both.

### License for Code

The code is licensed under a GPL v3 license. See LICENSE.txt for details.

Over and above the legal restrictions imposed by this license, if you use this software for an academic publication then you are obliged to provide proper attribution. This can be to this code directly,

XXXX (Zenodo)

## Data and Sources

All the results in the paper use confidential microdata from the Statistics Netherlands (CBS).

To gain access to the microdata, follow the directions in section [Data Availability and Provenance Statements](#data-availability-and-provenance-statements).

### Microdata files (Confidential)

| Category | Dataset Name | Notes |
|------------------------|------------------------------|-------------------|
| Sample Construction | `gbapersoontab` | Personal characteristics from GBA |
|  | `gbaadresobjectbus` | Residential address history |
|  | `kindoudertab` | Parent-child relationships |
|  | `vslpostcodebus` | Neighborhood-level socioeconomic data |
|  | `vslgwbtab` | Neighborhood classification |
| Predictors | `IPI` | Integrated Personal Income |
|  | `inpatab` | Personal income |
|  | `inhatab` | Household income |
|  | `vehtab` | Assets and debts |
|  | `gbahuishoudensbus` | Household composition |
| Outcomes | `hoogsteopltab` | Highest obtained education level |
|  | `spolisbus` | Insurance data |
|  | `secmbus` | Secondary education outcomes |
|  | `zvwzorgkostentab` | Health care costs |
|  | `eigendomtab` | Home ownership |
|  | `schtab` | School-level data |
|  | `levcyclwoonnietwoonbus` | Life course and housing transitions |
|  | `jdgbeschermbus` | Youth protection measures |
|  | `inschrwpotab` | Enrollment in secondary vocational education (MBO) |
|  | `doodoorztab` | Causes of death |
|  | `gbaoverlijdentab` | Date of death and demographics at death |

These files correspond to the ones that can be found in [CBS microdata catalogue](https://www.cbs.nl/nl-nl/onze-diensten/maatwerk-en-microdata/microdata-zelf-onderzoek-doen/catalogus-microdata) (only available in Dutch).

### Auxiliary Data Files (Provided)

| Location | File name | Description | Source |
|------------------|-------------------|------------------|------------------|
| /resources | Consumentenprijzen\_\_prijsindex_2015_100_07012021_123946.csv | Consumer price index with base year 2015 |  |
|  | Gemeenten en COROP vanaf 1981.xlsx | Historical list of municipalities and COROP regions |  |
|  | Hoftiezer_Geboortegewicht curves.xlsx | Birth weight reference curves by Hoftiezer et al. |  |
|  | LANDAKTUEELREF10.sav | CBS land classification reference data |  |
|  | gemeenten_corop_1981.xlsx | Duplicate or cleaned version of COROP-municipality mapping |  |
|  | r_packages_cbs.csv | List of R packages used for CBS scripts |  |
|  | r_version_cbs.txt | R version used for CBS-related analysis |  |
|  | sources.txt | Text file listing data sources |  |
|  | vo_advisering.xlsx | Data on secondary school advising (VO advisering) |  |

## Description of Samples

The Opportunity Map Preprocessing generates multiple samples, each defined by the age at which outcomes are measured. This is reflected in the sample names. A more detailed description of samples can be found [here](./resources/documentation/Samples.md).

| Sample | Birth Years | Outcome Age / Timing | Address Reference Age | Parental Income Period | Parental Education Timing | Outcome Timing | Notes |
|---------|---------|---------|---------|---------|---------|---------|---------|
| `newborns` | 1999–2010 (S1), 2011–2022 (S2) | At birth | At birth | 2014–2018 (both samples) | At birth | At birth | Includes stillbirths; address at birth |
| `prim8` | 2003–2006 (S1), 2009–2011 (S2) | Grade 8 (around age 12) | Age 10 | 2009–2013 (S1), 2014–2018 (S2) | At age 10 | In 8th grade (primary school) |  |
| `age16` | 2003–2007 | Age 16 | Age 15 | 2014–2018 | \- | At age 16 |  |
| `age21` | 1998–2002 | Age 21 | Age 15 | 2014–2018 | \- | At age 21 |  |
| `age35` | 1984–1988 | Age 34–35 | Age 15 | 2003–2007 | \- | Age 34–35 |  |

### How to re-create

Code for the samples creation is provided as part of this replication package. It is available [here]((Zenodo%20link)). Description follows in [Description of scripts](#description-of-scripts).

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

## Description of scripts

### Auxiliary Scripts (Provided)

| Script Name | Purpose |
|-------------------------|-----------------------------------------------|
| `create_cbs_countries.R` | Generates CBS-style country classification tables |
| `set_cbs_versions.R` | Configures version control for CBS files |

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
<img src="images/Opportunity%20Map%20Preprocessing%20Flowchart.png" alt="OpportunityMap Preprocessing Flowchart" />
<figcaption aria-hidden="true">OpportunityMap Preprocessing Flowchart</figcaption>
</figure>

### 1. **Configuration**

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

In this step, we select the individuals from the register that form our samples.

-   Define cohort which consists of individuals registered in the Netherlands and born within a specific birth date interval (`child_birth_date_min` - `child_birth_date_max`)\* (GBAPERSOONTAB).

    -   \*For samples for which we analyze a number of classroom composition outcomes, the birthdate range is increased by 2 years on both sides to include potential classmates.

-   Match individuals to their legal parents (KINDOUDERTAB). We exclude individuals who cannot be matched to their legal parents.

-   Link individuals to their childhood home address based on `childhood_home_age` (GBAADRESOBJECTBUS). We exclude individuals who cannot be linked to their childhood home address.

    -   In samples for which we analyze youth protection outcome, we additionally link individuals to their birth address

-   Add geographical area variables (`postcode3`, `postcode4`(VSLPOSTCODEBUS), `municipality_code`(VSLGWBTAB), `neighborhood_code`, `corop_code` ([`gemeenten_corop_1981.xlsx`](https://github.com/Netherlands-Opportunity-Lab/KansenKaart-Preprocessing-fork/blob/resources/gemeenten_corop_1981.xlsx))) based on childhood address. We exclude individuals whose childhood address cannot be linked to a municipality or 4-digit postcode.

    -   Geographical location definitions in the Netherlands can vary from year to year. Therefore, we use a specific target date (`postcode_target_date` & `gwb_target_date`) to determine the geographical location

-   Write the resulting sample (`01_cohort.rds)` dataset to *the scratch folder.*

-   At each step we record the sample sizes.

#### 2. **Add predictors**

In this step, we incorporate variables from various microdata sets to the sample, which serve as predictors for our estimates: parental income/wealth/education\*, migration background, household composition

\*parental education is only added to newborns and prim8 samples due to data availability

-   We check whether the parents meet the residency requirement. We exclude the children whose parents did not live continuously in the Netherlands between the years in which we define parental income of the children allowing for a number of slack days defined by `child_live_slack_days`.

-   Parental income: We obtain information on parental income during individual’s childhood from IPI (\<2011) and INPATAB (≥2011). Parental income represents the average pretax income of the mother and/or father combined over a specific period interval (`parent_income_year_min` - `parent_income_year_max`). We exclude individuals whose parents do not have observable income within the specified interval.

    -   We apply several restrictions to the income definition:

        1\. Income values of 999999999 (indicating a household with no perceived income) or negative income values (below 0) are converted to NA (not available).

        2\. Income values above the specified censoring limit in euros (`income_censoring_value`) are truncated.

        3\. Parental income is adjusted for inflation using the consumer price index (CPI) from CBS Statline (cpi_base_year).

    -   We compute parental income rank (in percentile) in the parental income distribution.

-   \*For the samples for which we analyze classroom composition outcomes, we split the class sample and write it to `class_cohort.rds` in the /scratch folder.

-   Parental wealth: We obtain information on parental wealth during individual’s childhood from the VEHTAB. Parental wealth represents the average pretax wealth of the household’s head (if these are different for parents, we use the total) combined over a specific period interval (`parent_wealth_year_min` - `parent_wealth_year_max`).

    -   The same restrictions applied to parental income are also imposed on parental wealth.

    -   We compute parental wealth rank (in percentile) in the parental income distribution.

-   \*Parental education: We obtain information on the parents’ highest achieved level of education during individual’s childhood from HOOGSTOPLTAB. We categorize education into 3 levels: University, Higher Professional Education, and Other (including NA). The parental education level is determined by the highest educational attainment between the father and the mother.

    -   \*For newborns and prim8 samples

    -   This is due to the availability of data on parental education, which began in 1983 for WO, 1986 for HBO, and 2004 for MBO (intermediate vocational education).

-   We introduce a third generation to the variable `GBAGENERATIE` from the GBAPERSOONTAB microdata for individuals in the cohort. If a child is native (autochtoon) and at least one of their parents is a second-generation immigrant (tweede generatie allochtoon), we reclassify the child’s generation as a third-generation immigrant (derde generatie allochtoon). Essentially, we change the child’s generation from native to third generation if at least one parent is a second-generation immigrant and the child is native.

    -   For children who are third-generation immigrants, we recode their origin (variable `GBAHERKOMSTGROEPRING`) as follows:

        1.  If the child is third generation and the father’s origin is native, the child adopts the mother’s origin.
        2.  If the child is third generation and the mother’s origin is native, the child adopts the father’s origin.
        3.  If the child is third generation and both parents’ origins are non-native, the child adopts the mother’s origin.

-   Migration background: We obtain child’s migration background data from the GBAPERSOONTAB. We categorize migration background into 6 levels:

    1.  No Migration Background
    2.  Turkey
    3.  Morocco
    4.  Suriname
    5.  Dutch Caribbean
    6.  With Migration Background

-   Type of household: We obtain the type of household a child was growing up in from GBAHUISHOUDENSBUS. We categorize this into 2 levels: Single Parent and Two Parents.

-   Write the resulting sample (`02_predictors.rds)` dataset to *the scratch folder.*

-   At each step we record the sample sizes.

#### 3. **Add outcomes**

In this step, we connect sample-specific outcomes to the samples.

-   We check whether the individual meets the residency requirement. We exclude the children who did not live continuously in the Netherlands within a specified period (`child_live_start` - `child_live_end`) allowing for a number of slack days defined by `child_live_slack_days`.

-   We add sample-specific outcomes. Further details regarding the outcomes used for each cohort can be found [here](resources/documentation/Samples.md).

-   Write the resulting sample (`03_outcomes.rds)` dataset to *the scratch folder.*

-   At each step we record the sample sizes.

#### 4. **Post-processing**

In this step, we select variables from the created sample data sets that are relevant for our estimates.

-   Categorize individuals into income (wealth) groups based on parental income (wealth ) percentile:

    1.  15 ≤ Percentile ≤ 35: “Low”
    2.  40 ≤ Percentile ≤ 60: “Mid”
    3.  65 ≤ Percentile ≤ 85: “High”

-   Categorize individuals into income (wealth) distribution’s tail groups based on the same percentile distribution:

    1.  0 ≤ Percentile ≤ 20: “Very Low”
    2.  80 ≤ Percentile ≤ 100: “Very High”

-   Write sample dataset `sample-name_cohort.rds` to the scratch folder.

## Instructions to Replicators

-   Clone this repository to a folder on your machine
-   Edit the file locations in the `config` files to point to the right files
-   Open the `.Rproj` file, install the `renv` package
-   Run `renv::restore()` to install the right versions of all dependencies

# References

Lars Vilhuber, Connolly, M., Koren, M., Llull, J., & Morrow, P. (2022). A template README for social science replication packages (v1.1). Social Science Data Editors. <https://doi.org/10.5281/zenodo.7293838>

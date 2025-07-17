# OpportunityMap preprocessing components

To create the samples datasets, we utilize the OpportunityMap preprocessing pipeline, which consists of four components. Below, we provide a detailed description of these four components.

## 1. Define sample

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

[!NOTE] Both parent and child residency requirements are checked on later stages. Why?

## 2. Add predictors

In this step, we incorporate variables from various microdata sets to the sample, which serve as predictors for our estimates: parental income/wealth/education\*, migration background, household composition

\*parental education is only added to newborns and prim8 samples due to data availability

-   We check whether the parents meet the residency requirement. We exclude the children whose parents did not live continuously in the Netherlands between the years in which we define parental income of the children allowing for a number of slack days defined by `child_live_slack_days`.

-   Parental income: We obtain information on parental income during individual's childhood from IPI (\<2011) and INPATAB (≥2011). Parental income represents the average pretax income of the mother and/or father combined over a specific period interval (`parent_income_year_min` - `parent_income_year_max`). We exclude individuals whose parents do not have observable income within the specified interval.

    -   We apply several restrictions to the income definition:

        1\. Income values of 999999999 (indicating a household with no perceived income) or negative income values (below 0) are converted to NA (not available).

        2\. Income values above the specified censoring limit in euros (`income_censoring_value`) are truncated.

        3\. Parental income is adjusted for inflation using the consumer price index (CPI) from CBS Statline (cpi_base_year).

    -   We compute parental income rank (in percentile) in the parental income distribution.

-   \*For the samples for which we analyze classroom composition outcomes, we split the class sample and write it to `class_cohort.rds` in the /scratch folder.

-   Parental wealth: We obtain information on parental wealth during individual's childhood from the VEHTAB. Parental wealth represents the average pretax wealth of the household's head (if these are different for parents, we use the total) combined over a specific period interval (`parent_wealth_year_min` - `parent_wealth_year_max`).

    -   The same restrictions applied to parental income are also imposed on parental wealth.

    -   We compute parental wealth rank (in percentile) in the parental income distribution.

-   \*Parental education: We obtain information on the parents' highest achieved level of education during individual's childhood from HOOGSTOPLTAB. We categorize education into 3 levels: University, Higher Professional Education, and Other (including NA). The parental education level is determined by the highest educational attainment between the father and the mother.

    -   \*For newborns and prim8 samples

    -   This is due to the availability of data on parental education, which began in 1983 for WO, 1986 for HBO, and 2004 for MBO (intermediate vocational education).

-   We introduce a third generation to the variable `GBAGENERATIE` from the GBAPERSOONTAB microdata for individuals in the cohort. If a child is native (autochtoon) and at least one of their parents is a second-generation immigrant (tweede generatie allochtoon), we reclassify the child's generation as a third-generation immigrant (derde generatie allochtoon). Essentially, we change the child's generation from native to third generation if at least one parent is a second-generation immigrant and the child is native.

    -   For children who are third-generation immigrants, we recode their origin (variable `GBAHERKOMSTGROEPRING`) as follows:

        1.  If the child is third generation and the father's origin is native, the child adopts the mother's origin.
        2.  If the child is third generation and the mother's origin is native, the child adopts the father's origin.
        3.  If the child is third generation and both parents' origins are non-native, the child adopts the mother's origin.

-   Migration background: We obtain child's migration background data from the GBAPERSOONTAB. We categorize migration background into 6 levels:

    1.  No Migration Background
    2.  Turkey
    3.  Morocco
    4.  Suriname
    5.  Dutch Caribbean
    6.  With Migration Background

-   Type of household: We obtain the type of household a child was growing up in from GBAHUISHOUDENSBUS. We categorize this into 2 levels: Single Parent and Two Parents.

-   Write the resulting sample (`02_predictors.rds)` dataset to *the scratch folder.*

-   At each step we record the sample sizes.

## 3. Add outcomes

In this step, we connect sample-specific outcomes to the samples.

-   We check whether the individual meets the residency requirement. We exclude the children who did not live continuously in the Netherlands within a specified period (`child_live_start` - `child_live_end`) allowing for a number of slack days defined by `child_live_slack_days`.

-   We add sample-specific outcomes. Further details regarding the outcomes used for each cohort can be found [here](resources/documentation/Samples.md).

-   Write the resulting sample (`03_outcomes.rds)` dataset to *the scratch folder.*

-   At each step we record the sample sizes.

## 4. Post-processing

In this step, we select variables from the created sample data sets that are relevant for our estimates.

-   Categorize individuals into income (wealth) groups based on parental income (wealth ) percentile:

    1.  15 ≤ Percentile ≤ 35: "Low"
    2.  40 ≤ Percentile ≤ 60: "Mid"
    3.  65 ≤ Percentile ≤ 85: "High"

-   Categorize individuals into income (wealth) distribution's tail groups based on the same percentile distribution:

    1.  0 ≤ Percentile ≤ 20: "Very Low"
    2.  80 ≤ Percentile ≤ 100: "Very High"

-   Write sample dataset `sample-name_cohort.rds` to the scratch folder.

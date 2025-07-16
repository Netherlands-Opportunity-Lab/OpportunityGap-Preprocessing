# Samples description
We create 97 outcomes in total based on 5 samples. Here, we briefly describe these samples and the outcomes. 

## 1. Perinatal sample
[! NOTE] in 2024Q4 we will have 2 perinaral and 2 mortality samples. currently there is only one newborns sample which contains both perinatal and mortality outcomes. how to go about this in the description of sampeles? for now, left as it was.

The perinatal cohort comprises approximately 1.5 million Dutch children who were born between 2008 and 2016. We assign these children to their home address based on where they reside at their date of birth. Parental income is measured between 2014 and 2018. The outcomes in the perinatal cohort are measured from 2008 to 2016.

- c00_sga (small-for-gestational age): Indicates children with a birth weight below the 10th percentile adjusted for gestational age and gender, according to the [Hoftiezer curve]( https://github.com/sodascience/kansenkaart_preprocessing/blob/cbs_updated/resources/Hoftiezer_Geboortegewicht%20curves.xlsx). 
- c00_preterm_birth: Indicates children with a gestational age before 37 completed weeks of gestation.

## 2. Child mortality cohort
The child mortality cohort comprises approximately 1.5 million Dutch children who were born between 2008 and 2016. We assign these children to their home address based on where they reside at birth. Parental income is measured between 2014 and 2018. The outcomes in the child mortality cohort are measured from 2008 to 2016.

- c00_perinatal_mortality: Represents the death of children that occurs between 24 completed weeks of gestation and up to 7 days after birth.
- c00_neonatal_mortality: Represents the death of children that occurs between 24 completed weeks of gestation and up to 28 days after birth.
- c00_infant_mortality: Represents the death of children that occurs between 24 completed weeks of gestation and up to 365 days after birth.

## 3. Prim8 sample
The prim8 samples consist of students in the final (8th) grade of primary school who were born between 2003 and 2006 (1st sample), and 2009 and 2011 (2nd sample). We assign these students to their home address based on the address on their 10th birthday. Parental income is measured between 2009 and 2013 (1st sample), and 2014 and 2018 (2nd sample). Parental education is defined on the child's 10th birthday. The outcomes are measured in the final (8th) grade of primary school.
	
- c11_math: Indicates whether the student has achieved at least the required level of mathematics in grade 8 of elementary school.
- c11_reading: Indicates whether the student has achieved at least the required level of reading in grade 8 of elementary school.
- c11_language: Indicates whether the student has achieved at least the required level of language proficiency in grade 8 of elementary school.
- c11_vmbo_gl_test: Indicates whether the student has received a test advice of at least VMBO-high or a higher level of high school education.
- c11_havo_test: Indicates whether the student has received a test advice of at least HAVO or a higher level of high school education.
- c11_vwo_test: Indicates whether the student has received a test advice of VWO level of high school education.
- c11_vmbo_gl_final: Indicates whether the student has received a final school advice of at least VMBO-high plus or a higher level of high school education.
- c11_havo_final: Indicates whether the student has received a final school advice of at least HAVO or a higher level of high school education.
- c11_vwo_final: Indicates whether the student has received a final school advice of VWO level of high school education.
- c11_under_advice: Indicates whether the student has received a final school advice lower than the test school advice. The determination is made using the advice table we have created, which can be found [here.](https://github.com/sodascience/kansenkaart_preprocessing/blob/main/resources/vo_advisering.xlsx) 
- c11_over_advice: Indicates whether the student has received a final school advice higher than the test school advice. The determination is made using the advice table we have created, which can be found [here.](https://github.com/sodascience/kansenkaart_preprocessing/blob/main/resources/vo_advisering.xlsx) 
- c11_youth_health_costs: Represents the total health care costs covered by the Health Insurance Act for students in grade 8 of elementary school.
- c11_youth_protection: Indicates whether the student has a youth protection measure in place while in grade 8 of elementary school.
- c11_living_space_pp: Represents the average living space per household member for students in grade 8 of elementary school.
- c11_class_vmbo_gl_test: Represents the percentage of individual's classmates in grade 8 of elementary school who receive a final test advice of VMBO-GL or higher.
- c11_class_havo_test: Represents the percentage of individual's classmates in grade 8 of elementary school who receive a final test advice of HAVO or higher.
- c11_class_vwo_test: Represents the percentage of individual's classmates in grade 8 of elementary school who receive a final test advice of VWO.
- c11_class_size: Represents the individual's class size in grade 8 of elementary school.
- c11_class_math: Represents the percentage of individual's classmates in grade 8 of elementary school who meet or exceed the math target level.
- c11_class_language: Represents the percentage of individual's classmates in grade 8 of elementary school who meet or exceed the language target level.
- c11_class_reading: Represents the percentage of individual's classmates in grade 8 of elementary school who meet or exceed the reading target level.
- c11_class_foreign_born_parents: Represents the percentage of individual's classmates in grade 8 of elementary school whose both parents were born abroad.
- c11_class_income_below_25th: Represents the percentage of individual's classmates in grade 8 of elementary school whose parents' income is below the 25th percentile of the parental income distribution.
- c11_class_income_below_50th: Represents the percentage of individual's classmates in grade 8 of elementary school whose parents' income is below the 50th percentile of the parental income distribution.
- c11_class_income_above_75th: Represents the percentage of individual's classmates in grade 8 of elementary school whose parents' income is above 75th percentile of the parental income distribution.
- c11_primary_neighborhood_income_below_25th: Represents the percentage of individual's neighbors whose parents' income is below the 25th percentile of the parental income distribution.
- c11_primary_neighborhood_income_below_50th: Represents the percentage of individual's neighbors whose parents' income is below the 50th percentile of the parental income distribution.
- c11_primary_neighborhood_income_above_75th: Represents the percentage of individual's neighbors whose parents' income is above the 75th percentile of the parental income distribution.
- c11_primary_neighborhood_foreign_born_parents: Represents the percentage of individual's neighbors whose parents are foreign born.

## 4. Age16 sample
The age16 sample consists of individuals who are 16 years old and were born between 2003 and 2007. We assign these students to their home address based on where they lived on their 15th birthday. Parental income is measured between 2014 and 2018. Outcomes are measured at age 16.

- c16_vmbo_gl: Indicates whether the individual has completed at least a VMBO-high high school education by the age of 16.
- c16_havo: Indicates whether the individual has completed at least a HAVO high school education by the age of 16.
- c16_vwo: Indicates whether the individual has completed at least a VWO high school education by the age of 16.
- c16_youth_health_costs: Represents the average total health care costs covered by the Health Insurance Act at the age of 16.
- c16_youth_protection: Indicates whether an individual has a youth protection measure in place at the age of 16.
- c16_living_space_pp: Represents the average living space per household member at the age of 16.
- c16_secondary_class_foreign_born_parents: Represents the percentage of individual's classmates in grade 4 of high school whose both parents were born abroad.
- c16_secondary_class_income_below_25th: Represents the percentage of individual's classmates in grade 4 of high school whose parents' income is below the 25th percentile of the parental income distribution.
- c16_secondary_class_income_below_50th: Represents the percentage of individual's classmates in grade 4 of high school whose parents' income is below the 50th percentile of the parental income distribution.
- c16_secondary_class_income_above_75th: Represents the percentage of individual's classmates in grade 4 of high school whose parents' income is above 75th percentile of the parental income distribution.
- c16_neighborhood_income_below_25th: Represents the percentage of individual's neighbors whose parents' income is below is below the 25th percentile of the parental income distribution.
- c16_neighborhood_income_below_50th: Represents the percentage of individual's neighbors in grade 8 of elementary school whose parents' income is below the 50th percentile of the parental income distribution.
- c16_neighborhood_income_above_75th: Represents the percentage of individual's neighbors whose parents' income is above 75th percentile of the parental income distribution.
- c16_neighborhood_foreign_born_parents: Represents the percentage of individual's neighbors in grade 8 of elementary school whose parents are foreign born.

## 5. Age21 sample
The age21 sample consists of individuals at age 21 born between 1998 and 2002. We assign individuals to their home address based on where they lived on their 15th birthday. Parental income is measured between 2014 and 2018. We measure the outcomes at age 21.

- c21_high_school_attained: Indicates whether the individual has achieved a basic high school qualification (havo, vwo, or mbo-2) by the age of 21.
- c21_hbo_followed: Indicates whether the individual has pursued higher professional education (HBO) or university education by the age of 21.
- c21_uni_followed: Indicates whether the individual has pursued university education by the age of 21.
- c21_young_parents: Indicates whether the individual had a child before the age of 20.
- c21_living_with_parents: Indicates whether the individual lives at parental home.

## 6. Age35 sample
The age35 sample consists of individuals around age of 35 born between 1984 and 1988. These individuals are assigned to their home addresses based on the address on their 15th birthday. Parental income is measured between 2003 and 2007. We measure their outcomes at the age of 34-35.

- c35_income: Represents the average pre-tax income between the ages of 34 and 35, measured in XXXX euros.
- c35_earnings: Represents the average primary income between the ages of 34 and 35, measured in XXXX euros.
- c35_below_poverty: Indicates whether an individual's income was below the poverty threshold at ages 34 and 35.
- c35_hbo_attained: Indicates whether an individual attained at least an HBO degree (higher professional education) by the age of 35.
- c35_wo_attained: Indicates whether an individual attained at least a university degree by the age of 35.
- c35_employed: Indicates whether an individual was employed at the age of 35.
- c35_disability: Indicates whether an individual received disability benefits at the age of 35.
- c35_social_assistance: Indicates whether an individual received social benefits at the age of 35.
- c35_specialist_mhc: Indicates whether an individual utilized specialist care within the basic insurance at the age of 35.
- c35_basic_mhc: Indicates whether an individual utilized generalist basic mental healthcare within the basic insurance at the age of 35.
- c35_pharma: Indicates whether an individual utilized pharmacy services within the basic insurance at the age of 35.
- c35_hospital: Indicates whether an individual utilized hospital care within the basic insurance at the age of 35.
- c35_total_health_costs: Represents the sum of healthcare costs at the age of 35, measured in 2020 euros.
- c35_hourly_wage: Represents the average hourly wage earned at the age of 35, measured in 2020 euros.
- c35_hrs_work_pw: Represents the average total hours worked per week at the age of 35.
- c35_permanent_contract: Indicates whether an individual had a permanent contract instead of a temporary contract at the age of 35.
- c35_hourly_wage_min_11: Indicates whether an individual had an hourly wage of 11 euros or above at the age of 35.
- c35_hourly_wage_min_14: Indicates whether an individual had an hourly wage of 14 euros or above at the age of 35.
- c35_debt: Represents the total debt of a household at the age of 35.
- c35_wealth: Represents the total wealth of a household at the age of 35.
- c35_homeowner: Indicates whether an individual was a homeowner at the age of 35.
- c35_wealth_no_home: Represents the total wealth of a household excluding the value of the house they own at age 35.
- c35_home_wealth: Represents the wealth of the house that remains after deducting the mortgage debt at age 35.
- c35_gifts_received: Indicates whether an individual received a gift between the ages of 26 and 35.
- c35_sum_gifts: Represents the total sum of the gifts received between the ages of 26 and 35.
- c35_household_income: Represents the average income at the household level when the child is aged 34-35.
- c35_disposable_household_income: Represents the average disposable income (gross income less transfers and taxes) at the household level when the child is aged 34-35.
- c35_primary_household_income: Represents the average primary income at the household level when the child is aged 34-35.
- c35_top_20_household_income: Indicates whether the individual's household income is in top 20th percentile of the household income distribution.
- c35_bottom_20_household_income: Indicates whether the individual's household income is in bottom 20th percentile of the household income distribution.
- c35_living_space_pp: Represents the average living space per household member at the age of 35.
- c35_age_left_parents: Represents the age at which an individual stopped living at parental home.

![Shot](https://github.com/user-attachments/assets/a04855ce-36ee-418b-b971-3c464e5f3dde)
# Here Comes H2N2
Analysis by Jordan Scriven  

## Business Understanding
As doctors and public health specialists warn of the forthcoming widespread of H2N2 flu virus, there is a rush from all pharmaceutical companies to develop the first H2N2 vaccine.  Once the vaccine is produced, the Department of Health and Human Services will run a public health campaign to encourage all eligible people recieve the vaccination.  The task is to run a predictive analysis on available data to inform that public health campaign - tailoring the campaign to specific demographics.

## Data Understanding
Data provided by the United States National Center for Health Statistics shows the social, economic, and demographic background of a surveyed population along with their opinions on effectiveness of vaccines and the vaccination status.  About 26,700 records were optained in the survey.

### Data Preparation
While the data includes information on both the H1N1 vaccine and the Seasonal Flu vaccine, we will concentrate on the H1N1 vaccination. The H1N1 flu virus was first detected in spring 2009 and the vaccination was available in October 2009. H1N1 came on quick, was unheard of and was responsible for many deaths. As we expect H2N2 to be similar, we will predict that people react the same.

We also needed to prepare the data for analysis by encoding categorical variables as numerical.

## Exploratory Data Anlysis
First, we want to examine that the belief in the effectiveness of a vaccination coincides with the probablity of receiving the vaccine.

![Effectiveness](https://github.com/user-attachments/assets/8d83fdde-b208-400c-adbe-3dba790b128d)

Then we looked at the vaccination rate by different demographics - sex, race, age, education level and income level.

![Sex](https://github.com/user-attachments/assets/b7a1b009-c0d0-4d9a-bd45-2aa6c0e25754)

![Race](https://github.com/user-attachments/assets/35f779d3-bfeb-4e14-acec-08e957afd422)

![Age](https://github.com/user-attachments/assets/73bf6520-2a21-47b6-bc18-fb35629c6fb4)

![EducationLevel](https://github.com/user-attachments/assets/e43693f3-958f-4863-a827-130cc0910fd4)

![IncomeLevel](https://github.com/user-attachments/assets/e0926423-0f1c-422d-ac0e-7f86fd58042a)

## Data Modeling
Using the different demographic groups, we ran a logistic regression model to determine if we would be able to predict the likelihood of vaccination for anyone who we had their demographics.

![Matrix](https://github.com/user-attachments/assets/7bf428d6-5260-4de4-ac1d-3bef0f327f2c)

The sample data has a large class imbalance with a much larger target of unvaccinated, so we oversampled the minority group.  This lowers the accuracy slightly (from 78.7% to 75.2%) but does increase the precision.

![Oversample](https://github.com/user-attachments/assets/ad3d2196-d649-4199-b9ae-95a0c97d43c7)

## Evaluation
                                  coef    std err          z      P>|z|      [0.025      0.975]
-----------------------------------------------------------------------------------------------
const                          -1.4257      0.090    -15.801      0.000      -1.603      -1.249
age_group_35 - 44 Years        -0.0166      0.063     -0.263      0.792      -0.140       0.107
age_group_45 - 54 Years         0.0113      0.058      0.195      0.845      -0.103       0.125
age_group_55 - 64 Years         0.2797      0.055      5.046      0.000       0.171       0.388
age_group_65+ Years             0.3050      0.054      5.621      0.000       0.199       0.411
education_LowEducation         -0.3231      0.046     -7.089      0.000      -0.412      -0.234
education_MediumEducation      -0.1146      0.043     -2.664      0.008      -0.199      -0.030
income_poverty_LowIncome       -0.2364      0.072     -3.271      0.001      -0.378      -0.095
income_poverty_MediumIncome    -0.2939      0.042     -7.081      0.000      -0.375      -0.213
sex_Male                       -0.0919      0.036     -2.567      0.010      -0.162      -0.022
race_Hispanic                   0.4104      0.100      4.097      0.000       0.214       0.607
race_Other or Multiple          0.3975      0.100      3.970      0.000       0.201       0.594
race_White                      0.3612      0.075      4.825      0.000       0.215       0.508

The logistic regression results indicate that several factors are significantly associated with H1N1 vaccination status. Specifically, individuals in older age groups (ages 55-64 and age 65+) are more likely to be vaccinated.  Those falling in the categories of low eduction and low or medium income are less likely to be vaccinated.  Men are predicted to recieve a vaccination less often than women and hispanic or other races are more likely to be vaccinated.

## Conclusion

The goal of the public health campaign is to reach those demographics who are less likely to vaccinate and convince as many of them as possible to vaccinate to reduce the spread of H2N2 through "herd immunity".  To reach those demographics, we have the following recommendations:

*   **Make it Convenient** People in younger age groups tend to have busy schedules with jobs, children to care for, etc. To help them out, offer mobile vaccination clinics where younger people frequent - schools, gyms, parks. And keep the process simple.
*  **Reduce Cost** With the lower income groups being less likely to recieve a vaccination, make sure the cost is low or free, so that financial problems are not the reason they aren't protected with vaccines.
*   **Educate** Low education levels tend to have less vaccinations.  Make sure a lower education doesn't prevent them from having the same low education on vaccinations.  Give them a chance to learn the concept of a vaccine, address misinformation that exists (we do not inject live, active viruses!), provide risk and reward.  Make sure information is clear and concise.

### Limitations
A limitation of the H1N1 data from United States National Center for Health Statistics is that it is surveyed data.  The data depends on the responses of a participant and that's if they answer at all.  We assume here that the likelihood of a participant responding to the survey is uniformly distributed.

## Next Steps

As we discover more about the H2N2 virus, and are able to take our steps to make vaccinations convenient, lower the cost and educate the public on the good of the vaccination, we will continually add data regarding the H2N2.  We can see if it fits the same model as H1N1 and run new models as we gather data.



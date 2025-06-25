#  Veritas Health Institute — 2025 Lung Cancer Diagnosis Report

![Task 31A - Adeniyi Oluwademilade Adedamola](https://github.com/user-attachments/assets/e92731a3-9932-492b-9843-55b983acc5e9)

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-yellow?style=for-the-badge)  
*Behavioural and Demographic Data Analysis for Early Lung Cancer Detection*

---

##  Overview

This project presents a complete end-to-end analysis of lung cancer diagnosis using behavioural, symptomatic, and demographic data. Conducted under the context of **Veritas Health Institute (2025)**, the goal was to uncover key risk patterns, segment participants based on risk level, and recommend early detection strategies through interactive visual storytelling using **Power BI**.

---

##  Project Objectives

- Identify the most common **symptoms** among diagnosed individuals.
- Discover the **leading behavioural risk factors** contributing to lung cancer.
- Segment participants into **risk categories** (Low, Medium, High).
- Provide **actionable insights and recommendations** for public health intervention.
- Deliver a **one-page Power BI dashboard** with rich interactivity and clarity.

---

##  Dataset Information

- **Source**: [Kaggle Lung Cancer Dataset](https://www.kaggle.com/datasets/aagambshah/lung-cancer-dataset)  
- **Size**: 309 participants  
- **Type**: Survey-based responses covering:
  - Demographics (Age, Gender)
  - Behavioural Indicators (Smoking, Alcohol, Anxiety, etc.)
  - Symptoms (Coughing, Chest Pain, Shortness of Breath, etc.)
  - Lung Cancer Diagnosis (`Yes/No`)

---

##  Tools & Technologies

- **Power BI** (Data Modelling, DAX, Visualization)
- **Power Query Editor** (Data Cleaning & Preprocessing)
- **DAX Measures & Calculated Tables**
- Git & GitHub for version control and documentation

---

## Dashboard Features

###  KPIs (Cards)
- % Diagnosed with Lung Cancer
- Average Age of Diagnosed Participants
- Leading Behavioural Risk Factor
- Most Common Symptom Among Diagnosed

###  Visuals Used
| Visual Type                    | Description                                       |
|-------------------------------|---------------------------------------------------|
| Treemap                       | Symptom Prevalence Among Diagnosed               |
| 100% Stacked Column Chart     | Diagnosis by Substance Usage (Smoking & Alcohol) |
| Ribbon Chart                  | Risk Level Breakdown (Low, Medium, High)         |
| Matrix Table                  | Behavioural Risk Matrix                           |
| Donut Chart                   | Gender Distribution of Diagnosed Cases           |
| 100% Stacked Bar              | Age Group vs Lung Cancer Diagnosis               |

---

##  Key DAX Measures

```DAX
LungCancerRate = DIVIDE(CALCULATE(COUNTROWS('Lung Cancer'), 'Lung Cancer'[LUNG_CANCER] = "YES"), COUNTROWS('Lung Cancer'))

AverageAgeDiagnosed = CALCULATE(AVERAGE('Lung Cancer'[AGE]), 'Lung Cancer'[LUNG_CANCER] = "YES")

LeadingBehaviorRiskFactor = 
VAR SummaryTable =
    SUMMARIZE(
        FILTER('Behavioural Breakdown', 
            'Behavioural Breakdown'[Presence] = "Yes" && 
            'Behavioural Breakdown'[LUNG_CANCER] = "Yes"),
        'Behavioural Breakdown'[Behaviour],
        "YesCount", COUNTROWS('Behavioural Breakdown')
    )
VAR MaxCount = MAXX(SummaryTable, [YesCount])
VAR TopBehavior = 
    MAXX(
        FILTER(SummaryTable, [YesCount] = MaxCount),
        'Behavioural Breakdown'[Behaviour]
    )
RETURN TopBehavior

More DAX expressions included in the Power BI file.
```

---

##  Supporting Tables Created

To make the analysis more flexible and insightful, three supporting tables were created from the main dataset:

###  Behavioural Breakdown
- **Purpose**: Unpivoted behavioural variables (e.g., Smoking, Alcohol Consuming, Anxiety) into a two-column format (`Behaviour`, `Presence`)
- **Use Case**: Enabled the creation of the **Behavioural Risk Matrix** and identification of the **Leading Behavioural Risk Factor**

### Symptom Breakdown
- **Purpose**: Consolidated symptom indicators (e.g., Coughing, Chest Pain, Fatigue) into a unified table with columns `Symptom` and `Presence`
- **Use Case**: Facilitated the **Symptom Prevalence Treemap** and detection of the **Most Common Symptom Among Diagnosed**

### Substance Consumption
- **Purpose**: Isolated and summarised the diagnosis split across **Smoking** and **Alcohol** usage
- **Use Case**: Powered the **Lung Cancer Diagnosis by Substance Usage** 100% stacked column chart

---

##  Observations Board

Based on the data visualisations and calculated insights, the following key findings were observed:

###  Fatigue Is the Most Common Symptom  
Fatigue was reported by **189 diagnosed participants**, making it the leading physical symptom associated with lung cancer in this dataset.

###  Smoking and Alcohol Use Are Strong Risk Factors  
**155 diagnosed participants** were smokers and **165** consumed alcohol — establishing these behaviours as major risk indicators.

###  Gender Split Is Slightly Male-Skewed  
While both genders were affected, **53.7% of diagnosed participants** were male, suggesting a marginally higher risk or exposure.

###  High-Risk Category Had a 100% Diagnosis Rate  
Every participant classified in the **High-Risk** segment (based on combined symptom/behaviour scores) was diagnosed with lung cancer.

###  Average Diagnosed Age Is 63 Years  
Age continues to be a strong correlate, with most diagnoses concentrated between **51–80 years**, and an average age of **63** among those diagnosed.

###  Age Groups 71–80 Show Extremely High Diagnosis Rates  
The **71–80 age group** had a staggering **98.04% diagnosis rate**, indicating an urgent need for focused health interventions in older adults.

###  Swallowing Difficulty & Yellow Fingers Are Underestimated  
Though less discussed in public health campaigns, these symptoms were strongly present in diagnosed patients and should not be ignored.

###  Behavioural Traits Like Anxiety & Peer Pressure Matter  
Beyond substances, psychosocial indicators (e.g., anxiety, peer pressure) were reported by **over 140 diagnosed participants**, highlighting the need for mental health integration in screening.

---

##  Recommendations

Based on the visual patterns and insights from the dashboard, the following practical actions are suggested:

###  Prioritise Adults Aged 50+ for Screening  
Most lung cancer diagnoses occurred in adults aged 51 and above. Focus public health screening and education on this age group to catch cases earlier.

###  Use Fatigue as a Primary Diagnostic Flag  
Fatigue was the most prevalent symptom among diagnosed patients. It should be considered a priority red flag for lung cancer screening, especially when combined with other symptoms.

###  Promote Smoking and Alcohol Awareness Campaigns  
The vast majority of diagnosed participants were smokers and/or alcohol consumers. Campaigns should focus on reducing these behaviours through targeted interventions.

###  Include Psychosocial Factors in Risk Evaluation  
Anxiety and peer pressure were frequently reported among diagnosed individuals. Mental health assessments should be included in routine evaluations for lung cancer risks.

###  Implement Risk-Based Triage Systems  
The High-Risk group in the risk segmentation model had a 100% cancer diagnosis rate. Health systems should adopt similar models for patient triage and prioritisation.

###  Educate on Subtle Symptoms  
Symptoms like swallowing difficulty and yellow fingers, though less frequently discussed, showed high presence among diagnosed participants and should not be overlooked during diagnosis.

###  Balance Sampling in Future Surveys  
The diagnosis rate in the dataset was unusually high (87.38%), possibly due to biased sampling. Future surveys should aim for more balanced sampling to improve generalisability.

###  Encourage Preventive Health Checkups  
Given the strong correlation between behavioural and symptomatic factors and cancer, preventive checkups should be promoted even among asymptomatic individuals in high-risk behavioural brackets.

---

## 🔗 Links

-  **Power BI File**: _[Download the .pbix file](./Veritas%20Health%20Institute%20—%202025%20Lung%20Cancer%20Diagnosis%20Report.pbix)_  
-  **Dashboard Summary Report**: _[View on Google Docs or PDF](./Veritas%20Health%20Institute%20—%202025%20Lung%20Cancer%20Diagnosis%20Report.pdf)_  
-  **Full Medium Report**: [Read the Project Article](https://medium.com/@demibolt/veritas-health-institute-2025-lung-cancer-diagnosis-report-d666e3de6225)

---

## 📬 Contact

- 📧 **Email**: adeniyioluwademilade@gmail.com  
- 💼 **LinkedIn**: [LinkedIn – Connect with Me](https://www.linkedin.com/in/adeniyioluwademilade)
- 🐦 **Twitter**: [@demibolt007](https://twitter.com/demibolt007)

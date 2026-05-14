# The ALERTSENSE Dataset: Comparing Human Perception of AI-Personalized Disaster Alerts and Conventional Warnings 

## **Table of Contents**

1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Implementation](#implementation)
4. [Tutorials](#tutorials)

## **Introduction**
Standard disaster alerting systems like IPAWS, WEA, and EAS are built to send the same message to everyone in a broad area. While this approach works well for fast, large-scale communication, these alerts often feel generic and lack personal relevance. Research in risk communication shows that people respond better when alerts are clear, trustworthy, relevant, and provide concrete guidance. When alerts feel repetitive or vague, people may start tuning them out, leading to alert fatigue and lower compliance. 


With the rapid rise of large language models (LLMs), it is possible to generate alerts that are more personalized and context-aware. Yet we still know very little about how the public actually reacts to AI-personalized alerts compared to standard ones. 


The ALERTSENSE dataset was created to help fill this knowledge gap. It contains responses from participants across the United States who evaluated disaster alerts generated from two sources: (1) Standard alerts originally written by the National Weather Service (NWS) and the PBS Warning, Alert, Response Network (PBS WARN); and (2) AI-personalized alerts produced in real time using Google’s Gemini 1.5 model. 

The study was conducted with approval from the University of Colorado Boulder's Institutional Review Board (IRB Protocol #24-0583) and involved U.S. participants recruited via Amazon Mechanical Turk (MTurk). Each participant was randomly assigned to receive a standard alert or an AI-personalized alert on the screen, and rated the alert based on six key qualities: clarity, trust, relevance, influence, confidence, and certainty. The dataset also includes sociodemographic information, personal traits, and the specific disaster type assigned to each participant. Together, these data provide a rich foundation for studying disaster communication, human-AI interaction, risk perception, and the potential benefits of personalized warning systems. 

## **Sample Disaster Alerts**

The table below presents representative examples of disaster alerts used in the study across both experimental conditions. Condition 1 includes standard, non-personalized alerts, while Condition 2 includes AI-personalized alerts tailored to participant-specific context. 

<table>
  <thead>
    <tr>
      <th align="left" valign="top">Event</th>
      <th align="left" valign="top">Condition 1 (Standard alert)</th>
      <th align="left" valign="top">Condition 2 (AI-personalized alert)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top">Flood</td>
      <td valign="top">Flood emergency: Stay where you are. Do not attempt to drive. Do not enter the water. Climb to higher ground to evacuate. Consider all roads closed until further notice.</td>
      <td valign="top">Attention residents of Seattle: Heavy rain and potential flooding are impacting your area. Secure your pets, gather medications, and ensure family members are prepared. Your single-family home may be at risk; have an evacuation plan ready. Monitor flood warnings at <a href="https://www.weather.gov">https://www.weather.gov</a>.</td>
    </tr>
    <tr>
      <td valign="top">Tornado</td>
      <td valign="top">National Weather Service: Tornado warning in this area until 12:15 PM. Take shelter now in a basement or an interior room on the lowest floor of a sturdy building. If you are outdoors, in a mobile home, or a vehicle, move to the closest substantial shelter and protect yourself from flying debris. Check the media.</td>
      <td valign="top">Attention residents of Terre Haute: A tornado is imminent. Seek immediate shelter in a basement or interior room. Keep medications accessible. Contact family members. Follow updates at <a href="https://www.weather.gov">https://www.weather.gov</a>.</td>
    </tr>
    <tr>
      <td valign="top">Winter storm</td>
      <td valign="top">The County Sheriff's Office has placed a No Travel Advisory throughout the County until the winter storm passes and driving conditions improve. Monitor local news for updates on the road conditions.</td>
      <td valign="top">Attention Staten Island residents: Winter storm approaching. Secure your pets, family, and medications. Stock up on pizza. Monitor evacuation notices. Follow updates at <a href="https://www.weather.gov">https://www.weather.gov</a>.</td>
    </tr>
  </tbody>
</table>

## **Dataset**
The ALERTSENSE dataset is provided as a single CSV file located at: data/mturk_data.csv 

This file contains all cleaned responses from the survey (N = 503), including sociodemographic factors (gender, age, education, language preference, prior disaster experience), personal traits (living close to family, having dependent family members, use of medication, pet ownership, home type),  U.S. Zip code, the exact alert text each participant viewed, and Likert-scale evaluations. 

Each row represents one participant, and each column corresponds to a specific survey field or derived variable. The table below describes every column included in the dataset. 

- \* Derived from the participant’s responses 
- ∆ Fields automatically generated and recorded by the survey logic

## Dataset Fields

| Data Field | Description |
|-----------|-------------|
| participant_id<sup>*</sup> | Encrypted MTurk worker ID for participants |
| age | Age bracket selected by participant |
| participant_Zipcode | Participant’s self-reported Zip code |
| participant_city<sup>*</sup> | Participant’s U.S. city derived from Zip code |
| participant_state<sup>*</sup> | Participant’s U.S. state derived from Zip code |
| gender | Participant’s self-reported gender |
| hispanic_or_latino | Participant’s ethnicity identification (Hispanic/Latino) |
| race | Participant’s self-reported race category |
| race_text | Open-ended race response (if applicable) |
| education | Participant’s highest educational attainment |
| language | Primary language(s) spoken at home |
| language_text | Other specified languages spoken at home |
| confidence_in_understanding_english | Self-rated ability to understand English |
| previous_disaster_experience | Whether the participant has prior disaster experience (Yes/No) |
| disaster1 | Prior disaster experience (entry 1) |
| location1 | Location corresponding to disaster 1 |
| disaster2 | Prior disaster experience (entry 2) |
| location2 | Location corresponding to disaster 2 |
| disaster3 | Prior disaster experience (entry 3) |
| location3 | Location corresponding to disaster 3 |
| disaster4 | Prior disaster experience (entry 4) |
| location4 | Location corresponding to disaster 4 |
| disaster5 | Prior disaster experience (entry 5) |
| location5 | Location corresponding to disaster 5 |
| time1 | Recency of disaster 1 (selected from year ranges) |
| time2 | Recency of disaster 2 (selected from year ranges) |
| time3 | Recency of disaster 3 (selected from year ranges) |
| time4 | Recency of disaster 4 (selected from year ranges) |
| time5 | Recency of disaster 5 (selected from year ranges) |
| family | Whether family lives nearby (Yes/No) |
| occupation | Participant’s job or type of work |
| dependents | Whether the participant cares for dependents (Yes/No) |
| medications | Whether the participant requires daily medications (Yes/No) |
| home_type | Type of housing |
| home_type_text | Open-ended housing description (if “Other”) |
| pet | Whether the participant owns pets (Yes/No) |
| fun_fact | Optional fun fact provided by the participant |
| condition<sup>∆</sup> | Experimental condition (1 = Standard alert, 2 = AI-personalized alert) |
| alert_display<sup>∆</sup> | Exact disaster alert text shown to the participant |
| selected_disaster<sup>∆</sup> | Disaster category assigned based on participant Zip code |
| clarity | Perceived clarity of the alert (5-point Likert scale) |
| trust | Perceived trustworthiness of the alert (5-point Likert scale) |
| relevance | Perceived relevance of the alert (5-point Likert scale) |
| influence | Perceived influence of the alert (5-point Likert scale) |
| confidence | Perceived confidence in the alert (5-point Likert scale) |
| certainty | Perceived certainty in the alert (5-point Likert scale) |

## Metadata Files

In addition to the main survey dataset, the ALERTSENSE repository includes three metadata files that document the alert generation logic, disaster selection procedure, and experimental stimuli used in this study. These files are essential for reproducing the study design, understanding how alerts were constructed and assigned, and supporting secondary analyses or replication efforts. 

#### [`disaster_prompt.txt`](data/metadata/disaster_prompt.txt)
This file contains the base prompt template used to generate AI-personalized disaster alerts used in this study. 

The prompt was provided to Google’s Gemini 1.5 LLM API and designed to ensure that AI-personalized alerts followed similar structural conventions, tone, and formatting as standard alerts. The prompt incorporates contextual information such as disaster type and location, while allowing the LLM to generate personalized, context-sensitive alert text. This file documents the exact instruction logic used for AI alert generation, and is critical for reproducibility and future benchmarking of LLM-based alert systems. 

#### [`standard_alerts_by_disaster.txt`](data/metadata/standard_alerts_by_disaster.txt)
This file contains the library of standard, human-authored disaster alerts used in this study. 

Alerts were sourced from authoritative public warning systems, including NWS and PBS WARN. Each alert corresponds to a specific disaster type (e.g., flood, wildfire, winter storm) and adheres to established public alerting standards, including concise language and standardized structure. These alerts serve as the baseline against which AI-personalized alerts were evaluated. 

#### [`top_disaster_by_state.txt`](data/metadata/top_disasters_by_state.txt)
This file maps each U.S. state to its three most frequent disaster types, derived from historical hazard data reported by the National Oceanic and Atmospheric Administration (NOAA) U.S. billion-dollar weather and climate disasters database. 

Participants’ self-reported Zip codes were validated and used to determine their state, after which one disaster type was randomly selected from the top three disasters associated with that state. This ensured that participants evaluated alerts for hazards that were geographically realistic and relevant to their location. This file documents the state-to-disaster logic embedded in the survey and supports transparent verification of disaster assignment. 

---

Together, these metadata files provide full traceability between participant’s location, disaster assignment, alert content, and experimental condition, enabling rigorous replication, auditing, and extension of the ALERTSENSE dataset. 



## **Implementation**

### Dependencies
- `python`
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `geocode`

## **Tutorials**

The repository includes two interactive tutorials that demonstrate how to explore, visualize, and enrich the ALERTSENSE dataset. 

### **1. Data Visualization & Distribution Analysis**
**Notebook:** `tutorials/data_visualization.ipynb`  

This tutorial walks through basic data exploration and visualization using participants’ survey data (`mturk_data.csv`). 

It includes: 
- Summary statistics of participant demographics and responses 
- Geographical distribution of participants 
- Heatmaps and interactive plots showing perception score variations by alert type 

The goal of this tutorial is to help users quickly understand the dataset structure and variability across the data. 

---

### **2. Zip Code, City, and State Extraction**
**Notebook:** `tutorials/geolocation_extraction.ipynb`  

This tutorial focuses on geographical data processing for `mturk_data.csv`. 

It demonstrates how to:
- Extract **city** and **state** from Zip codes using `pgeocode`

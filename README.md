***
# Passenger flight incidents
✈️ Automating data categorization using Structured Outputs
***

<br>

<div class='tableauPlaceholder' id='viz1745847359579' style='position: relative'><noscript><a href='#'><img alt='Cause ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pa&#47;passengerflightincidents&#47;Cause&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='path' value='views&#47;passengerflightincidents&#47;Cause?:language=en-US&amp;:embed=true&amp;:sid=&amp;:redirect=auth' /> <param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pa&#47;passengerflightincidents&#47;Cause&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>                <script type='text/javascript'>                    var divElement = document.getElementById('viz1745847359579');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.minWidth='420px';vizElement.style.maxWidth='1920px';vizElement.style.width='100%';vizElement.style.minHeight='587px';vizElement.style.maxHeight='1107px';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.minWidth='420px';vizElement.style.maxWidth='1920px';vizElement.style.width='100%';vizElement.style.minHeight='587px';vizElement.style.maxHeight='1107px';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else { vizElement.style.width='100%';vizElement.style.height='1227px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>

## 📖 Overview

With airline incidents making headlines, flying might seem more dangerous than ever… but is it really?

This project aims to analyze scheduled passenger flight incidents (e.g. commercial flights), identifying their causes, as well as airlines and plane models associated with these events. The project is structured into three main steps :

1. Web scraping for incident information
    - A combination of `PyAutoGUI` and `BeautifulSoup` was used to collect articles on flight incidents occurred between Jan 2021 and March 2025
2. Automated incident categorizing via `OpenAI API`
    - Articles were trimmed to optimize input token usage
    - The text were processed through the `OpenAI API` to extract categorizations based on pre-defined structured outputs, along with associated probability scores for manual verification
    - Additional data cleaning was performed to address potential discrepancies
3. Data visualization using `Tableau`
    - The cleaned and categorized data was visualized to highlight trends, causes, and patterns across airlines and aircraft models

## ❓ Key questions

**Causes of the incidents**

Has there been an increase in incidents, and if so, what are the main causes?
- The yearly aggregated data suggests an increase in incidents over the given period. This increase is largely attributed to unfavorable weather conditions, with turbulences frequently cited. Technical failures were the second most common cause.
- Interestingly, a noticeable cases involved passenger inattention, where injuries occurred due to misstep or other types of inadvertence.

**Casualties from the incidents**

What was the most fatal incident during the given time frame?
- The most tragic incident involved Jeju Air (BKK > MWH) on 29th of December 2024, resulting in 179 fatalities. December 2024 also marked the deadliest month, with 33 injuries and 218 deaths.

**Plane models**

Which manufacturer’s planes were most frequently involved in incidents?
- Over half of the incidents in 2022 involved Boeing aircraft, followed by Airbus. However, this does not imply that Boeing planes are inherently more prone to incidents, as the analysis does not account for the proportion of Boeing aircraft in operation relative to other manufacturers.

**Airlines**

Which airlines were most frequently involved in incidents?
- US-based airlines (e.g., United Airlines, Delta Air Lines, American Airlines, Southwest Airlines) accounted for approximately 20% of the incidents. However, since this analysis does not consider the total number of flights operated, this figure may reflect the higher volume of operations by US carriers.
- Contrary to initial expectations, only Ryanair stood out among Low-Cost Carriers, with a significant number of incidents linked to passenger inattention.

## 💾 Dataset

Out of 887 incidents identified from the articles, 271 were classified as scheduled passenger flights. These incidents were further categorized according to the following criteria:

```
Extracted data
├── Flight Type : scheduled / unscheduled / other
├── Date of the incident
├── Name of the operating carrier
├── Name of the marketing carrier
├── Whether Low Cost Carrier
├── Name of the plane manufacturer
├── Name of the plane model
├── Departure airport
├── Destination airport
├── Number of minor injuries
├── Number of major injuries
├── Number of fatalities
├── Cause of the incident
├── Probability of the cause of the incident
└── Detailed cause
```

## ⏭️ Limitations and possible next steps

**Lack of Flight Volume Data**

- Comparing number of incidents might not provide the full picture as total number of flights are not considered in the analysis. For example, although the number of incidents have been increasing since 2021, it’s not clear if the share of incidents actually increased, or if it’s due to increase of overall passenger flights. This was mainly due to cost to aviation API access. To have more complete picture, access to such APIs can be considered.

**Reliance on News Articles Over Official Reports**

- The articles used in this analysis were generally published shortly after the incidents occurred, meaning that reported causes were often speculative and based on initial observations of the circumstances. While official aviation incident reports from regulatory authorities offer a more detailed and verified understanding, they typically have a significant publication delay. In this project, news articles were prioritized to capture recent incidents. As a next step, supplementing the dataset with official reports could be considered as they would improve accuracy and depth.

**Temporal Context and Long-Term Trends**

- The analysis focuses on a relatively short period (2021–2025). Expanding the time frame by including historical data could help distinguish between short-term fluctuations and long-term safety trends in aviation.

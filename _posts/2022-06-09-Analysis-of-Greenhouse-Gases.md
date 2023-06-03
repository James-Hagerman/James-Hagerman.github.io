---
layout: post
title: Analysis of the Effects of Greenhouse Gases
subtitle: Explores the correlation between Greenhouse Gases, Pollutants, Sea Level, and Natural Disasters
cover-img: /assets/img/ghg_background.jpg
thumbnail-img: /assets/img/ghg_thumbnail.jpg
share-img: /assets/img/ghg_background.jpg
gh-repo: https://github.com/James-Hagerman/tek-hagerman-james-capstone2
gh-badge: [star, fork, follow]
tags: [Data Engineering, Statistics, Dashboard, Climate Change]
---



The objective was to analyze and develop an interactive dashboard to explore the correlations among greenhouse gases/pollutants, sea level, natural disasters, and temperature. The project aimed to address three key questions: the correlation between sea level and natural disasters, sea level and greenhouse gases, and the relationship between natural disasters and greenhouse gases.

To begin, I sourced data from four different datasets, each from a distinct reliable source. However, since the data came from multiple sources, I had to dedicated significant effort in cleaning and transforming it using Jupyter Notebook. The initial step involved loading and cleaning the data, followed by conducting preliminary data exploration to gain insights into the dataset.

To facilitate analysis, I merged the formatted tables, considering variations in country-specific and worldwide data. With the merged dataset, I proceeded to create heatmaps to identify potential correlations among the variables of interest. Additionally, I conducted hypothesis testing to assess the strength and significance of these correlations.

The results of the hypothesis testing yielded valuable insights. Firstly, in the case of sea level and natural disasters, an R-value of 0.90 suggested a strong positive correlation. This implies that as sea levels rise, there is a notable tendency for an increased occurrence of natural disasters. The exceptionally low P-value of 1.76e-45 provides strong statistical evidence to reject the null hypothesis of no correlation.

Regarding sea level and greenhouse gases/pollutants, the hypothesis test indicated a statistically significant correlation (p-value of 0.049). However, the resulting weak positive correlation (r-value of 0.31) suggests that the association between rising sea levels and increased greenhouse gas emissions is not as pronounced.

Lastly, exploring the relationship between natural disasters and greenhouse gases/pollutants revealed a statistically significant correlation (p-value of 0.012). The moderate positive correlation (r-value of 0.41) implies that as the instances of natural disasters increase, there is a tendency for greenhouse gas/pollutant levels to rise. These findings highlight the interconnectedness between natural disasters and the environmental impact of greenhouse gases/pollutants.

To enhance data exploration and accessibility, I developed an interactive dashboard using Power BI. The dashboard allows users to explore and visualize the analyzed data, providing a comprehensive understanding of the correlations and their implications.

<span style="color:gray">*Dashboard showing an overview of greenhouse emissions by country and by year*</span>
![](/assets/img/ghg_greenhouse_main_page.PNG)

<span style="color:gray">*Dashboard to view the relationship and greenhouse emissions sea level*</span>
![](/assets/img/ghg_sea_level_page.PNG)

<span style="color:gray">*Dashboard to view the relationship between greenhouse emissions and number of natural disasters*</span>
![](/assets/img/ghg_num_disasters_page.PNG)

In conclusion, one of the most significant findings of this project was the strong correlation between sea level and the occurrence of natural disasters. As sea levels rise, there is a notable tendency for an increased number of natural disasters. This emphasizes the critical role of sea level in influencing the frequency and severity of such events.

To visualize this correlation, a linear regression plot has been included below:

![](/assets/img/sea_lvl_disasters_plt.PNG)

This plot further illustrates the positive relationship between sea level and natural disasters, reaffirming the project's findings. The comprehensive analysis, interactive dashboard, and insightful conclusions of this project highlight the significance of understanding the correlations among greenhouse gases, sea level, natural disasters, and their environmental implications.

****

#### Data Sources: 
- EMDAT (2020): International Disaster Database <span style="color:gray">*Natural Disaster data*</span> [Link](https://ourworldindata.org/grapher/number-of-natural-disaster-events)

- OECD (2022): "Air and climate: Greenhouse gas emissions by source", OECD Environment Statistics <span style="color:gray">*Greenhouse Emissions by Year and Country data*</span> [Link](https://www.oecd-ilibrary.org/environment/data/oecd-environment-statistics/greenhouse-gas-emissions_data-00594-en)

- UHSLC (2020): Estimate of Data for the Changes in Sea-Level <span style="color:gray">*Sea-Level data*</span> [Link](https://datahub.io/ismail.shahzad/rise-in-sea-level)

- NASA (2021): Global Climate Change Vital Signs of the Planet <span style="color:gray">*Temperature Data*</span> [Link](https://data.giss.nasa.gov/gistemp/graphs/graph_data/Global_Mean_Estimates_based_on_Land_and_Ocean_Data/graph.txt)


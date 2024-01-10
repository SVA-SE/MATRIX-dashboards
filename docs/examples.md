---
layout: default
title: "Practical Examples"
nav_order: 6
toc: true
---

# Practical Examples of Dashboards and Tools
{: .no_toc }

<details open markdown="block">
  <summary>
    Contents
  </summary>
  {: .text-delta }
1. Contents
{:toc}
</details>

Found in here are practical "real-world" examples of interactive dashboards and tools, developed by members of the MATRIX project.

## BIKE (RUOKAVIRASTO, Finland)

BIKE is a probabilistic dietary exposure assessment model for microbiological hazards (acute exposures) and chemical hazards (chronic exposures) in food, aimed for risk assessment professionals doing quantitative assessments. It is downloadable and open source, providing dashboard features in a graphical user interface (Shiny App). Once downloaded, the user can run the model in their local computer with their own data, to obtain results on estimated exposure (& concentration- & consumption-) distributions and the associated uncertainty implied by the quantity and accuracy of data.

### Method
The models are based on Bayesian statistical methods and implemented by Markov Chain Monte Carlo (MCMC) simulations. The mathematical models are described in detail in open journal: <a href="https://www.mdpi.com/2304-8158/10/11/2520" target="_blank">https://www.mdpi.com/2304-8158/10/11/2520</a>, and the corresponding matching model code at <a href="https://github.com/jukran/BIKE" target="_blank">https://github.com/jukran/BIKE</a>.

### Data
Consumption data for named food types and hazard occurrence data for the same food types. The user is required to provide data on dietary records for a representative sample of individuals for at least two days per individual, showing the consumed amounts (positive or zero) of each named food type per day. Additionally, hazard concentrations (a set of measurements) and possibly hazard prevalence data for the corresponding food types are needed. A few combinations and alternative interpretations of data are allowed, e.g. concerning values below or between measurement limits. Also processing factors can be applied, affecting prevalence and/or concentration at the time of consumption.

### Technical implementation
The model utilizes both R and OpenBUGS, which need to be installed first. The R code reads data from user given files, and then formats and analyses the data. Based on this, it writes a data-specific OpenBUGS code for implementing the Bayesian model simulations, according to the data structure found, and calls OpenBUGS to perform the MCMC simulations accordingly. After the MCMC simulations are done, the results are processed in R, and they are visualised in a local Shiny app which provides a user interface for interactively investigating the hazard-food exposure pairs, or total exposure from several foods, or concentrations, or consumptions.

## COVID-19 Dashboard (SSI, Denmark)
**<a href="https://experience.arcgis.com/experience/242ec2acc014456295189631586f1d26" target="_blank">https://experience.arcgis.com/experience/242ec2acc014456295189631586f1d26</a>**

### Data
The data used in this dashboard comes from <a href="https://covid19.ssi.dk/datakilder-og-definitioner" target="_blank">several registers and surveillance systems</a>:

* The Central Population Register (CPR) provides data regarding address, nationality, and death date
* The Cause of Death Register (DAR) provides data on the official cause of death
* Patient Registers (LPR & LPR3) provide data on patients currently admitted at hospitals in Denmark
* Sentinel surveillance from private practitioners provides data on patients seen for moderate illness
* <a href="https://covid19.ssi.dk/overvagningsdata/covidmeter" target="_blank">COVIDmeter</a>, a platform that allows individuals to report whether or not they have had COVID-related symptoms each week, and other home-based reporting methods provide data on individuals with mild to no symptoms
* The Authorizations registry monitors the infection among healthcare personnel
* MIS3 is the central database where all patients with diseases with reporting obligation are registered. Covid-19 cases were reported individually but now the reporting is done by the laboratories
* These registers are then coupled with The Danish Microbiological Database (MiBA), which provides data on microbiological test results across Denmark both from private and public test centers

#### Data pipeline
Data is taken from the MiBA database (raw sample results), standardized in the KIDS (Keys to Infectious Diseases System) data mart, and then processed with the help of SAS and Python, and finally ArcGIS. ArcGIS was chosen from among other possible tools because the interface is fairly user-friendly, it is great for geographical data visualization, and it does not require as sophisticated coding skills as some of the other solutions.

### Layout
The dashboard has different interfaces, which allow the user to choose whether they would like to see data regarding infection or vaccination on either a municipal or a regional level. Once an interface has been chosen, the viewer can see various relevant numbers, graphs and tables, including an interactive map of Denmark broken down by the aforementioned level of the user’s choosing. Some figures are also interactive, allowing the user to choose a municipality or region to view in greater detail. Additionally, the collection of dashboards has an interface displaying key national numbers covering the last 24 hour period as well as since 27 January 2020.

### Implementation
The dashboards are automated and update every day at 14:00 CET. The update frequency can be adjusted depending on the level of alertness/attention regarding covid-19. Since the summer of 2022, only the key national numbers interface is updated daily, while the rest of the dashboard is updated only on weekdays.

## Disease Dashboards (SVA, Sweden)

The Swedish Veterinary Agency (SVA) is the largest veterinary laboratory in Sweden. Every day the microbiology, pathology and sequencing departments analyse a large amount of samples, which in turn produces large amount of data. These data need to be summarised and translated into actionable information in order to fulfil one our main missions: surveillance communication. We need to effectively communicate the epidemiological situation of Sweden to disease experts, as well as animal owners and the general public.

<a href="https://www.sva.se/amnesomraden/smittlage/sjukdomsrapporter-om-sva-s-overvakning/" target="_blank">Surveillance of infectious diseases in animals and humans</a> ("the surveillance report") is the annual report describing the surveillance activities carried out in Sweden during the year. The report covers surveillance for important animal diseases and zoonotic agents in humans, food, feed and animals, carried out and compiled by experts from several Swedish governmental agencies, university and private industry with surveillance mandates along the entire food chain, from farm to fork. The surveillance report is published by the Swedish Veterinary Agency (SVA), in collaboration with the Swedish Board of Agriculture, the Public Health Agency and the Swedish Food Agency.

To better highlight the important findings presented in the report, and to strengthen the "one health-ness" of the surveillance, SVA is now planning to translate the contents of chapters describing hazards of great interest into interactive online Disease Dashboards. These dashboards will collect all our available knowledge about a specific pathogen, both historically and the current situation.

### Data
The data presented in these disease dashboards will come from two main sources:

* The surveillance report, which provides manually curated datasets and expert analyses on an annual basis. This will provide a historical overview and in-depth conclusions about the status of the disease.
* Internal databases for storage of laboratory results and surveillance data, which are updated daily. This will give a snapshot of the current disease situation, allowing experts to obtain information and take action in a timely and robust manner.

### Layout
The dashboards will be structured as a traditional side-menu website, with different tabs covering different topics. It will have full interactive capabilities, meaning that all data-driven content (maps, tables, graphs, etc) can be filtered and customised to the user's needs.

### Technical implementation
The dashboard will be developed using a combination of R, JavaScript and CSS. An in-house R package has been developed to produce static graphs, maps and tables for the surveillance report; this will be adapted so that it can also be used to create dynamic JavaScript-powered HTML widgets, something which is easily achievable without leaving the R environment. Another in-house R package exists for analysing and summarising the daily lab data, which is currently used to update standalone maps, graphs and tables on the external web; this package will be expanded on to provide content for the disease dashboards. For greater customisation of design and behaviour, a layer of custom JavaScript and CSS will be added on top of the R-generated content. The content will then be brought together into a full web application using the <a href="https://shiny.rstudio.com/" target="_blank">R Shiny</a> package. The app will be hosted on an internal virtual server and made available through an Internet connection. It will be possible to control the access to the dashboards, ranging from specific users within SVA to the entire public. The plan is to establish a localised access control so that, for example, certain tabs may be available publicly while others require authentication.

## FoodChain-Lab (BfR, Germany)
**<a href="https://foodrisklabs.bfr.bund.de" target="_blank">https://foodrisklabs.bfr.bund.de</a>**

FoodChain-Lab (FCL) is a free and open-source software tool aimed to support trace-back and trace-forward analysis of implicated feed or food items along supply chains as well as exposure and risk assessments in foodborne incidents (outbreaks, chemical contaminations).
Implementation:
The desktop version of FCL has been implemented as a modular extension to the open source data analytics platform Konstanz Information Miner (KNIME). KNIME enables visual assembly of data analysis workflows. These workflows consist of so-called nodes and edges. Each node is able to perform a specific data processing task while edges define how information flow is directed between nodes. FCL is also available as a web application (<a href="https://fcl-portal.bfr.berlin" target="_blank">FCL Web</a>).

FoodChain-Lab was created in 2011 and has been running and constantly developing with the support of third projects. From 2023 onward, FCL will be supported by EFSA and BfR for further improvements.

### Data
FCL Desktop collects and imports data into an internal database by generating semi-filled Excel templates that can be sent to local authorities for data completion and afterwards be imported into the database, or through a direct interface to the database for manual data input. Once the data is transferred into the database it can be validated and updated. FCL Web uses a JSON-based data format and is fed with data from FCL Desktop or other food tracing software systems.

### Layout
A major application of FCL Desktop and FCL Web is the analysis and visualization of food tracing information. This is accomplished by the construction and visualization of interactive food chain network graphs consisting of nodes (stations such as food business operators or disease cases) and edges (food product transportation events, deliveries). A score calculated for all stations and deliveries helps to identify the source of a foodborne contamination and prioritize next investigation steps. All visualizations are interactive and can be exported as data tables or images for use in other KNIME nodes, other tools or in reports. Detailed description of FCL is available at the website (link above).

## GENPAT (IZS, Italy)
**<a href="https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis" target="_blank">https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis</a>**

The “National Reference Centre for Whole Genome Sequencing of microbial pathogens: database and bioinformatic analysis” (GENPAT) manages, on behalf of the Italian Ministry of Health, a national platform for collection and sharing of microbial pathogen WGS data from animal, food and environmental isolates and for performing bioinformatic analyses.

The platform supports and assists the Italian Ministry of Health and competent authorities in technical and scientific claims, providing IT tools and data that are quickly available, usable and helpful in outbreak situations allowing to link molecular typing and bioinformatics analyses results with time and position of sampling as well as the other epidemiological information available. The system is a web-based information system with three main components:

- Data component: Based on CMDBuild, an open-source web enterprise environment used to configure custom applications and to manage databases of items. It has native mechanisms to model its internal database, design workflow, configure reports, build connectors with external systems and so on.
- Calculation engine component: Nextflow enables scalable and reproducible scientific workflows using software containers. It allows the adaptation of pipelines written in the most common scripting languages. Its fluent DSL simplifies the implementation and deployment of complex parallel and reactive workflows on clouds and clusters.
- Dashboards component: WGS analysis and metadata are combined together in easy-to-use dashboards. For this purpose, a number of well-known, robust open-source projects have been integrated: GrapeTree, Phylocanvas, Openstreetmap, Openlayers.

The GENPAT platform is derived from the OHEJP COHESIVE project results. In particular, it extends the CIS (COHESIVE Information System) for Italian needs. The system has been also used in the national project of the "Italian One-Health JointDB" where a pilot has been conducted on Listeria monocytogenes to integrate data from ISS (storing isolates from human clinical cases) and GENPAT (storing animal, food and environmental isolates) using a mechanism based on federated servers.

## OH-EpiCap tool (ANSES, France & UoS, UK)
**<a href="https://freddietafreeth.shinyapps.io/OH-EpiCap/" target="_blank">https://freddietafreeth.shinyapps.io/OH-EpiCap/</a>**

OH-EpiCap Tool: Evaluation tool for One Health epidemiological surveillance capacities and capabilities
The OH-EpiCap tool aims to develop system-specific profiles of (potential) surveillance interoperability between sectors, highlighting both strengths and gaps in surveillance capacities and capabilities.

The OH-EpiCap tool allows evaluation and improvement of ‘One Health (OH)-ness’ using a set of standardized indicators, which allows comparison across systems, countries and hazards of interest. Countries at similar levels of ‘OH-ness’, including similar capacities, limitations and resources, can potentially collaborate to develop a common framework for OH Surveillance that will address zoonotic threats across borders. This will improve national OH structures, including surveillance and data analysis, while also facilitating better integration of multinational collaboration. Countries at different levels of ‘OH-ness’ and surveillance capacities/resources can share experiences regarding surveillance practice against the same pathogen, transfer knowledge and share ideas to improve surveillance quality and efficacy across settings.

The OH-EpiCap tool facilitates discussion between surveillance representatives from different disciplines and programs, encouraging a more collaborative OH approach. It is based on a standalone interactive web-based application, which allows a panel with representatives from all sectors within the system being evaluated to complete an in-country surveillance evaluation. The tool focuses on evaluating “One Heath-ness” across three dimensions:

- Dimension 1: Organization of the OH surveillance system
- Dimension 2: OH-ness in operational activities of the OH surveillance system
- Dimension 3: Impact of the OH surveillance system

Some of the features of the tool include:
- Evaluation of 'OH-ness' across the three dimensions
- Interactive visualisation of results
- Benchmarking tool to compare to other One Health Surveillance systems

The OH-EpiCap tool has been developed by the MATRIX consortium, a joint integrative project funded by the One Health European Joint Programme. The MATRIX consortium aims to advance the implementation of OH surveillance in practice, by building onto existing resources, adding value to them, and creating synergies among the sectors at the national level. One activity has been the development of the generic benchmarking tool presented here, for characterizing, monitoring, and evaluating epidemiological surveillance capacities and capabilities, which directly contribute to OH surveillance. The tool aims to identify and describe the collaborations among actors involved in the surveillance of a hazard and to characterize the OH-ness of the surveillance system. The tool will support identification of areas that could lead to improvements in existing OH surveillance capacities.

More information is available here: <a href="https://onehealthejp.eu/wp-content/uploads/2022/11/OHEJP-MATRIX_OH-EpiCap-flyer.pdf" target="_blank">OH-EpiCap tool flyer</a> and <a href="https://onehealthejp.eu/wp-content/uploads/2022/06/OHEJP_MATRIX_OH-EpiCap_user_guide_2022_06.pdf" target="_blank">OH-EpiCap tool user guide</a>.

## Prioritisation tool for targeting the monitoring of veterinary pharmaceuticals in soils (INIA, Spain)
**<a href="https://eisg-apps.shinyapps.io/App_for_SM/" target="_blank">https://eisg-apps.shinyapps.io/App_for_SM/</a>**

Since most veterinary antibiotics employed in livestock production are excreted essentially unaltered, they have been identified as major contributors of environmental contamination. Specifically, the presence of antimicrobial resistance (AMR) determinants has been recognised as a global hazard. However, the efforts of monitoring antimicrobial and AMR are focused on humans and livestock, neglecting the environment. Although selected substances are monitored in surface and ground-waters under the Water Framework Directive, no European regulatory framework for antibiotics contamination in soils is currently in place.

The European Union institutions recognized this gap. In March 2019, the European Commission adopted the EU Strategic Approach to Pharmaceuticals in the Environment (2019), which is a component of the European Union's One Health Action Plan against Antimicrobial Resistance. One of the key points of PiE is the prioritisation of cost-effective monitoring of antimicrobials and antimicrobial resistances in water, soil, sediments, and wildlife using innovative strategies, such as advanced modelling and information technology (IT)-based tools and platforms.

In this frame, this approach offers a prototype prioritisation tool applicable to soils to identify which sampling sites and antibiotics require more attention as part of monitoring efforts. It is an open source, providing dashboard features in a graphical user interface (Shiny App). To facilitate the implementation of the method in other EU countries, for which appropriate data are available, a script in R to run the model is available.

### Method
The model is described in detail in an open journal: Rodríguez, A., Iglesias, I., de la Torre, A. (2022). Prioritisation tool for targeting the monitoring of veterinary pharmaceuticals in soils at a national level: The case of Spain. European Journal of Soil Science, 73(4), e13268. <a href="https://doi.org/10.1111/ejss.13" target="_blank">https://doi.org/10.1111/ejss.13</a>.

### Data
The approach comprises three steps: antibiotic load estimation, antibiotic fate estimation and soil vulnerability, giving an approximation of the likelihood of antibiotic presence in soils. It was applied to two different scenarios corresponding to the main methods of manure management in soils: (i) manure produced by intensively reared animals is applied as fertiliser to agricultural soils, and (ii) manure is added directly to pastures by animals kept outdoors for much or most of their lives.

Antibiotic load estimation consisted of the combination of antibiotic use data by livestock species and their geographical census in the crop land and pasture scenarios. Antibiotic fate was estimated in terms of persistence as a primary measure of an antibiotic's potential to contaminate soils. Soil vulnerability integrates antibiotic load and antibiotic fate to approximate the likelihood that an antibiotic occurs in soil.

### Technical implementation
The model has been developed in R code. It estimates antibiotic load, fate and soil vulnerability. The script works from the following input parameters: livestock population, antibiotic excretion rate and use proportion, Koc and DT50, as well as crop land and pasture scenarios. The script generates vulnerability maps by livestock species, antibiotics and scenarios

A web interface is available in a local Shiny app which provides a user interface for interactively investigating the vulnerability maps at different livestock productions and scenarios.


## RESAPATH online (ANSES, France)
**<a href="https://shiny-public.anses.fr/ENresapath2/" target="_blank">https://shiny-public.anses.fr/ENresapath2/</a>**

The RESAPATH is the French network for surveillance of antimicrobial resistance (AMR) in bacterial pathogens isolated from diseased animals. It monitors AMR rates and trends in France.

### Data

Data collected include all the results of antibiotic susceptibility tests carried out by RESAPATH member laboratories at the request of practicing veterinarians in the context of their health care activities.
Resapath data are freely accessible via an interactive open-access web English interface.

### Layout & implementation

This dashboard, updated once a year in the fall, was designed with R Shiny (a library of web development for the statistical software R). A custom stylesheet in CSS was developed to improve visual appeal. Graphs were created using specific R libraries (ggplot2, plotly).
This interface allows the visualization of results by selecting different combinations of interest (year/animal species/bacteria/pathology/antibiotic). Data are presented through three tabs:

- General data: number of antibiograms;
- Antimicrobial susceptibility tables: proportion of susceptible strains;
- Trends: curves of temporal evolution of the proportions of susceptible isolates with their 95% confidence intervals.
All graphs are downloadable as images along with their associated data in Excel© format.

## SARS-BOARD (INIA-CSIC, Spain)
**<a href="https://www.arcgis.com/apps/dashboards/1ddf56d1b9764372a7d5ff4e83485174" target="_blank">https://www.arcgis.com/apps/dashboards/1ddf56d1b9764372a7d5ff4e83485174</a>**

The aim of the SARS-BOARD dashboard is to provide an interactive tool for exploring SARS-CoV-2 outbreaks in all types of animals (captive, domestic, wild and pets).

The dashboard was authored by the <a href="https://www.inia.es/investigacion/animal/sanidad/Epidemiolog%C3%ADa y sanidad ambiental/Pages/Home_old.aspx?PageName=Epidemiolog%C3%ADa%20y%20sanidad%20ambiental" target="_blank">Epidemiology and Environmental Health</a> group at the Center for Animal Health Research (CISA), INIA-CSIC. It was funded by and developed within the OHEJP <a href="https://onehealthejp.eu/jip-covrin/" target="_blank">COVRIN</a> project. GIS development was done by [Innvel](http://www.innvel.com/en/). The technical platform of choice was <a href="https://www.arcgis.com/index.html" target="_blank">ArcGIS</a>.

### Data Sources

- SARS-CoV-2 outbreaks: World Animal Health Information System (<a href="https://wahis.woah.org/#/home" target="_blank">WAHIS</a>) of the World Organisation for Animal Health (WOAH, formerly OIE). Weekly download of notifications.
- Climate data: Climate Data Online (<a href="https://www.ncei.noaa.gov/cdo-web/" target="_blank">CDO</a>)
- Socioeconomical factors: <a href="https://www.worldbank.org/en/home" target="_blank">World Bank Data</a>

### Definitions of Animal Types

- Captive: Refers to wild animals with phenotypes unaffected by human selection but that are captive, for example zoo animals
- Domestic: Livestock or farms (including fur farms)
- Wild: an animal that has a phenotype unaffected by human selection and lives independent of direct human supervision or control. Included here are feral animals (animals of a domesticated species that now live without direct human supervision or control)
- Pets: animals that live directly under human supervision or control, typically for companionship (dogs, cats, rabbits, etc.)

### Layout

The SARS-BOARD contains three tabs:

1.	The historical outbreak records tab is the main page for exploring and visualising data. This section includes map of SARS-CoV-2 outbreaks in animals from 2020 to present at the top, a time slider of outbreak notifications at the bottom, and a list of interactive graphics on the right related to the region of the total or selection of outbreaks that could be developed in the map or in the time graphic. The time slider tool enables users to wind back time and view the global situation at any given moment since 2020, as well as to select time periods by species and regions. By clicking on any outbreak, a pop-up window with outbreak information appears.
2.	The tab "Country data” includes an interactive historical map of monthly mean temperatures and SARS-CoV-2 outbreaks in animals. Each monthly temperature layer can be turned on and off as an interactive background map. Potential socioeconomic factors related to SARS-CoV-2 outbreaks notifications in animals have been included.
3.	The tab "World globe" allows users to explore SARS-CoV-2 outbreak notifications in animals on the entire globe including a place search tool.


## Sykdomspulsen One Health (NIPH & NVI, Norway)

The Sykdomspulsen One Health website is a pilot project for the surveillance of Campylobacter infections in Norway. It is a collaboration between the Norwegian Institute of Public Health, the Norwegian Veterinary Institute and the Norwegian Food Safety Authorities. It is currently a closed website.

### Data
We are using doctor’s consultation symptomatic data, Campylobacter tests of broiler flocks and weather data to forecast potential gastro-intestinal outbreaks in humans. Every week, all data is being automatically retrieved, cleaned, analysed and displayed as graphs and maps on the website. The testing of broiler flocks started in 2006 and runs every year from May to October. More information is available in a poster presented at the University of Oslo for the 2021 One Health in the 21st century conference (<a href="https://www.med.uio.no/helsam/english/research/centres/global-health/news-and-events/events/2021/posters-webpage.pdf" target="_blank">see page 3</a>).

### Layout
The website is structured in a traditional way, with a navigation bar at the top of the page, and a set of tabs and subtabs to structure information. There are different sections for gastro-intestinal diseases in Norway, Campylobacter-specific surveillance, general information on One Health, and a glossary based on the OneHealth ORION Glossary. Data and forecasts are being displayed as interactive graphs and maps where the user can choose the time frame and geographical area of their choice.

### Implementation
The website is developed entirely with Shiny, a library of web development for the statistical software R. Additionally, we wrote a custom stylesheet in CSS to improve visual appeal and user-friendliness. Graphs and maps make use of some specific R libraries (leaflet, fhimaps, fhiplot, ggplot2). The automatization of data flow is handled by Sykdomspulsen Analytics, which is an implementation of the generic Sykdomspulsen Core framework (available in the form of an open-source R package). It requires a linux server, a database, and a set of container images (i.e. lightweight virtual machines). More information can be found <a href="https://docs.sykdomspulsen.no/" target="_blank">here</a>.

## TSIS – TierSeuchenInformationsSystem / Animal Diseases Information System (FLI, Germany)
**<a href="https://tsis.fli.de/" target="_blank">https://tsis.fli.de/</a>**

The TierSeuchenInformationsSystem (TSIS), otherwise known as the Animal Diseases Information System, makes up-to-date information on notifiable animal diseases in Germany available to the public. The system allows for interactive searching of animal disease outbreaks in Germany, provides information on the status of notifiable infectious animal diseases in Germany and respective restriction zones.
Notifiable animal diseases are infections of animals that are subject to national control programmes due to their economic importance or their risks for livestock or human health. In Germany, control measures are implemented by the federal states (Länder). The competent veterinary authorities must notify the Federal Ministry of Food and Agriculture about all animal disease outbreaks that occur in their area of responsibility. Notification occurs via electronic data transmission through use of the software "TSN", i.e. TierSeuchenNachrichten System (animal disease information system), which is only accessible to the approved authorities.


However, these notifications form the basis of the Animal Disease Information System (TSIS) and make appropriate information on the current animal health situation in Germany accessible to the public. TSIS also contains information on previous animal disease outbreaks, individual epidemics and the functioning of national control measures. As a result, TSIS provides all those interested in animal health with quick and easy access to up-to-date information on the animal health situation in Germany.

### Data and technical implementation
Notifiable animal disease data are collected into TSN, a relational database management system based on the Microsoft SQL server software. Limited data from TSN, including the disease, the species affected, the state and district within which the disease occurred, the date of detection and any restriction zones implemented in response to the notification are made available to the public through the TSIS web interface. The TSIS web interface uses the ASP.NET framework software and (C#) programming language.


### Layout
The TSIS web interface is structured with a navigation bar at the top of the page with menu options ‘*Startseite*’(Home page), ‘*Tierseuchenlage*’(Animal disease situation), ‘*Service*’(Resources) and ‘*Impressum*’(About). The option ‘*Tierseuchenlage*’ provides the user with three further options ‘*Tiersucheninformationen*’ (Animal disease information), '*Amtlicher Monatsbericht*’ (Official Monthly report) and ‘*Tiergesundheitsjahresberichte*’ (Animal health annual reports). When the user selects the option ‘*Tiersucheninformationen*’ they are taken to a page presenting all the notifiable diseases for which a report is available. If the user then selects a disease of interest from the list, they arrive at a page listing all the reports available for that disease. The user can filter the information by case status (active or inactive), animal type (domestic or wild), disease occurrence date (can be a range), location (state and/or region), pathogen details, and/or association with a restriction zone. The data are visualised in tabular form. Cases can also be visualised geographically through overlay over a map of Germany. At this time, the data can not be exported, however, planned updates to the system will allow this function in the future.

## Netherlands

No dashboard reported as of yet.

## Poland

No dashboard reported as of yet.

## Portugal

Considering the One Health concept there is not any report which includes human, animal and environmental health. However, there are reports for human and animal health separately.

Regarding the human health reports, they are annually published by the General Directorate of Health (<a href="https://www.dgs.pt/" target="_blank">DGS</a>) and are related to viral hepatitis, tuberculosis and prevention and control of infections and antimicrobial resistance.

Concerning the animal health reports, they are annually published by the General Directorate of Food and Veterinary (<a href="https://www.dgav.pt/" target="_blank">DGAV</a>) and are related to some zoonoses that affect the animals in Portugal, such as bovine tuberculosis, bovine brucellosis, salmonella, among others.

At this moment, a dashboard that includes animal and human health is not planned.

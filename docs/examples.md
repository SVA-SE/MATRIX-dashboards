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
The models are based on Bayesian statistical methods and implemented by Markov Chain Monte Carlo (MCMC) simulations. The mathematical models are described in detail in open journal: https://www.mdpi.com/2304-8158/10/11/2520, and the corresponding matching model code at [https://github.com/jukran/BIKE](https://github.com/jukran/BIKE).

### Data
Consumption data for named food types and hazard occurrence data for the same food types. The user is required to provide data on dietary records for a representative sample of individuals for at least two days per individual, showing the consumed amounts (positive or zero) of each named food type per day. Additionally, hazard concentrations (a set of measurements) and possibly hazard prevalence data for the corresponding food types are needed. A few combinations and alternative interpretations of data are allowed, e.g. concerning values below or between measurement limits. Also processing factors can be applied, affecting prevalence and/or concentration at the time of consumption.

### Technical implementation
The model utilizes both R and OpenBUGS, which need to be installed first. The R code reads data from user given files, and then formats and analyses the data. Based on this, it writes a data-specific OpenBUGS code for implementing the Bayesian model simulations, according to the data structure found, and calls OpenBUGS to perform the MCMC simulations accordingly. After the MCMC simulations are done, the results are processed in R, and they are visualised in a local Shiny app which provides a user interface for interactively investigating the hazard-food exposure pairs, or total exposure from several foods, or concentrations, or consumptions.

## Disease Dashboards (SVA, Sweden)

The National Veterinary Institute (SVA) is the largest veterinary laboratory in Sweden. Every day our microbiology, pathology and sequencing departments analyse a large amount of samples, which in turn produces large amount of data. These data need to be summarised and translated into actionable information in order to fulfil one our main missions: surveillance communication. We need to effectively communicate the epidemiological situation of Sweden to disease experts, as well as animal owners and the general public.

[Surveillance of infectious diseases in animals and humans](https://www.sva.se/amnesomraden/smittlage/sjukdomsrapporter-om-sva-s-overvakning/) ("the surveillance report") is the annual report describing the surveillance activities carried out in Sweden during the year. The report covers surveillance for important animal diseases and zoonotic agents in humans, food, feed and animals, carried out and compiled by experts from several Swedish governmental agencies, university and private industry with surveillance mandates along the entire food chain, from farm to fork. The surveillance report is published by the National Veterinary Institute (SVA), in collaboration with the Swedish Board of Agriculture, the Public Health Agency and the Swedish Food Agency.

To better highlight the important findings presented in the report, and to strengthen the "one health-ness" of the surveillance, SVA is now planning to translate the contents of chapters describing hazards of great interest into interactive online Disease Dashboards. These dashboards will collect all our available knowledge about a specific pathogen, both historically and the current situation.

### Data
The data presented in these disease dashboards will come from two main sources:

* The surveillance report, which provides manually curated datasets and expert analyses on an annual basis. This will provide a historical overview and in-depth conclusions about the status of the disease.
* Our internal LIMS systems and databases, which are updated daily. This will give a snapshot of the current situation, allowing experts to obtain information and take action in a timely and robust manner.

### Layout
The dashboards will be structured as a traditional side-menu website, with different tabs covering different topics. It will have full interactive capabilities, meaning that all data-driven content (maps, tables, graphs, etc) can be filtered and customised to the user's needs.

### Technical implementation
The dashboard will be developed using a combination of R, JavaScript and CSS. An in-house R package has been developed to produce static graphs, maps and tables for the surveillance report; this will be adapted so that it can also be used to create dynamic JavaScript-powered HTML widgets, something which is easily achievable without leaving the R environment. Another in-house R package exists for analysing and summarising the daily lab data, which is currently used to update standalone maps, graphs and tables on the external web; this package will be expanded on to provide content for the disease dashboards. For greater customisation of design and behaviour, a layer of custom JavaScript and CSS will be added on top of the R-generated content. The content will then be brought together into a full web application using the [R Shiny](https://shiny.rstudio.com/) package. The app will be hosted on an internal virtual server and made available through an Internet connection. It will be possible to control the access to the dashboards, ranging from specific users within SVA to the entire public. The plan is to establish a localised access control so that, for example, certain tabs may be available publicly while others require authentication.

## FoodChain-Lab (BfR, Germany)
**[https://foodrisklabs.bfr.bund.de](https://foodrisklabs.bfr.bund.de)**

FoodChain-Lab (FCL) is a free and open-source software tool aimed to support trace-back and trace-forward analysis of implicated feed or food items along supply chains as well as exposure and risk assessments in foodborne incidents (outbreaks, chemical contaminations).
Implementation: 
The desktop version of FCL has been implemented as a modular extension to the open source data analytics platform Konstanz Information Miner (KNIME). KNIME enables visual assembly of data analysis workflows. These workflows consist of so-called nodes and edges. Each node is able to perform a specific data processing task while edges define how information flow is directed between nodes. FCL is also available as a web application ([FCL Web](https://fcl-portal.bfr.berlin)).

FoodChain-Lab was created in 2011 and has been running and constantly developing with the support of third projects. From 2023 onward, FCL will be supported by EFSA and BfR for further improvements.

### Data
FCL Desktop collects and imports data into an internal database by generating semi-filled Excel templates that can be sent to local authorities for data completion and afterwards be imported into the database, or through a direct interface to the database for manual data input. Once the data is transferred into the database it can be validated and updated. FCL Web uses a JSON-based data format and is fed with data from FCL Desktop or other food tracing software systems.

### Layout
A major application of FCL Desktop and FCL Web is the analysis and visualization of food tracing information. This is accomplished by the construction and visualization of interactive food chain network graphs consisting of nodes (stations such as food business operators or disease cases) and edges (food product transportation events, deliveries). A score calculated for all stations and deliveries helps to identify the source of a foodborne contamination and prioritize next investigation steps. All visualizations are interactive and can be exported as data tables or images for use in other KNIME nodes, other tools or in reports. Detailed description of FCL is available at the website (link above).

## GENPAT (IZS, Italy)
**[https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis](https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis)**

The “National Reference Centre for Whole Genome Sequencing of microbial pathogens: database and bioinformatic analysis” (GENPAT) manages, on behalf of the Italian Ministry of Health, a national platform for collection and sharing of microbial pathogen WGS data from animal, food and environmental isolates and for performing bioinformatic analyses.

The platform supports and assists the Italian Ministry of Health and competent authorities in technical and scientific claims, providing IT tools and data that are quickly available, usable and helpful in outbreak situations allowing to link molecular typing and bioinformatics analyses results with time and position of sampling as well as the other epidemiological information available. The system is a web-based information system with three main components:

- Data component: Based on CMDBuild, an open-source web enterprise environment used to configure custom applications and to manage databases of items. It has native mechanisms to model its internal database, design workflow, configure reports, build connectors with external systems and so on.
- Calculation engine component: Nextflow enables scalable and reproducible scientific workflows using software containers. It allows the adaptation of pipelines written in the most common scripting languages. Its fluent DSL simplifies the implementation and deployment of complex parallel and reactive workflows on clouds and clusters.
- Dashboards component: WGS analysis and metadata are combined together in easy-to-use dashboards. For this purpose, a number of well-known, robust open-source projects have been integrated: GrapeTree, Phylocanvas, Openstreetmap, Openlayers.

The GENPAT platform is derived from the OHEJP COHESIVE project results. In particular, it extends the CIS (COHESIVE Information System) for Italian needs. The system has been also used in the national project of the "Italian One-Health JointDB" where a pilot has been conducted on Listeria monocytogenes to integrate data from ISS (storing isolates from human clinical cases) and GENPAT (storing animal, food and environmental isolates) using a mechanism based on federated servers.

## OH-EpiCap tool (ANSES, France & UoS, UK)
**[https://carlijnbogaardt.shinyapps.io/OH-EpiCap/](https://carlijnbogaardt.shinyapps.io/OH-EpiCap/) (temporary URL)**

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

More information is available here: [OH-EpiCap tool flyer](https://onehealthejp.eu/wp-content/uploads/2022/06/OHEJP_MATRIX_OH-EpiCap_flyer_2022_06.pdf) and [OH-EpiCap tool user guide](https://onehealthejp.eu/wp-content/uploads/2022/06/OHEJP_MATRIX_OH-EpiCap_user_guide_2022_06.pdf).

## RESAPATH online (ANSES, France)
**[https://shiny-public.anses.fr/ENresapath2/](https://shiny-public.anses.fr/ENresapath2/)**

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

## Sykdomspulsen One Health (NIPH & NVI, Norway)

The Sykdomspulsen One Health website is a pilot project for the surveillance of Campylobacter infections in Norway. It is a collaboration between the Norwegian Institute of Public Health, the Norwegian Veterinary Institute and the Norwegian Food Safety Authorities. It is currently a closed website.

### Data
We are using doctor’s consultation symptomatic data, Campylobacter tests of broiler flocks and weather data to forecast potential gastro-intestinal outbreaks in humans. Every week, all data is being automatically retrieved, cleaned, analysed and displayed as graphs and maps on the website. The testing of broiler flocks started in 2006 and runs every year from May to October. More information is available in a poster presented at the University of Oslo for the 2021 One Health in the 21st century conference ([see page 3](https://www.med.uio.no/helsam/english/research/centres/global-health/news-and-events/events/2021/posters-webpage.pdf)).

### Layout
The website is structured in a traditional way, with a navigation bar at the top of the page, and a set of tabs and subtabs to structure information. There are different sections for gastro-intestinal diseases in Norway, Campylobacter-specific surveillance, general information on One Health, and a glossary based on the OneHealth ORION Glossary. Data and forecasts are being displayed as interactive graphs and maps where the user can choose the time frame and geographical area of their choice.

### Implementation
The website is developed entirely with Shiny, a library of web development for the statistical software R. Additionally, we wrote a custom stylesheet in CSS to improve visual appeal and user-friendliness. Graphs and maps make use of some specific R libraries (leaflet, fhimaps, fhiplot, ggplot2). The automatization of data flow is handled by Sykdomspulsen Analytics, which is an implementation of the generic Sykdomspulsen Core framework (available in the form of an open-source R package). It requires a linux server, a database, and a set of container images (i.e. lightweight virtual machines). More information can be found [here](https://docs.sykdomspulsen.no/).

## TSIS – TierSeuchenInformationsSystem / Animal Diseases Information System (FLI, Germany)
**[https://tsis.fli.de/](https://tsis.fli.de/)**

The TierSeuchenInformationsSystem (TSIS), otherwise known as the Animal Diseases Information System, makes up-to-date information on notifiable animal diseases in Germany available to the public. The system allows for interactive searching of animal disease outbreaks in Germany, provides information on the status of notifiable infectious animal diseases in Germany and respective restriction zones.
Notifiable animal diseases are infections of animals that are subject to national control programmes due to their economic importance or their risks for livestock or human health. In Germany, control measures are implemented by the federal states (Länder). The competent veterinary authorities must notify the Federal Ministry of Food and Agriculture about all animal disease outbreaks that occur in their area of responsibility. Notification occurs via electronic data transmission through use of the software "TSN", i.e. TierSeuchenNachrichten System (animal disease information system), which is only accessible to the approved authorities.


However, these notifications form the basis of the Animal Disease Information System (TSIS) and make appropriate information on the current animal health situation in Germany accessible to the public. TSIS also contains information on previous animal disease outbreaks, individual epidemics and the functioning of national control measures. As a result, TSIS provides all those interested in animal health with quick and easy access to up-to-date information on the animal health situation in Germany.

### Data and technical implementation
Notifiable animal disease data are collected into TSN, a relational database management system based on the Microsoft SQL server software. Limited data from TSN, including the disease, the species affected, the state and district within which the disease occurred, the date of detection and any restriction zones implemented in response to the notification are made available to the public through the TSIS web interface. The TSIS web interface uses the ASP.NET framework software and (C#) programming language.


### Layout
The TSIS web interface is structured with a navigation bar at the top of the page with menu options ‘*Startseite*’(Home page), ‘*Tierseuchenlage*’(Animal disease situation), ‘*Service*’(Resources) and ‘*Impressum*’(About). The option ‘*Tierseuchenlage*’ provides the user with three further options ‘*Tiersucheninformationen*’ (Animal disease information), '*Amtlicher Monatsbericht*’ (Official Monthly report) and ‘*Tiergesundheitsjahresberichte*’ (Animal health annual reports). When the user selects the option ‘*Tiersucheninformationen*’ they are taken to a page presenting all the notifiable diseases for which a report is available. If the user then selects a disease of interest from the list, they arrive at a page listing all the reports available for that disease. The user can filter the information by case status (active or inactive), animal type (domestic or wild), disease occurrence date (can be a range), location (state and/or region), pathogen details, and/or association with a restriction zone. The data are visualised in tabular form. Cases can also be visualised geographically through overlay over a map of Germany. At this time, the data can not be exported, however, planned updates to the system will allow this function in the future. 


## Denmark

No dashboard to report.

## Netherlands

No dashboard reported as of yet.

## Poland

No dashboard reported as of yet.

## Portugal

Considering the One Health concept there is not any report which includes human, animal and environmental health. However, there are reports for human and animal health separately. 

Regarding the human health reports, they are annually published by the General Directorate of Health ([DGS](https://www.dgs.pt/)) and are related to viral hepatitis, tuberculosis and prevention and control of infections and antimicrobial resistance.

Concerning the animal health reports, they are annually published by the General Directorate of Food and Veterinary ([DGAV](https://www.dgav.pt/)) and are related to some zoonoses that affect the animals in Portugal, such as bovine tuberculosis, bovine brucellosis, salmonella, among others. 

At this moment, a dashboard that includes animal and human health is not planned. 

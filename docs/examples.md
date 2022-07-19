---
layout: default
title: "Practical Dashboard Examples"
nav_order: 6
toc: true
---

# Practical Dashboard Examples

Found in here are practical "real-world" examples of OHS dashboards and tools, developed by members of the MATRIX project.

## Disease Dashboards (SVA, Sweden)

[Surveillance of infectious diseases in animals and humans](https://www.sva.se/amnesomraden/smittlage/surveillance-rapporten-om-sva-s-overvakning/) ("the surveillance report") is the annual report describing the surveillance activities carried out in Sweden during the year. The report covers surveillance for important animal diseases and zoonotic agents in humans, food, feed and animals, carried out and compiled by experts from several Swedish governmental agencies, university and private industry with surveillance mandates along the entire food chain, from farm to fork. The surveillance report is published by the National Veterinary Institute (SVA), in collaboration with the Swedish Board of Agriculture, the Public Health Agency and the Swedish Food Agency.

To better highlight the important findings presented in the report, and to strengthen the "one health-ness" of the surveillance, SVA is now planning to translate the zoonotic chapters into a web-based interactive experience. This gives an opportunity to display data in greater detail and to more dynamically follow the disease situation over time.

### Data
The data presented in these zoonotic dashboards will be manually curated by surveillance experts on each specific disease agent. The data are summarised and presented temporally (time series) and/or spatially (maps).

### Layout
Due to the static and curated nature of the data, and the great detail with which the surveillance is described in the original report, the dashboard will be designed in the style of "story maps" where the interactive elements are accompanied by a text-based story which gives the graphs, maps and tables a context. Examples of this layout style can be found in the [Animal disease profiles]https://animal-diseases.efsa.europa.eu/) published by the European Food Safety Agency (EFSA).

### Technical implementation
The dashboard will be developed using a combination of R, JavaScript and CSS. An in-house R package has been developed to produce static graphs maps and tables for the surveillance report; this will be adapted so that it can also be used to create dynamic JavaScript-powered HTML widgets, something which is easily achievable without leaving the R environment. For greater customisation of design and behaviour, a layer of custom JavaScript and CSS will be added on top of the R-generated content. The content will then be brought together into a full web application using the [R Shiny](https://shiny.rstudio.com/) package. The app will be hosted on an internal virtual server and made publicly available on the Internet.

## FoodChain-Lab (BfR, Germany)
FoodChain-Lab (FCL) is a free and open-source software tool aimed to support trace-back and trace-forward analysis of implicated feed or food items along supply chains as well as exposure and risk assessments in foodborne incidents (outbreaks, chemical contaminations).
Implementation: 
The desktop version of FCL has been implemented as a modular extension to the open source data analytics platform Konstanz Information Miner (KNIME). KNIME enables visual assembly of data analysis workflows. These workflows consist of so-called nodes and edges. Each node is able to perform a specific data processing task while edges define how information flow is directed between nodes. FCL is also available as a web application (FCL Web, https://fcl-portal.bfr.berlin).

### Data
FCL Desktop collects and imports data into an internal database by generating semi-filled Excel templates that can be sent to local authorities for data completion and afterwards be imported into the database, or through a direct interface to the database for manual data input. Once the data is transferred into the database it can be validated and updated. FCL Web uses a JSON-based data format and is fed with data from FCL Desktop or other food tracing software systems.

### Layout
A major application of FCL Desktop and FCL Web is the analysis and visualization of food tracing information. This is accomplished by the construction and visualization of interactive food chain network graphs consisting of nodes (stations such as food business operators or disease cases) and edges (food product transportation events, deliveries). A score calculated for all stations and deliveries helps to identify the source of a foodborne contamination and prioritize next investigation steps. All visualizations are interactive and can be exported as data tables or images for use in other KNIME nodes, other tools or in reports. Detailed description of FCL is available at https://foodrisklabs.bfr.bund.de.


## GENPAT (IZS, Italy)
The “National Reference Centre for Whole Genome Sequencing of microbial pathogens: database and bioinformatic analysis” ([GENPAT](https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis)) manages, on behalf of the Italian Ministry of Health, a national platform for collection and sharing of microbial pathogen WGS data from animal, food and environmental isolates and for performing bioinformatic analyses.

The platform supports and assists the Italian Ministry of Health and competent authorities in technical and scientific claims, providing IT tools and data that are quickly available, usable and helpful in outbreak situations allowing to link molecular typing and bioinformatics analyses results with time and position of sampling as well as the other epidemiological information available. The system is a web-based information system with three main components:

- Data component: Based on CMDBuild, an open-source web enterprise environment used to configure custom applications and to manage databases of items. It has native mechanisms to model its internal database, design workflow, configure reports, build connectors with external systems and so on.
- Calculation engine component: Nextflow enables scalable and reproducible scientific workflows using software containers. It allows the adaptation of pipelines written in the most common scripting languages. Its fluent DSL simplifies the implementation and deployment of complex parallel and reactive workflows on clouds and clusters.
- Dashboards component: WGS analysis and metadata are combined together in easy-to-use dashboards. For this purpose, a number of well-known, robust open-source projects have been integrated: GrapeTree, Phylocanvas, Openstreetmap, Openlayers.

The GENPAT platform is derived from the OHEJP COHESIVE project results. In particular, it extends the CIS (COHESIVE Information System) for Italian needs. The system has been also used in the national project of the "Italian One-Health JointDB" where a pilot has been conducted on Listeria monocytogenes to integrate data from ISS (storing isolates from human clinical cases) and GENPAT (storing animal, food and environmental isolates) using a mechanism based on federated servers.

## OH-EpiCap dashboard (ANSES, Fance & UoS, UK)

To be reported.

## RESAPATH online (ANSES, France)

To be reported.

## Sykdomspulsen (NIPH & NVI, Norway)

The Sykdomspulsen One Health website is a pilot project for the surveillance of Campylobacter infections in Norway. It is a collaboration between the Norwegian Institute of Public Health, the Norwegian Veterinary Institute and the Norwegian Food Safety Authorities. It is currently a closed website.

### Data
We are using doctor’s consultation symptomatic data, Campylobacter tests of broiler flocks and weather data to forecast potential gastro-intestinal outbreaks in humans. Every week, all data is being automatically retrieved, cleaned, analysed and displayed as graphs and maps on the website. The testing of broiler flocks started in 2006 and runs every year from May to October. More information is available in a poster presented at the University of Oslo for the 2021 One Health in the 21st century conference ([see page 3](https://www.med.uio.no/helsam/english/research/centres/global-health/news-and-events/events/2021/posters-webpage.pdf)).

### Layout
The website is structured in a traditional way, with a navigation bar at the top of the page, and a set of tabs and subtabs to structure information. There are different sections for gastro-intestinal diseases in Norway, Campylobacter-specific surveillance, general information on One Health, and a glossary based on the OneHealth ORION Glossary. Data and forecasts are being displayed as interactive graphs and maps where the user can choose the time frame and geographical area of their choice.

### Implementation
The website is developed entirely with Shiny, a library of web development for the statistical software R. Additionally, we wrote a custom stylesheet in CSS to improve visual appeal and user-friendliness. Graphs and maps make use of some specific R libraries (leaflet, fhimaps, fhiplot, ggplot2). The automatization of data flow is handled by Sykdomspulsen Analytics, which is an implementation of the generic Sykdomspulsen Core framework (available in the form of an open-source R package). It requires a linux server, a database, and a set of container images (i.e. lightweight virtual machines). More information can be found [here](https://docs.sykdomspulsen.no/).

## Denmark

No dashboard to report.

## Finland

No dashboard reported as of yet.

## Germany

No dashboard reported as of yet.

## Netherlands

No dashboard reported as of yet.

## Poland

No dashboard reported as of yet.

## Portugal

Considering the One Health concept there is not any report which includes human, animal and environmental health. However, there are reports for human and animal health separately. 

Regarding the human health reports, they are annually published by the General Directorate of Health ([DGS](https://www.dgs.pt/)) and are related to viral hepatitis, tuberculosis and prevention and control of infections and antimicrobial resistance. 

Concerning the animal health reports, they are annually published by the General Directorate of Food and Veterinary ([DGAV](https://www.dgav.pt/)) and are related to some zoonoses that affect the animals in Portugal, such as bovine tuberculosis, bovine brucellosis, salmonella, among others. 

At this moment, a dashboard that includes animal and human health is not planned. 

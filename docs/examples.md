---
layout: default
title: "Practical Dashboard Examples"
nav_order: 5
toc: true
---

# Practical Dashboard Examples

Found in here are practical examples of OHS dashboards, from all the countries participating in MATRIX WP6.

## Denmark

## Finland

## France

## Germany

## Italy
The “National Reference Centre for Whole Genome Sequencing of microbial pathogens: database and bioinformatic analysis” ([GENPAT](https://www.izs.it/IZS/Centres_of_excellence/National_Centres/National_Reference_Centre_for_Whole_Genome_Sequencing_of_microbial_pathogens_database_and_bioinformatic_analysis)) manages, on behalf of the Italian Ministry of Health, a national platform for collection and sharing of microbial pathogen WGS data from animal, food and environmental isolates and for performing bioinformatic analyses.

The platform supports and assists the Italian Ministry of Health and competent authorities in technical and scientific claims, providing IT tools and data that are quickly available, usable and helpful in outbreak situations allowing to link molecular typing and bioinformatics analyses results with time and position of sampling as well as the other epidemiological information available. The system is a web-based information system with three main components:

- Data component: Based on CMDBuild, an open-source web enterprise environment used to configure custom applications and to manage databases of items. It has native mechanisms to model its internal database, design workflow, configure reports, build connectors with external systems and so on.
- Calculation engine component: Nextflow enables scalable and reproducible scientific workflows using software containers. It allows the adaptation of pipelines written in the most common scripting languages. Its fluent DSL simplifies the implementation and deployment of complex parallel and reactive workflows on clouds and clusters.
- Dashboards component: WGS analysis and metadata are combined together in easy-to-use dashboards. For this purpose, a number of well-known, robust open-source projects have been integrated: GrapeTree, Phylocanvas, Openstreetmap, Openlayers.

The GENPAT platform is derived from the OHEJP COHESIVE project results. In particular, it extends the CIS (COHESIVE Information System) for Italian needs. The system has been also used in the national project of the "Italian One-Health JointDB" where a pilot has been conducted on Listeria monocytogenes to integrate data from ISS (storing isolates from human clinical cases) and GENPAT (storing animal, food and environmental isolates) using a mechanism based on federated servers.


## The Netherlands

## Norway

## Poland

## Portugal

Considering the One Health concept there is not any report which includes human, animal and environmental health. However, there are reports for human and animal health separately. 

Regarding the human health reports, they are annually published by the General Directorate of Health ([DGS](https://www.dgs.pt/)) and are related to viral hepatitis, tuberculosis and prevention and control of infections and antimicrobial resistance. 

Concerning the animal health reports, they are annually published by the General Directorate of Food and Veterinary ([DGAV](https://www.dgav.pt/)) and are related to some zoonoses that affect the animals in Portugal, such as bovine tuberculosis, bovine brucellosis, salmonella, among others. 

At this moment, a dashboard that includes animal and human health is not planned. 

## Sweden

[Surveillance of infectious diseases in animals and humans](https://www.sva.se/amnesomraden/smittlage/surveillance-rapporten-om-sva-s-overvakning/) ("the surveillance report") is the annual report describing the surveillance activities carried out in Sweden during the year. The report covers surveillance for important animal diseases and zoonotic agents in humans, food, feed and animals, carried out and compiled by experts from several Swedish governmental agencies, university and private industry with surveillance mandates along the entire food chain, from farm to fork. The surveillance report is published by the National Veterinary Institute (SVA), in collaboration with the Swedish Board of Agriculture, the Public Health Agency and the Swedish Food Agency.

To better highlight the important findings presented in the report, and to strengthen the "one health-ness" of the surveillance, SVA is now planning to translate the zoonotic chapters into a web-based interactive experience. This gives an opportunity to display data in greater detail and to more dynamically follow the disease situation over time.

### Data
The data presented in these zoonotic dashboards will be manually curated by surveillance experts on each specific disease agent. The data are summarised and presented temporally (time series) and/or spatially (maps).

### Layout
Due to the static and curated nature of the data, and the great detail with which the surveillance is described in the original report, the dashboard will be designed in the style of "story maps" where the interactive elements are accompanied by a text-based story which gives the graphs, maps and tables a context. Examples of this style can be found in the [vector-borne disease journals](https://efsa.maps.arcgis.com/apps/PublicGallery/index.html?appid=dfbeac92aea944599ed1eb754aa5e6d1) published by the European Food Safety Agency (EFSA).

### Technical implementation
The dashboard will be developed using a combination of R, JavaScript and CSS. An in-house R package has been developed to produce static graphs maps and tables for the surveillance report; this will be adapted so that it can also be used to create dynamic JavaScript-powered HTML widgets, something which is easily achievable without leaving the R environment. For greater customisation of design and behaviour, a layer of custom JavaScript and CSS will be added on top of the R-generated content. The content will then be brought together into a full web application using the [R Shiny](https://shiny.rstudio.com/) package. The app will be hosted on an internal virtual server and made publicly available on the Internet.

## United Kingdom

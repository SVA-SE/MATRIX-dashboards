---
layout: default
title: "Step-by-Step Guide"
nav_order: 2
---

# Developing an OHS Dashboard: A Step-by-Step Guide
{: .no_toc }

<details open markdown="block">
  <summary>
    Contents
  </summary>
  {: .text-delta }
1. Contents
{:toc}
</details>

So you want to build a dashboard? Where to begin? This guide aims to answer that question and help you through the process of developing a dashboard for OHS. Some sections of the guide will refer to other sections of the Information Centre for practical examples and further reading.

To achieve an optimal result, there are certain factors that need to be addressed in the various phases of the dashboard development process. These can be divided into three stages: 1) planning the dashboard, 2) constructing the dashboard, and 3) dashboard maintenance and outreach.

## Planning the Dashboard

In the planning phase, there are two aspects which need to be considered: the aim of the dashboard, and its intended user groups. These are closely linked together and will determine what kind of dashboard should be developed.
    
### Aim of the Dashboard

The first question to ask is "why do we need a dashboard?" The aim of the dashboard and the issue which that aim is intended to address, should be as clear and specific as possible. This affects the rest of the development process, including data customisation, dashboard layout and which information to present.

### User Groups

Identifying the target groups that will use the dashboard is equally, if not more, important. Together with the aim, this informs which type of content to display in the dashboard so that it becomes an interesting and relevant tool for the user groups, while also being targeted to their level of expertise on the subject. A dashboard for the general public will look different from one intended to be used by topic experts, even if the underlying data is the same.

There are three interest groups involved in the planning of a dashboard: those who develop it, those who requested it, and those who will use it. While these groups could be the same, that is not necessarily the case. Therefore it is important to understand the relationship between these interests as they should all be represented in the planning and development of the dashboard.

Once the target user groups have been identified, it is important to pinpoint their needs and how the dashboard can help them fulfil those -- which also ties into the aim of the dashboard. The best way to go about this is not to think "what information would the user want?" and attempt to guess what kind of dashboard would achieve that, but rather ask "who is my user? What do they do and what do they need?" Spending time on getting to know the user in the planning phase will result in a more organic development process and save time for the developers. This co-conception can be achieved in a variety of ways depending on who the user groups are, including but not limited to surveys, interviews, or establishing a dashboard reference group with representatives from the users, developers and those who requested the dashboard (see more on reference groups below). The latter is especially useful if the dashboard is intended to be used by a specific group (e.g., disease or health experts) but may not be applicable if the target user group is a wider audience, such as the general public.

## Developing the Dashboard

A dashboard consists of two components: the collection and processing of data (backend), and the visual representation of that data in an interactive website (frontend). Depending on the situation, the available data and the backend system for delivery of that data may or may not be in the control of the dashboard developers, which will influence the development of the dashboard and which information can be displayed in the frontend.

### Backend Infrastructure and Data

If development and maintenance of the backend data system is not within the scope of the dashboard project, the developer group needs to be sure of what data are available, as well as the status of the data delivery system, before the dashboard development starts. Proceeding with the frontend development before the backend system is up and running may result in having to go back and redo previous work to adapt the graphical interface to the data system.

There is a need for an infrastructure or statistical tool that can organise, analyse and produce readily available data that can be used in the dashboard. An important aspect for this is how often the data should be updated (e.g., hourly, daily, weekly), which is often dependent on whether the update will happen manually or automatically. If done automatically, the backend system must be built to handle this, while if the updates will be done manually, it is essential to ensure that there is enough personnel to update the data regularly enough for the purposes of the dashboard. Whether or not the responsibility of the backend lies with the dashboard development team, it is necessary to ensure that the system has the technical compliance for supplying the dashboard and that it is built to maintain continuity and integrity. This can be achieved by detailing the specifications of the data system in a standard operating procedure (SOP). Creating a contingency plan to ensure data uptime and integrity in case of unexpected events is also beneficial. This plan should include routines for regular backup of data and how to restore this backup in the event of a disaster.

What data will be processed and presented in the dashboard depends both on what the user groups have determined as important to achieve the identified aims as well as what data are or will be available. A privacy and confidentiality assessment must also be made to determine what and how data can legally be used and presented, especially if the dashboard is going to be publicly available.

How to analyse data and in which form it should be presented are also important aspects, especially if multiple sources are going to be shown together. Datasets with the same age groups, geographical regions, time aggregation, etc, are often easier to combine and provide a more coherent picture for the users. In a One Health context, one usually needs to combine and co-analyse data from several sectors which may use different methodologies, definitions and ways of aggregating data. The challenge of analysing multisectoral data while avoiding potential pitfalls and biases is covered in the "[One Health Data](https://sva-se.github.io/MATRIX-dashboards/docs/data/)" section of this Information Centre.

### Dashboard frontend

The most appropriate choice of a frontend platform for a particular dashboard project depends on several factors. Availability of resources has a major impact on this decision, both in terms of infrastructure (e.g., for hosting) and knowledge of the development, as well as financial resources. Third-party solutions require a paid license, a cost that needs to be weighed against potential costs for in-house development (programming manpower being the largest). Another factor to take into account is the structure and complexity of the data as well as potential legal aspects; if the data are sensitive, it may not be desirable to host them on a third-party platform. The matter of dashboard access (and who should have it) also needs to be considered -- control of access un user-level is often easier to control in a locally developed and hosted dashboard, which may be better suited if it should not be made available for a wider audience. Oftentimes, locally developed and hosted dashboards offer a higher level of control of access on the user level, which may be better suited if the dashboard is not intended for a wider audience.

On the technical level, there is a multitude of options to choose between, from writing the website from scratch in [HTML](https://html.spec.whatwg.org/) and [JavaScript](https://www.javascript.com/), to relying on proprietary third-party software such as [ArcGIS](https://www.arcgis.com/index.html), [Tableau](https://www.tableau.com/) or [PowerBI](https://powerbi.microsoft.com/). A popular "middle ground" between these two extremes, which combines the control of "home-made" code with a lower learning threshold and third-party resource support is the [R language for statistical computing](https://www.r-project.org/), along with its [Shiny](https://shiny.rstudio.com/) package for developing interactive interfaces. For a more in-depth description and instruction for how to use R and Shiny for dashboard development, see the "[R Shiny](https://sva-se.github.io/MATRIX-dashboards/docs/r-shiny/)" section of this Information Centre.

The visual design of the dashboard needs to take into account useability, which depends on the needs of the user groups and the aim of the dashboard. Navigation and orientation should be intuitive and not distract from the purpose of the dashboard: to display information efficiently and tell a story. It is also important that the dashboard is accessible, without barriers that prevent interaction or access for those with disabilities or technical restrictions in bandwidth and speed. This is especially important for public dashboards -- it is often a legal requirement for websites produced by the public sector. For more in-depth guidance on dashboard design for useability and accessibility, see the [Design Considerations](https://sva-se.github.io/MATRIX-dashboards/docs/design/) section of this Information Centre.

## Maintenance, Feedback and Outreach

When the dashboard (or a first version of it) has been developed, efforts must be made to make sure that relevant target groups know about it ("spreading the word"), and that it remains up and running and relevant going forward. A dashboard is usually a "living document" which not only needs to be maintained, but also updated with time. For that purpose, it is a good idea to collect feedback from those who use it.

### Maintenance and Sustainability

Much like for the backend, it is a good idea to have a contingency plan to ensure dashboard uptime and sustainability in the long-term. This should detail who is responsible for maintaining both the information content and the technical aspects of the dashboard. If code is developed in-house, it is important that it is properly annotated and documented to facilitate future evolution -- this is useful regardless of whether the development team changes or remains the same.

The choice of a solution for development and hosting also affects the sustainability of the dashboard. While on-premises hosting may be beneficial for information security and control, it requires that resources are available to maintain the infrastructure -- both today and in the future. Increased traffic to the dashboard may require larger investments to ensure a sufficient user experience, which could pose a challenge if resources are scarce. Using a third-party solution usually offers greater stability (provided that the responsible company remains in business), as well as scalability meaning that available storage capacity and bandwidth can be adapted to the traffic in real time. This also comes with a price, but may offer more flexibility than an in-house solution. As with choosing the appropriate development solution, the choice of hosting also depends on the needs of the dashboard and the resources available.

### Feedback Collection

Receiving feedback on the data, design and user friendliness of the dashboard is a very important part of creating an optimal product that is widely used. This can be done using one or a combination of several tools, including questionnaires, site analytics tools (e.g., [Google Analytics](https://analytics.google.com/), but **note** that there may be data protection restrictions regarding the use of such third-party services), meetings, and reference groups (more on that below). Another option could be embedding a feedback and questions and answers (Q&A) form into the dashboard itself. However, this needs to be designed in a non-intrusive way -- actively asking the user for feedback through pop-ups or similar is likely to act as a deterrent and reduce the probability of receiving input.

### Outreach

A dashboard is something that you want people to know about and use. It is therefore important to get in contact and spread the word about the dashboard to the user groups. This can be done through several communication channels, though a combination of these will most probably be best:

-   Reference groups -- spread the word through the people in the reference groups

-   Email information -- to stakeholders

-   Conference -- have a presentation or poster at a conference

-   Web search -- make sure that the dashboard is easy to find through online search engines

-   Contact user groups and ask to hold a presentation about the dashboard

-   Social media posts

It may be beneficial to involve the communications department of the institute where the dashboard is published, as they likely have better resources to handle communication, questions and outreach, and can do so through the institute´s official channels. If so, the communications department should be familiar with the dashboard and how it works so they are prepared to answer questions that may come in or alternatively, who to forward them to.

### Reference Groups

Reference groups consisting of users as well as representatives of all parts of the dashboard development (including communication) could be a very useful tool in all stages of dashboard development: planning, development, feedback and outreach. Direct communication in this form allows the development team to receive direct feedback on the dashboard, while also opening an opportunity to spread the word through the members' extended networks.

Whether or not it is a good idea to establish a reference group depends on the structure of the dashboard development as well as its aim and target user groups. If many interests are involved, it is a very efficient way to make sure everyone is heard informed regarding the status of the project. However, if the target users are a wider audience (such as the public) reference groups may not be a relevant tool to use. Regardless, it is still a good idea to involve the development team in a working group with close connections.


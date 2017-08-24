# Salesforce Marketing Cloud Solution Document

The purpose of this document is to provide a high-level framework for getting started with documenting how to provide a single customer view and associated data integration in Salesforce Marketing Cloud.

Work on this document was largely inspired by a community support collaboration where Salesforce Marketing Cloud Developer Group assisted Autism CRC to setup their Salesforce Marketing Cloud. Supporting documentation for the Autism CRC project is available on request.

## Backlog of work in progress

This document is a work in progress. Additional sections for campaigns, journeys and logging will be added as time permits. 

## How to view document

Formatted document with rended UML diagrams can be viewed [here](https://stackedit.io/viewer#!url=https://gist.githubusercontent.com/mattcam/c67ed65d15b0690af6dafb35d241db3a/raw/f59f220430bab4a8cf7682d660b2dbe724d8bac9/README.md)

# How this document is organised

* [Sample documentation](#sample-salesforce-marketing-cloud-solution-document)
* [Requirements checklist](#requirements-checklist)
* [Requirement specification](#requirement-specification)

The following section provides details for each of the requirements.

# How to use this documentation

Copy and paste, or clone as required. If you find this document useful please star and share SFMCDG. If you can improve pull requests on topic branches are very welcome. Use issues for suggestions.

# Documentation License

This document shared with the [MIT License](https://github.com/sfmcdg/sfmc-solution-document/blob/master/LICENSE).

# Sample Salesforce Marketing Cloud Solution Document

What follows is the sample Salesforce Marketing Cloud Solution Document.

## Document Purpose

The purpose of this document is to describe for client stakeholders the Salesforce Marketing Cloud (SFMC) solution and to provide actionable content for contributors to assist with development.

## Data Integration Model

The following sequence diagram provides a high-level view of how external components interact with the SFMC.

```sequence
External SSOT->SFMC Staging: data import (A.1)
External SSOT->SFMC SCV: data import (A.1)
SFMC Staging->SFMC SCV: map stage to SCV (A.2)
SFMC SCV->SFMC SCV (brand): map SCV to brand specific SCV (A.3)
SFMC SCV->SFMC Campaigns & Applications: map SCV to campaigns (A.4)
SFMC SCV (brand)->SFMC Campaigns & Applications: map SCV [brand] to campaigns (A.4)
SFMC Campaigns & Applications->SFMC SCV: map responses to SCV (A.5)
SFMC SCV-->External SSOT: data export (A.6)
```


### Data Integration Objects

The following section provides a summary of the data integration objects.

| Item | Description |
| - | - |
| External SSOT | Single source of truth is used to represent data warehouse, application or Salesforce instance where customer data is stored. Where SFMC is SSOT then external SSOT is not required. |
| SFMC Staging | Staging is used to represent data extensions that are updated from the SSOT. Staging is optional and will not be required where SSOT maps directly to SCV. |
| SFMC SCV | Single customer view (SCV) is used to represent data extensions in SFMC that are used to store information known about the customer. |
| SFMC SCV (brand) | Brand specific single customer view is used to represent data extensions in SFMC that are used to store a subset of information known about the customer. Brand specific single customer view is optional and is a commonly used with business units in enterprise accounts. |
| SFMC Campaigns & Applications | Used to represent various processes that interact with the customer. Includes for example cloud pages used for preference centres, campaigns used for ad-hoc sends, customer journeys and triggered sends. |

### Data Integration Interactions 

The following section provides a summary of the data integration interactions.

| Item | Title | Description |
| - | - | - |
| (A.1) | Data Import | Automation used to complete ETL load function from data warehouse, Salesforce Marketing Cloud Connector or/and API used import data from SSOT to SFMC staging data extensions. |
| (A.2) | Map Stage to SCV | Automations used to upsert data from staging into single customer view data extension. |
| (A.3) | Map SCV to brand specific SCV | Automations used to select a subset of customer data and project customer records into business units. |
| (A.4) | Map SCV [brand] to campaigns | Automations used to map data to campaigns and journeys. Note that APIs can be used to trigger and fire events that result in data extensions updates. |
| (A.5) | Map responses to SCV | Automations, activities and AMPScript that are used to update SCV with customer responses. |
| (A.6) | Data export | Data file transfer and/or API that is used to update the SSOT. |
  
# Requirements Checklist

The following section provides a checklist of the SFMC solution documentation data integration tasks.

- [ ] A.1 **External SSOT required**
- [ ] A.1.1 SubscriberKey and PrimaryKey relationship defined
- [ ] A.1.2 SCV data extension objects defined
- [ ] A.1.3.1 Data mapped to staging data extensions
- [ ] A.1.3.2 Data mapped to SCV 
- [ ] A.1.4.1 **Data imported using SSOT ETL process**
- [ ] A.1.4.1.1 Is ETL full data load
- [ ] A.1.4.1.2 Is ETL delta data load
- [ ] A.1.4.2 **Data imported using Salesforce Marketing Cloud Connector**
- [ ] A.1.4.2.1 Salesforce objects required for import defined 
- [ ] A.1.4.3 **Data Imported using API**
- [ ] A.1.4.3.1 API methods defined
- [ ] A.2 **Staging data extensions required**
- [ ] A.2.1 Are additional data transformations required on load defined
- [ ] A.3 **Business units required**
- [ ] A.3.1 Business unit strategy defined
- [ ] A.4 **Campaigns data extensions required**
- [ ] A.4.1 Campaign data requirements defined
- [ ] A.5 **Customer response to SCV required**
- [ ] A.5.1 Customer response options defined
- [ ] A.5.1.1 Customer preference centre required
- [ ] A.6 **Data reporting to SSOT required**
- [ ] A.6.1 Scope of SFMC data reporting defined
- [ ] A.6.2.1 Is SFMC data reporting via file transfer
- [ ] A.6.2.2 Is SFMC data reporting via API

Notes: not all tasks are required.

# Requirement specification

The following section contains examples for how to specify Salesforce Marketing Cloud requirements. This document is a work in progress. Additional sections for campaigns, journeys and logging will be added as time permits. Pull requests on topic branches are very welcome.

## A.1 External SSOT required

> replace with description of external data system(s)

### A.1.1 SubscriberKey and PrimaryKey relationship defined

> replace with PrimaryKey to SubscriberKey relationship



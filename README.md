# FHIR in QH Questionnaire Track

This GitHub repository contains information and resources for the Questionnaire track during the two-day FHIR in Queensland Health connectathon in Brisbane on 9-10 October 2025.

## Description

This track explores how FHIR Questionnaires and the Structured Data Capture (SDC) specification can be used to streamline the collection and exchange of clinical data across health systems. In this track you will be:

- Gain an understanding of the architecture for deployment of forms and how they can be used in a user-facing setting
- Explore example implementations, including:
  - Pre-populating Questionnaires with existing patient data
  - Writing responses back into clinical records
  - Enhancing forms with terminology services and value sets to ensure captured data is coded and interoperable across systems
- Explore a Queensland Health use case for a FHIR Questionnaire
- Get hands-on experience in building a FHIR Questionnaire

## Track Lead(s)

- Sean Fong (CSIRO) - sean.fong@csiro.au
- Jacky Hung (QH) - jacky.hung@health.qld.gov.au

## Specification Information

- R4 Questionnaire - https://hl7.org/fhir/R4/questionnaire.html
- R4 QuestionnaireResponse - https://hl7.org/fhir/R4/questionnaireresponse.html
- Structured Data Capture - https://hl7.org/fhir/uv/sdc/

## Resources

- Day 1 Morning Session Slides - WIP
- Track Slides - WIP

## Tools

> **New to FHIR or Questionnaires?**
>
> We recommend having a look at the [Smart Forms documentation](https://smartforms.csiro.au/docs/), especially the [basic components](https://smartforms.csiro.au/docs/components) page.
>
> It includes simple examples based on the FHIR R4 Questionnaire and SDC spec, making it a great resource for a "Hello World" introduction.

#### Smart Forms documentation

View it here: https://smartforms.csiro.au/docs/

For this track, the following pages are most relevant:

- https://smartforms.csiro.au/docs/components
- https://smartforms.csiro.au/docs/sdc

#### Questionnaire-building tools

You can build Questionnaires either by working directly with JSON or by using a visual form builder.

If you are working with an implementation guide (IG), you can use [FSH](https://hl7.org/fhir/uv/shorthand/) too but this will not be covered during the track.

**1. Visual Form Builders**

Build and visualise Questionnaires via a GUI. Good place to start if you're not familiar with the syntax.

- [Aidbox Form Builder](https://form-builder.aidbox.app/) - Freemium, more user-friendly
- [NLM Form Builder](https://formbuilder.nlm.nih.gov/) - Open-source

**2. JSON-based Tools**

Build and visualise Questionnaires directly in JSON. Using AI tools like ChatGPT now makes this process much faster and more efficient.

- [Smart Forms Playground](https://alpha.smartforms.io/playground)

#### Forms Server

This server acts as the central repository for Questionnaires.

Public forms server: https://smartforms.csiro.au/api/fhir (append “/Questionnaire” at the end to view Questionnaires.)

#### Patient Management System (PMS) Server

A Patient Management System (PMS) server provides access to patient and related clinical data to support pre-population and context for Questionnaires.

Public FHIR endpoint for patient data: https://gw.interop.community/QHConnectathon2025/open

#### Terminology Server

A terminology server provides access to FHIR terminology value sets to be used in Questionnaires via [Questionnaire.item.answerValueSet](https://hl7.org/fhir/R4/questionnaire-definitions.html#Questionnaire.item.answerValueSet).

Public terminology server: https://r4.ontoserver.csiro.au/

## Zulip stream (chat.fhir.org)

[chat.fhir.org](https://chat.fhir.org) is a FHIR Community forum/chat platform for FHIR discussion hosted on Zulip.

Feel free to use this Zulip stream to discuss topics, share questions, and collaborate during the event. https://chat.fhir.org/#narrow/channel/179173-australia/topic/Queensland.20Health.20Connectathon.202025/with/536342663

## Testing Scenarios

- Basic Scenario: Launch SMART App from SMART App Host

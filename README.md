# FHIR in QH Questionnaire Track

This GitHub repository contains information and resources for the Questionnaire track during the two-day FHIR in Queensland Health connectathon in Brisbane on 9-10 October 2025.

**Edit 10/10/2025: Looking for links to the SMART on FHIR demo? Check the [SMART on FHIR Demo links](#smart-on-fhir-demo-links) for more information.**

## Description

This track explores how FHIR Questionnaires and the Structured Data Capture (SDC) specification can be used to streamline the collection and exchange of clinical data across health systems. In this track you will:

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
- SMART App Launch - https://hl7.org/fhir/smart-app-launch/app-launch.html

## Resources

- [Day 1 Morning Session Slides](FHIR_in_QH_Morning_Pres_Questionnaire_Track_PDF.pdf)
- [Track Slides](FHIR_in_QH_Questionnaire_KickOff_PDF.pdf)

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

Build and visualise Questionnaires directly in JSON. Using AI tools like ChatGPT makes this process much faster and more efficient.

- [Smart Forms Playground](https://fhir-in-qh.smartforms.io/playground)

#### Forms Server

This server acts as the central repository for Questionnaires.

Public forms server: https://smartforms.csiro.au/api/fhir (append “/Questionnaire” at the end to view Questionnaires.)

#### Patient Management System (PMS) Server

A Patient Management System (PMS) server provides access to patient and related clinical data to support pre-population and context for Questionnaires. We use MELD Sandbox for this connectathon, and it also provides SMART on FHIR capabilities!

**Note: You should have received an email on registering for access to the MELD sandbox. If you did not, please let us know!**

MELD Sandbox: https://meld.interop.community/QHConnectathon2025

Public FHIR endpoint for patient data: https://gw.interop.community/QHConnectathon2025/open

For SMART on FHIR Launch from MELD Sandbox, check out [SMART on FHIR Demo Links](#smart-on-fhir-demo-links).

#### Terminology Server

A terminology server provides access to FHIR terminology value sets to be used in Questionnaires via [Questionnaire.item.answerValueSet](https://hl7.org/fhir/R4/questionnaire-definitions.html#Questionnaire.item.answerValueSet).

Public terminology server: https://r4.ontoserver.csiro.au/

#### FHIRPath Debugging Tool

A simple web-based tool to help you test and debug FHIRPath expressions.

https://fhirpath-lab.com/FhirPath

## SMART on FHIR Demo Links

#### MELD Sandbox

**Note: You should have received an email on registering for access to the MELD sandbox. If you did not, please let us know!**

1. Go to https://meld.interop.community/QHConnectathon2025/apps.
2. Under "FHIR in QH Smart Forms", click "Launch".
3. Choose any persona and any patient. You can add more patients if needed.
4. Step 3 triggers a SMART App Launch sequence to Smart Forms with the selected patient context.
5. IF you see your Patient and User come through in the Smart Forms interface, you're all set!

#### CSIRO EHR Simulator

Allows you to save QuestionnaireResponses and write back a BMI Observation to the patient record.

This is connected to another FHIR server with the patient Kimberly Re-pop (pat-repop), but it gives you a visual demo of writing back to a patient record.

[EHR Simulator demo configured with BMI Calculator Questionnaire](https://ehr.smartforms.io/?fhir_version=r4&launch_url=https%3A%2F%2Ffhir-in-qh.smartforms.io%2Flaunch&app_name=FHIR+in+QH+Smart+Forms+-+Q+Track&tab=0&launch=WzAsInBhdC1yZXBvcCIsInBoYXJtYWNpc3QiLCIiLDAsMCwwLCJsYXVuY2ggb3BlbmlkIGZoaXJVc2VyIG9ubGluZV9hY2Nlc3MgcGF0aWVudC9BbGxlcmd5SW50b2xlcmFuY2UuY3MgcGF0aWVudC9Db25kaXRpb24uY3MgcGF0aWVudC9FbmNvdW50ZXIuciBwYXRpZW50L0ltbXVuaXphdGlvbi5jcyBwYXRpZW50L01lZGljYXRpb24uciBwYXRpZW50L01lZGljYXRpb25TdGF0ZW1lbnQuY3MgcGF0aWVudC9PYnNlcnZhdGlvbi5jcyBwYXRpZW50L1BhdGllbnQuciBwYXRpZW50L1F1ZXN0aW9ubmFpcmVSZXNwb25zZS5jcnVzIHVzZXIvUHJhY3RpdGlvbmVyLnIgbGF1bmNoL3F1ZXN0aW9ubmFpcmU_cm9sZT1odHRwOi8vbnMuZWxlY3Ryb25pY2hlYWx0aC5uZXQuYXUvc21hcnQvcm9sZS9uZXciLCJodHRwczovL2ZoaXItaW4tcWguc21hcnRmb3Jtcy5pbyIsImE1N2Q5MGUzLTVmNjktNGI5Mi1hYTJlLTI5OTIxODA4NjNjMSIsIiIsIiIsIiIsIiIsMCwxLCJbe1wicm9sZVwiOlwiaHR0cDovL25zLmVsZWN0cm9uaWNoZWFsdGgubmV0LmF1L3NtYXJ0L3JvbGUvbmV3XCIsXCJ0eXBlXCI6XCJRdWVzdGlvbm5haXJlXCIsXCJjYW5vbmljYWxcIjpcImh0dHBzOi8vc21hcnRmb3Jtcy5jc2lyby5hdS9kb2NzL3NkYy9leHRyYWN0aW9uL3RlbXBsYXRlLTF8MC4xLjBcIn1dIiwiaHR0cHM6Ly9wcm94eS5zbWFydGZvcm1zLmlvL3YvcjQvZmhpciIsZmFsc2Vd&jwks_tab=0&validation=1)

#### SMART on FHIR demo CodeSandbox

A simple demo app that launches a Questionnaire via SMART on FHIR.

This app uses the [SMART on FHIR JavaScript client library](https://docs.smarthealthit.org/client-js/).

[CodeSandbox App Demo](https://codesandbox.io/p/sandbox/smart-on-fhir-0rd1q)

## Zulip stream (chat.fhir.org)

[chat.fhir.org](https://chat.fhir.org) is a FHIR Community forum/chat platform for FHIR discussion hosted on Zulip.

Feel free to use this Zulip stream to discuss topics, share questions, and collaborate during the event. https://chat.fhir.org/#narrow/channel/179173-australia/topic/Queensland.20Health.20Connectathon.202025/with/536342663

## Testing Scenarios

You can find a FHIR Questionnaire skeleton here: https://smartforms.csiro.au/api/fhir/Questionnaire/FHIRinQHSkeleton. Feel free to use any of the tools listed in [Questionnaire-building tools](#questionnaire-building-tools) to build your questionnaire.

Choose any of the scenarios to tackle — you can work on one or more depending on your interest.

### 1. BMI Calculator Questionnaire (Beginner-friendly)

#### Objective:

Build a BMI calculator Questionnaire that demonstrates how to pre-populate patient height and weight data, automatically calculates a BMI value and (bonus) writes it back into the patient record.

#### Explored SDC concepts:

- Pre-population
- Calculations
- (Bonus) Extraction

See the [detailed testing scenario guide](testing-scenarios/bmi-scenario.md) if you're interested in working on this.

### 2. QH Adult Sepsis Risk Screening Questionnaire

#### Objective:

Build a Sepsis Risk Screening Questionnaire based on the [web version by Queensland Health](https://www.health.qld.gov.au/__data/assets/pdf_file/0019/1381330/adult-sepsis-screening-tool.pdf) that generates a screening outcome. This scenario demonstrates comprehensive usage of various SDC concepts.

#### Explored SDC concepts:

- Terminology binding
- Pre-population
- Conditional rendering
- Advanced visual rendering

See the [detailed testing scenario guide](testing-scenarios/sepsis-screening-scenario.md) if you're interested in working on this.

### 3. Exploring Queensland Health Use Cases for FHIR Questionnaires

#### Objective:

Explore and build out potential Queensland Health use cases where FHIR Questionnaires could add value — identifying scenarios where structured, interoperable data capture would help improve workflows, patient care, or integration with existing systems.

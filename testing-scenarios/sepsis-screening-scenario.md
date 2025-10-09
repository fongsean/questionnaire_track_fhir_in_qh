# Adult Sepsis Risk Screening Questionnaire

## Objective:

Build a Sepsis Risk Screening Questionnaire based on the [web version by Queensland Health](https://www.health.qld.gov.au/__data/assets/pdf_file/0019/1381330/adult-sepsis-screening-tool.pdf) that generates a screening outcome. This scenario demonstrates comprehensive usage of various SDC concepts.

## Explored SDC concepts:

- Terminology binding
- Pre-population
- Conditional rendering (enableWhen / enableWhenExpression)
- Advanced visual rendering (rendering-xhtml)

## Step by step guide:

1. Build the Questionnaire structure:

- (Optional) Patient information group - includes relevant pre-populated Observations from patient record for assist clinician workflow
- Presumed Infections group
- "Is ONE Red Flag present" group
- "Is an AMBER Flag present" group

2. Add terminology binding

- Use [Questionnaire.item.answerValueSet](https://hl7.org/fhir/R4/questionnaire-definitions.html#Questionnaire.item.answerValueSet) to bind "Aboriginal or Torres Strait Islander peoples" item to a https://healthterminologies.gov.au/fhir/ValueSet/australian-indigenous-status-1 FHIR ValueSet.

3. Add conditional logic

- Add [enableWhen](https://hl7.org/fhir/R4/questionnaire-definitions.html#Questionnaire.item.enableWhen) or [enableWhenExpression](http://hl7.org/fhir/uv/sdc/expressions.html#enableWhenExpression) on relevant items to control visibility based on responses to previous questions.
- If using enableWhenExpression, you need to define [FHIRPath variables](http://hl7.org/fhir/uv/sdc/expressions.html#variable) to capture values from the relevant items.

4. Create sepsis screening outcome guidance texts based on previous responses

- There are multiple ways to achieve this.
- You can use [cqf-expressions](http://hl7.org/fhir/uv/sdc/behavior.html#cqf-expression) to dynamically generate guidance texts.
- Alternatively, you can use enableWhen/enableWhenExpression to conditionally show/hide pre-defined guidance texts.

5. Configure launch context and x-fhir-query variables

- Add [launchContext](http://hl7.org/fhir/uv/sdc/expressions.html#launchContext) and [x-fhir-query variables](http://hl7.org/fhir/uv/sdc/expressions.html#x-fhir-query-enhancements) at the root-level
- Use them to fetch relevant patient Observations to be used for pre-population.
- If you're interested, you can view the queries that run behind the scenes during pre-population. Use the patient Carol Allen (smart-1577780) as the test patient.

  [<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](<https://app.getpostman.com/run-collection/22885901-bc216af3-bcf4-47a0-9c83-36474a7e46ab?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D22885901-bc216af3-bcf4-47a0-9c83-36474a7e46ab%26entityType%3Dcollection%26workspaceId%3D223dc781-848c-46d3-bd95-7735671fd8d1#?env%5BPatient%3A%20Carol%20Allen%20(smart-1577780)%5D=W3sia2V5IjoicGF0aWVudElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6InNtYXJ0LTE1Nzc3ODAiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6InNtYXJ0LTE1Nzc3ODAiLCJzZXNzaW9uSW5kZXgiOjB9XQ==>)

6. Pre-populate values

- Add [initialExpressions](http://hl7.org/fhir/uv/sdc/expressions.html#initialExpression) on relevant items.
- Ensure that fetched values from the patient context are pre-filled into the form.

## Success Criteria:

- Screening logic flows as per the original paper-based tool.

Upload your Questionnaire to https://smartforms.csiro.au/api/fhir/Questionnaire via Postman and
try it out with [SMART App Launch in MELD sandbox with patient Carol Allen (smart-1577780)](https://fhir-in-qh.smartforms.io/launch?iss=https%3A%2F%2Fgw.interop.community%2FQHConnectathon2025%2Fdata&launch=EtdWnN) !

## If you get stuck:

You can refer to the following completed/partially completed example Questionnaires below:

- [Questionnaire skeleton with general structure](https://smartforms.csiro.au/api/fhir/Questionnaire/AdultSepsisScreeningIncomplete/_history/2)
- [Complete Questionnaire](https://smartforms.csiro.au/api/fhir/Questionnaire/AdultSepsisScreening/_history/4)

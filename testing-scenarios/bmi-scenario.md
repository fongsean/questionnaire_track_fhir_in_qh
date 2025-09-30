# BMI Calculator Questionnaire (Beginner-friendly)

## Objective:

Build a BMI calculator Questionnaire that demonstrates how to pre-populate patient height and weight data, automatically calculates a BMI value and (bonus) writes it back into the patient record.

## Explored SDC concepts:

- Pre-population
- Calculations
- (Bonus) Extraction

## Step by step guide:

1. Build the Questionnaire structure:

- Height (decimal)
- Weight (decimal)
- BMI value (decimal, readOnly, calculated)

2. Configure launch context and x-fhir-query variables

- Add [launchContext](http://hl7.org/fhir/uv/sdc/expressions.html#launchContext) and [x-fhir-query variables](http://hl7.org/fhir/uv/sdc/expressions.html#x-fhir-query-enhancements) at the root-level
- Use them to fetch patient height and weight Observations to be used for pre-population.
- If you're interested, you can view the queries that run behind the scenes during pre-population:

  [<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](<https://app.getpostman.com/run-collection/22885901-ce38c7db-1dd1-4c28-a369-2776f7b4bd56?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D22885901-ce38c7db-1dd1-4c28-a369-2776f7b4bd56%26entityType%3Dcollection%26workspaceId%3D223dc781-848c-46d3-bd95-7735671fd8d1#?env%5BPatient%3A%20Carol%20Allen%20(smart-1577780)%5D=W3sia2V5IjoicGF0aWVudElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6InNtYXJ0LTE1Nzc3ODAiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6InNtYXJ0LTE1Nzc3ODAiLCJzZXNzaW9uSW5kZXgiOjB9XQ==>)

3. Pre-populate values

- Add [initialExpressions](http://hl7.org/fhir/uv/sdc/expressions.html#initialExpression) on the height and weight items.
- Ensure that fetched values from the patient context are pre-filled into the form.

4. Calculate BMI

- Define [FHIRPath variables](http://hl7.org/fhir/uv/sdc/expressions.html#variable) for height and weight.
- Use a calculatedExpression on the BMI item with the following formula:
  ```
  (%weight/((%height/100).power(2))).round(1)
  ```

5. (Bonus) Extract and write back BMI

- Add a [extraction template](https://build.fhir.org/ig/HL7/sdc/extraction.html#template-based-extraction) to extract the calculated BMI result into a FHIR Observation resource for write-back

## Success Criteria:

- **Pre-population**: Height and weight values are automatically populated for patient Carol Allen (https://gw.interop.community/QHConnectathon2025/open/Patient/smart-1577780).
- **Calculation**: BMI is automatically computed.
- **(Bonus) Extraction**: A valid FHIR Bundle containing one BMI Observation is extracted.

Upload your Questionnaire to https://smartforms.csiro.au/api/fhir/Questionnaire via Postman and
try it out with [SMART App Launch in MELD sandbox with patient Carol Allen (smart-1577780)](https://fhir-in-qh.smartforms.io/launch?iss=https%3A%2F%2Fgw.interop.community%2FQHConnectathon2025%2Fdata&launch=EtdWnN) !

## If you get stuck:

You can refer to the following completed/partially completed example Questionnaires below:

- [Questionnaire skeleton with general structure](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorPrepop-Incomplete/_history/1)
- [Complete Questionnaire without extraction template](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorPrepop/_history/4)
- (Bonus) [Complete Questionnaire with extraction template](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorTemplateExtract/_history/5)

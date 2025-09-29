# Beginner - BMI Calculator Questionnaire

## Objective:

Build a BMI calculator Questionnaire that demonstrates how to pre-populate patient height and weight data, automatically calculates a BMI value and (bonus) writes it back into the patient record.

## Explored SDC concepts:

- Pre-population
- Calculation
- (Bonus) Extraction

## Step by step guide:

1. Build the Questionnaire structure:

- Height (decimal)
- Weight (decimal)
- BMI value (decimal, readOnly, calculated)

2. Configure launch context and x-fhir-query variables

- Add [launchContext](http://hl7.org/fhir/uv/sdc/expressions.html#launchContext) and [x-fhir-query variables](http://hl7.org/fhir/uv/sdc/expressions.html#x-fhir-query-enhancements) at the root-level
- Use them to fetch patient height and weight from existing FHIR Observations.

3. Pre-populate values

- Add [initialExpressions](http://hl7.org/fhir/uv/sdc/expressions.html#initialExpression) on the height and weight items.
- Ensure that the fetched values from the patient context are pre-filled into the form.

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

## If you get stuck:

You can refer to the following completed/partially completed example Questionnaires below:

- [Questionnaire skeleton with general structure](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorPrepop-Incomplete/_history/1)
- [Complete Questionnaire without extraction template](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorPrepop/_history/4)
- (Bonus) [Complete Questionnaire with extraction template](https://smartforms.csiro.au/api/fhir/Questionnaire/CalculatedExpressionBMICalculatorTemplateExtract/_history/5)

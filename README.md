# Topic 3: Data Validation, Cleaning & Duplicate Prevention

## 1. Project Overview

In this project, I built an n8n workflow to clean and validate marketing leads before sending them to a mock CRM.

The workflow takes sample lead data, cleans email addresses, formats phone numbers, and checks whether the details are valid. It also identifies duplicate leads so the same lead is not sent more than once in the same batch.

Invalid leads and duplicate leads are moved to separate quarantine branches for review.

## 2. Project Objectives

The main goals of this project are to:

- Create sample marketing lead data.
- Remove extra spaces and convert email addresses to lowercase.
- Clean and format phone numbers.
- Check email and phone number formats.
- Reject leads with disposable email addresses.
- Find duplicate leads within the same batch.
- Send valid and unique leads to a mock CRM.
- Separate invalid and duplicate leads for review.
- Calculate the final workflow metrics.

## 3. Tools Used

- **n8n:** To build and run the workflow.
- **Code nodes:** To clean data, validate leads, and identify duplicates.
- **IF nodes:** To route valid and invalid leads.
- **HTTP Request node:** To send leads to the mock CRM.
- **DummyJSON Custom Response:** To simulate a CRM API response.
- **Git and GitHub:** To save and share the project files.

## 4. Workflow Steps

The workflow follows these steps:

1. **Manual Trigger:** Starts the workflow when I click Test workflow.
2. **Generate Dirty Leads:** Creates five sample leads with different types of data.
3. **Sanitize and Format:** Cleans email addresses and phone numbers.
4. **Validate Lead Quality:** Checks the lead details and rejects invalid emails, phone numbers, and disposable email domains.
5. **IF – Is Quality Lead?:** Sends invalid leads to the invalid quarantine branch and passes valid leads to the next step.
6. **Deduplicate Leads:** Checks for duplicate leads after cleaning and normalizing the data.
7. **IF – Is Unique Lead?:** Sends duplicate leads to the duplicate quarantine branch and passes unique leads to the CRM.
8. **POST to Mock CRM:** Sends the valid, unique leads using an HTTP Request.
9. **Aggregate Pipeline Metrics:** Calculates the final results of the workflow.

## 5. Sample Test Data

I used five sample leads to test different scenarios.

- **LD-001:** A valid lead that should be sent to the CRM.
- **LD-002:** A lead with an invalid email address and phone number.
- **LD-003:** A lead with a disposable email address.
- **LD-004:** A duplicate of LD-001 after cleaning and normalization.
- **LD-005:** A unique lead with an international phone number.

This test data helps me check whether the workflow correctly handles valid, invalid, duplicate, and international leads.

## 6. Expected Results

After running the workflow, the expected results are:

- Total leads received: 5
- Invalid leads: 2
- Duplicate leads: 1
- Unique leads sent to the mock CRM: 2
- `uniqueLeadsPushed`: 2

These results help confirm that the workflow is cleaning the data, rejecting invalid leads, and preventing duplicates within the batch.

## 7. How to Run the Workflow

1. Open the workflow in n8n.
2. Check the mock CRM URL in the HTTP Request node.
3. Click **Test workflow** to run the workflow.
4. Open each node and check its output.
5. Verify that invalid leads go to the invalid quarantine branch.
6. Check that duplicate leads go to the duplicate quarantine branch.
7. Confirm that the two valid, unique leads reach the HTTP Request node.
8. Check the final pipeline metrics to confirm the results.

GIT Url:

https://github.com/SagarBommela/n8n-Hands-On-Level-2

Loom Video:

https://www.loom.com/share/68cfbcc489a34d0b8f13d5badee2ef9c


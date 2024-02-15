developer using voice talks to copilot, describes a sample application she wants to build. copilot generates code, developers reviews it, provides feedback to copilot tool, copilot makes necessary changes, generates unit test, test data and documentation. developer reviews and accepts the change makes minor enhancements on her own and commits the code in SCM , raises a pull request, code is reviewed and merge, this triggers a CI/CD pipeline, during the run, the pipeline detects that there is a critical vulnerability that was just issued for a core library requiring an upgrade. the developer receives a notification about this and an open rewrite recipe is proposed, developer accepts the changes, Impacted code is updated and commited,  pipeline is rerun, now the unit test fails due to some enhancements the developers made earlier on so copilot is automatically run to fix the failed unti test and pipeline is retriggered. unit test is successful and the pipeline automatically runs automated end-end test and performance test. all tests are succesdl and we show a screen that all evidence (of peer review, code coverage, functiona, performance test) are available and acceptable, so automatically pushed to production via blue green deployment on ECS Fargate instance in 2 regions

Creative coding tasks are often exploratory in nature. When producing digital artwork, artists usually begin with a high-level semantic construct such as a "stained glass filter" and programmatically implement it by varying code parameters such as shape, color, lines, and opacity to produce visually appealing results. Based on interviews with artists, it can be effortful to translate semantic constructs to program syntax, and current programming tools don't lend well to rapid creative exploration.

To address these challenges, we introduce Spellburst, a large language model (LLM) powered creative-coding environment.

Spellburst provides (1) a node-based interface that allows artists to create generative art and explore variations through branching and merging operations, (2) expressive prompt-based interactions to engage in semantic programming, and (3) dynamic prompt-driven interfaces and direct code editing to seamlessly switch between semantic and syntactic exploration. Our evaluation with artists demonstrates Spellburst's potential to enhance creative coding practices and inform the design of computational creativity tools that bridge semantic and syntactic spaces.

To effectively demonstrate the envisioned use case involving a developer interacting with an AI assistant like GitHub Copilot to build, test, and deploy an application, it’s useful to break down the scenario into distinct categories that highlight each stage of the software development lifecycle (SDLC). This breakdown will not only make the demo more structured but also clarify how generative AI can enhance each phase.

### 1. **Idea Conception & Code Generation**

- **Voice Interaction**: The developer verbally describes the desired application's functionality to the Copilot tool.
- **Initial Code Generation**: Copilot interprets the description and generates a preliminary set of code for the application.

### 2. **Review & Iteration**

- **Code Review**: The developer reviews the generated code, assessing its quality, completeness, and alignment with the initial description.
- **Feedback Provision**: The developer provides verbal or typed feedback on the generated code to Copilot.
- **Code Refinement**: Based on the feedback, Copilot makes necessary adjustments to the code.

### 3. **Testing & Documentation**

- **Unit Test Generation**: Copilot generates unit tests for the refined code to ensure functionality works as intended.
- **Test Data Creation**: Copilot creates test data that can be used to test the application.
- **Documentation**: Copilot generates initial documentation outlining the application's purpose, architecture, and usage.

### 4. **Source Control Management (SCM) & Peer Review**

- **Code Commitment**: The developer makes minor enhancements, commits the code to SCM (e.g., GitHub), and raises a pull request.
- **Code Review & Merge**: The pull request is reviewed by peers, and upon approval, the code is merged into the main branch.

### 5. **Continuous Integration/Continuous Deployment (CI/CD)**

- **Pipeline Trigger**: Merging the code triggers the CI/CD pipeline, which automatically builds, tests, and prepares the application for deployment.
- **Vulnerability Detection & Fixing**: The pipeline detects a critical vulnerability in a core library. Copilot suggests a fix with an open rewrite recipe, which the developer approves. Impacted code is updated and committed.
- **Re-Run Pipeline & Testing Failures**: The pipeline is retriggered, revealing unit test failures due to the developer's enhancements. Copilot automatically adjusts the failing tests.
- **Final Testing**: The pipeline successfully completes automated end-to-end and performance tests.

### 6. **Deployment & Validation**

- **Blue-Green Deployment**: The application is deployed to production via blue-green deployment on ECS Fargate across two regions, minimizing downtime and risk.
- **Evidence Collection & Final Review**: Screens are shown to the developer and stakeholders with all necessary evidence of peer review, code coverage, functional testing, and performance testing, confirming that all criteria for a successful deployment are met.

### 7. **Production Monitoring & Feedback**

- **Monitoring**: Post-deployment, the application's performance and user interactions are monitored to gather feedback and identify areas for further improvement.

### Demonstrating the Use Case

This narrative emphasizes the revolutionary potential of AI in accelerating and enhancing software development processes.

### Application Concept: Corporate Financial Health Monitor

- **Functionality Description for Copilot**: The developer communicates to the Copilot tool, "Build a Corporate Financial Health Monitor Streamlit app that enables enterprises to input and analyze their financial data comprehensively. The application should include modules for cash flow analysis, budget versus actual spending review, financial health scoring based on key performance indicators (KPIs), and predictive modeling for financial forecasting. It should also provide interactive visualizations for financial metrics, trend analysis, and offer scenario planning tools to evaluate potential financial decisions. The design should be professional, intuitive, and adaptable for both desktop and mobile viewing."

### Code Generation Prompt:

"Generate a Streamlit script that incorporates:

- User interfaces for entering and managing financial data across various categories like revenues, expenses, assets, and liabilities.
- Functionalities for creating and comparing budgets, with visual representations of budget allocations versus actual expenditures.
- A financial health scoring system that evaluates the enterprise's financial status based on liquidity ratios, profitability ratios, and debt ratios, displaying a comprehensive health score dashboard.
- Predictive modeling features to forecast future financial states based on historical data, using time-series analysis or machine learning models.
- Scenario planning tools that allow businesses to simulate different financial strategies and their potential impacts on financial health.
- Interactive charts and graphs built with Streamlit's native plotting capabilities or integration with advanced visualization libraries like Plotly or Altair for dynamic financial data presentation."

### Verbal Feedback 

"Hey Copilot, the function you generated to calculate monthly expenses seems to include all transactions, which skews the results since it doesn't distinguish between income and expenses. Can you update the function to first filter out only expense transactions? Also, it would be beneficial to categorize the expenses into predefined categories like 'Utilities', 'Groceries', and 'Rent'. This way, we can have a more detailed view of where the monthly spending goes. Lastly, ensure that the function can handle transactions with missing categories gracefully, perhaps logging a warning or assigning them to a 'Miscellaneous' category."

### Typed Feedback

If providing feedback through typing, such as in a comment within the code or a feedback tool provided by the development environment, you might structure it as follows:

pythonCopy code

`# REVIEW FEEDBACK: Function for Calculating Monthly Expenses # The current implementation of calculate_monthly_expenses() includes both income and expenses in the total, which leads to inaccurate expense tracking. To improve the accuracy of this function, I suggest the following enhancements: # 1. Modify the function to filter transactions, including only those classified as 'expenses' before calculating the total. # 2. Incorporate a categorization feature that assigns each expense transaction to categories like 'Utilities', 'Groceries', and 'Rent'. This addition will help in generating more detailed expense reports. # 3. Implement error handling for transactions with undefined categories. These should either log a warning or be categorized under 'Miscellaneous' to ensure they are accounted for without causing errors. # With these changes, we can achieve a more accurate and detailed breakdown of monthly expenses, enhancing our financial tracking capabilities.`

## Tests
### Voice Prompts for Copilot

#### Unit Test Generation

"Hey Copilot, I need you to generate comprehensive unit tests for the Enterprise Finance Tracker. Focus on the critical functionalities such as transaction recording, budget analysis, and financial forecasting. Ensure the tests cover various input scenarios, including edge cases like invalid financial entries and extreme budget limits."

#### Test Data Creation

"Can you also create a set of test data that reflects realistic enterprise financial transactions? This should include a mix of income, expenses, budget allocations, and investment data. Include edge cases for robust testing, such as transactions exceeding budget limits or overlapping investment periods."

#### Documentation

"Lastly, I need you to draft the initial documentation for the Enterprise Finance Tracker. It should include an overview of the application's purpose, detailed architecture, and a guide for users on how to record transactions, analyze budgets, and use the financial forecasting feature. Make sure it's detailed enough for new users to get started without prior knowledge."

### Typed Prompts for Copilot

#### Unit Test Generation

plaintextCopy code

`// Copilot Task: Generate Unit Tests for Enterprise Finance Tracker // Required unit tests for: // 1. Transaction Recording: Tests should validate correct processing of income and expenses, including validation of transaction categories and amounts. // 2. Budget Analysis: Generate tests to ensure budgets are accurately tracked against expenses, including scenarios where expenses exceed budgets. // 3. Financial Forecasting: Create tests to validate forecasting accuracy, considering historical financial data. // Cover a range of scenarios, including edge cases for comprehensive testing.`

#### Test Data Creation

plaintextCopy code

`// Copilot Task: Create Test Data for Enterprise Finance Tracker // Please generate test data that includes: // - Diverse income and expense transactions with various categories and amounts. // - Budget data for different departments or projects, including cases of budget overruns. // - Historical financial data for use in forecasting tests, with varied financial health indicators. // Ensure the inclusion of edge cases to test the application's robustness.`

#### Documentation

plaintextCopy code

`// Copilot Task: Generate Documentation for Enterprise Finance Tracker // Documentation needs: // 1. Application Overview: Explain the purpose and key benefits of the finance tracker. // 2. Architecture Description: Detail the main components and their interactions within the application. // 3. User Guide: Step-by-step instructions on how to use key features - transaction recording, budget analysis, and financial forecasting. // Aim for clarity, targeting users who might be new to financial tracking systems.`

For the scenario involving a critical vulnerability in a core library within a CI/CD pipeline, let's specify the vulnerability as a severe deserialization flaw in a popular JSON parsing library, which could potentially allow unauthorized remote code execution.

### Voice Prompts for Copilot

#### Pipeline Trigger

"Trigger the CI/CD pipeline for the latest merge to automatically build, test, and prep the application for deployment."

#### Vulnerability Detection & Fixing

"The CI/CD pipeline has detected a critical deserialization vulnerability in the JSON parsing library we're using. Can you suggest a secure fix or provide an open rewrite recipe to patch this vulnerability? I need a solution that maintains our current functionality but eliminates the security risk."

#### Re-Run Pipeline & Testing Failures

"We've applied a fix for the JSON library vulnerability, but now some unit tests are failing. They're likely affected by the changes made to address the security issue. Can you automatically update the failing tests to accommodate the new library version or the security patch we've applied?"

#### Final Testing

"Now that we've fixed the unit tests, let's rerun the CI/CD pipeline to conduct final testing. This should include comprehensive automated end-to-end and performance tests to ensure everything operates smoothly post-fix."

### Typed Prompts for Copilot

#### Pipeline Trigger

plaintextCopy code

`// Copilot Task: Initiate CI/CD Pipeline // Command: Execute the CI/CD pipeline following our recent code merge. This includes automatic builds, tests, and deployment preparations.`

#### Vulnerability Detection & Fixing

plaintextCopy code

`// Copilot Task: Mitigate Critical Deserialization Vulnerability // A critical deserialization vulnerability has been identified in our JSON parsing library, posing a risk of unauthorized remote code execution. Generate a secure patch or suggest an open rewrite recipe to fix this issue, ensuring the solution is compatible with our application's functionality and does not introduce new risks.`

#### Re-Run Pipeline & Testing Failures

plaintextCopy code

`// Copilot Task: Adjust Failing Unit Tests Post-Security Patch // Following the security patch to our JSON parsing library, certain unit tests related to JSON processing are failing. Automatically revise these tests to align with the updated library functionalities and the security improvements. Confirm when the tests are adapted so we can proceed to retrigger the CI/CD pipeline.`

#### Final Testing

plaintextCopy code

`// Copilot Task: Complete Final Testing Phase // With the JSON library vulnerability addressed and all unit tests passing, initiate the final phase of testing through the CI/CD pipeline. This includes detailed automated end-to-end testing and performance assessments. Monitor the process for any issues that arise from the recent fixes and report back on the test outcomes.`

## Deployment and Validation
### Voice Prompts for Copilot

#### Blue-Green Deployment

"Initiate a blue-green deployment for our application on ECS Fargate, spanning across two regions. Ensure this process minimizes downtime and mitigates deployment risks. Let's prioritize smooth traffic transition and rollback capabilities in case any issues arise."

#### Evidence Collection & Final Review

"Compile all deployment-related evidence, including peer review documentation, code coverage reports, results from functional and performance testing. I need comprehensive dashboards or reports that clearly present this information for review by both the development team and stakeholders, ensuring we meet all deployment success criteria."

### Typed Prompts for Copilot

#### Blue-Green Deployment

plaintextCopy code

`// Copilot Task: Execute Blue-Green Deployment // Command: Conduct a blue-green deployment for the application using ECS Fargate, covering two regions. The deployment should aim to minimize downtime and ensure a risk-averse transition between the old and new versions. Include mechanisms for monitoring traffic and performing quick rollbacks if needed.`

#### Evidence Collection & Final Review

plaintextCopy code

`// Copilot Task: Aggregate Deployment Evidence // Gather comprehensive evidence of the deployment process, including: // - Peer review documents and approval logs. // - Code coverage metrics and reports. // - Functional and performance testing results, with detailed analyses. // Organize this information into accessible dashboards or reports suitable for stakeholder review, verifying that the deployment meets all predefined success criteria.`

## Monitoring
### Voice Prompts for Copilot

#### Monitoring Setup

"Set up a comprehensive monitoring system for the application now that it's deployed. We need to track both performance metrics and user interactions in real time. Focus on identifying any performance bottlenecks and areas where user experience can be enhanced."

#### Feedback Collection

"Implement a mechanism to collect user feedback directly within the application. This feedback, along with the insights from our monitoring tools, should help us pinpoint what's working well and what needs improvement."

### Typed Prompts for Copilot

#### Monitoring Setup

plaintextCopy code

`// Copilot Task: Configure Application Monitoring // Instructions: Establish a robust monitoring framework for the newly deployed application. This should include: // - Performance tracking: Monitor server response times, error rates, and usage patterns. // - User interaction analysis: Track key user actions, navigation flows, and feature utilization. // The goal is to swiftly identify any technical issues or user experience shortcomings for immediate rectification.`

#### Feedback Collection

plaintextCopy code

`// Copilot Task: User Feedback Collection Integration // Create a feature within the application that prompts users for their feedback on usability, performance, and general satisfaction. Ensure this data is systematically collected and analyzed alongside monitoring insights to drive continuous improvement efforts.`


Seemless Innovation: During a transaction, the user discovers that adding a new feature could be advantageous. They describe the expected functionality of this feature in conversational language. Reacting to this, the product automatically launches a code editor, creates a development environment, and produces the necessary code for the new feature. This process enables the user to trial the feature in real-time, without requiring any extra actions on their part, before they propose integrating it into the main product.
# Trustworthy AI: Algorithm Assessment Design Document for CARiSMA (UoK)

## Summary

The LORIA and Affectlog solutions are complemented by [CARiSMA (CompliAnce, Risk, and Security ModelAnalyzer)](https://github.com/CARiSMA-Tool/carisma-tool), developed by the University of Koblenz and Fraunhofer ISST. CARiSMA is a comprehensive open source software suite that enables system designers and security experts to perform automated compliance analyses, risk analyses and security analyses of software and system models. This allows users to consider security requirements early in the development process. Unified Modelling Language (UML) models are annotated with security-specific requirements that can be tailored to the users’ needs to cover a wide range of topics. Checks are performed on UML models, analyzing the models against the specified requirements and providing the user with detailed feedback on the models' compliance with the previously defined requirements.

In the context of Trustworthy AI assessment, it is planned to extend the approach to generate informative documentation that helps users to understand, how their personal data is processed within an AI Scenario. This is achieved by defining a UML extension that an AI expert uses whithin the *CARiSMA Modeler* to create an *AI Scenario Model*, which is a UML model containing additional AI specific information as shown in Figure 1. The AI scenario models can be analyzed and assessed by the *CARiSMA Analyzer* regarding [AI/ML specific security issues](https://owasp.org/www-project-machine-learning-security-top-10/) as identified by the Open Worldwide Application Security Project (OWASP) community. These analyses  yield an *AI Analysis Report*, which, on the  one hand, helps the AI Expert to improve the scenario. On the other hand, the AI Analysis Report can then be shared with the visualization building block to present the report to the natural persons, whose personal data is processed within the AI scenario. This improves the understandability of the AI scenario and contributes to fulfill documentation obligations as defined in [EU’s AI Act](https://www.europarl.europa.eu/topics/en/article/20230601STO93804/eu-ai-act-first-regulation-on-artificial-intelligence).

![Figure 1: AI Scenario Analysis](images/AI%20Scenario%20Analysis.drawio.svg)

## Technical usage scenarios & Features

**Key functionalities:**

- Ability to model Trustworthy AI systems
- Get feedback about trust factors of AI system
- Automatically generating reports of system for documentation purposes
- Visualize Trustworthiness of AI systems

**Value-added:**

- Increasing user's trust in AI system
- System engineer gets a better understanding of risk in system modeling 
- System engineer gets automated feedback about his system

### Features/main functionalities

- **Modelling Trustworthy AI systems:** CARiSMA utilizes the profile mechanism of the Unified Modeling Language (UML) which allows to tailor the UML to different, more specific scenarios. 
  - AI Expert models his system with the Papyrus Modeling Tool
  - AI Expert applies the profile delivered with CARiSMA to his model
  - AI Expert applies stereotypes of the profile to  selected elements of his system model
  - AI Expert fills the tagged values associated with the stereotypes
  - AI Expert applies constraints to model elements
  - Alternatively : The profile mechanism of the CARiSMA tool allows the user to define new stereotypes, tags and constraints for UML elements of his choice
- **Feedback about trust factors of AI system:** CARiSMA utilizes an Analyzer which implements a series of different analyses for different types of structure and behavioral diagrams/models. 
  - AI Expert has finished the creation of his system with the new profile
  - AI Expert creates a new CARiSMA analysis file 
  - AI Expert chooses the .uml file of his system/model as an input for the analysis 
  - AI Expert chooses one (or more) of a list of predefined checks/analysis
  - AI Expert runs the selected checks/analyses
  - A positive/negative feedback is shown on the screen
  - Alternatively : The plugin architecture of CARiSMA allows the user to implement new new checks/analyses making use of (newly created) stereotypes defined in the profile
- **Reports of system for documentation purposes:** CARiSMA enables the automatic generation of reports which contain information on the trustworthiness of a system.
  - AI Expert has finished the creation of his system with the new profile
  - AI Expert ran a number of checks/analysis
  - AI Expert clicks on the displayed (positive/negative) analysis result/feedback 
  - AI Expert chooses to generate a report
  - AI Expert decides on the XML format and clicks on generate report
  - A XML report file is created in the project of the AI Experts modeled system
  - AI Expert opens the XML reports and gets further information of security risks that occurred during the modeling process
  - AI Expert has the opportunity to refine his system depending on the information received in the report 
  - Alternatively : AI Expert creates a HTML report instead of a XML report 
- **Trustworthiness visualization of AI systems:** CARiSMA will have functions for JSON creation of reports as well as communication of these reports between data space connectors. Visualization components are therefore enabled to visualize these reports on a user's personal dashboard.
  - AI Expert has finished the creation of his system with the new profile
  - AI Expert ran a number of checks/analysis
  - AI Expert clicks on the created report
  - AI Expert clicks on send
  - The report gets send to the visualization BB 
  - User can access the visualization before he decides to use the AI system

### Technical usage scenarios

CARiSMA is beneficial for AI system engineers:

- **Trust Enhancement:** Helps to increase the user trust in AI systems by providing a structured method to evaluate and visualize the AI system's trustworthiness.
- **Risk Understanding:** Assists system engineers in better understanding and managing risks associated with AI system modeling.
- **Fast Feedback:** Offers immediate feedback on AI systems and therefore helps to identify issues early in the development process.
- **Documentation:** Automates the documentation process with comprehensive reports ad therefore saves time and ensuring consistent documentation, e.g. as required by the EU AI Act.
- **Customization:** Allows for tailored modeling and analysis to fit specific scenarios and requirements through customizable profiles and analysis checks.

CARiSMA is beneficial for AI system users:

- **Visualization:** Enhances the visualization BB to interpret trustworthiness reports and therefore helps the user in decision making on system usage.

## Requirements

### Use Cases

![Figure 2: Use Cases of the CARiSMA in BB context](images/use-cases.svg)

| Use Case              | Create AI Scenario Model                                                           |
|-----------------------|------------------------------------------------------------------------------------|
| Actor(s)              | AI Expert                                                                          |
| Brief Description     | AI Expert creates a system model in context of Trustworthy AI                      |
| Pre-Conditions        | Eclipse, Papyrus and CARiSMA installed                                             |
| Post-Conditions       | A model of a system with stereotypes, tags and constraints                         |
| Main Success Scenario | AI Expert designed a system, annotates the required stereotypes, tags, constraints |

| Use Case              | Analyze AI Scenario Model                                                                                 |
|-----------------------|-----------------------------------------------------------------------------------------------------------|
| Actor(s)              | AI Expert                                                                                                 |
| Brief Description     | AI Expert analyzes a system model in context of Trustworthy AI                                            |
| Pre-Conditions        | A system model in context of Trustworthy AI has been created                                              |
| Post-Conditions       | A feedback is given to the AI Expert whether his system is correct or not                                 |
| Main Success Scenario | AI Expert creates a CARiSMA analysis file, chooses the analysis type he wants to execute and clicks "Run" |

| Use Case              | Create & View AI Analysis Report                                                                                                                                                       |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Actor(s)              | AI Expert                                                                                                                                                                              |
| Brief Description     | AI Expert creates an analysis report of a model in context of Trustworthy AI                                                                                                           |
| Pre-Conditions        | A system has been modeled and an analysis file is created and executed                                                                                                                 |
| Post-Conditions       | An HTML or XML file which contains information on the success or failure of the analysis including a brief description of possible mistakes                                            |
| Main Success Scenario | AI Expert clicks on the result of the analysis and chooses the format he want to create the report in, a file gets created in the folder of the model, the AI Experts opens the report |

| Use Case              | Improve AI Scenario Model                                                                                                                                                                                                                                                                      |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Actor(s)              | AI Expert                                                                                                                                                                                                                                                                                      |
| Brief Description     | AI Expert uses the error pointed out in the AI Analysis Report to improve them in the modeled system                                                                                                                                                                                           |
| Pre-Conditions        | A system has been modeled and an analysis report file is created which contains errors for the Checks/Analysis executed                                                                                                                                                                        |
| Post-Conditions       | An improved system model which contains no more errors after the same Analysis is executed again                                                                                                                                                                                               |
| Main Success Scenario | AI Expert opens the report which shows him one (or several more) errors, he improves his system regarding the errors and saves the system model, he opens the analysis file again and runs the analysis again, he creates another report which shows him a success for all the checks executed |

| Use Case              | Share AI Analysis Report                                                                                                                                                    |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Actor(s)              | AI Expert                                                                                                                                                                   |
| Brief Description     | AI Expert clicks on the analysis of the system and chooses send, he specifies the address and clicks send                                                                   |
| Pre-Conditions        | A system has been modeled and an analysis file is created and executed                                                                                                      |
| Post-Conditions       | A JSON file is created and send to a Connector specialized by the Visualization BB                                                                                          |
| Main Success Scenario | AI Expert clicks on the result of the analysis and chooses "send", (specifies the location of the Visualization BB) and the analysis JSON gets send to the Visualization BB |

### Requirements

- R1. CARiSMA MUST allow an AI expert to create an AI scenario model
- R2. CARiSMA MUST allow an AI expert to analyse the AI scenario model
- R3. CARiSMA MUST allow an AI expert to create an AI Analysis report
- R4. CARiSMA MUST allow an AI expert to view the AI Analysis Report
- R5. CARiSMA MUST allow an AI expert to improve the AI Analysis Report
- R6. CARiSMA SHOULD allow an AI expert to share an AI Analysis Report with the building block "Distributed Data Visualization"
- R7. The building block "Distributed Data Visualization SHOULD allow a user (the data subject) to view the AI Analysis Report

## Integrations

### Direct Integrations with Other BBs

Analysis results can be stored in a JSON/HTML file format and sent to the building block "Decentralized Data Visualization" that visualizes the check result (maybe in a checkbox green/red). Also further details could be sent with the report (e.g. information when hovering over this checkbox). Data format could be a json-ld document using some standardized vocabulary/ontology.

### Integrations via Connector

It's planned to use a PDC to share AI Analysis Reports with the building block "distributed data visualiation".

## Relevant Standards

### Data Format Standards

CARiSMA in the context of this building block makes use of the following standards, data formats and markup languages:

- UML (XMI serialization)
- HTML (for reports)
- XML (for reports)
- JSON-LD / RDF (for reports)

### Mapping to Data Space Reference Architecture Models

CARiSMA in the context of this building block does not implement an element of a data space reference architecture model. It does make use of a connector implementation (the PDC) as defined by the Reference Architecture Model of the International Data Spaces Association (IDS-RAM).

## Input / Output Data

### Input

No data from other building blocks will be received. Papyrus allows the creation of Unified Modeling Language (UML) models in the .di format via a graphical user interface. When such a model is created, a corresponding .uml file is created at the same time, which represents and saves this model in a tree structure used as an input for the CARiSMA tool. An extension will allow the user to model his system in the context of “Trustworthy AI”, for example by creating an AI scenario model on the use of data with personal information, by annotating various model elements with new stereotypes, tagged values and constraints.

![Figure 3: Example Model for Data Usage Control](images/datausagecontrol.svg)

For each of these .uml files, a CARiSMA analysis file can be created which allows to select various checks/analyses via an UI tailored to the problem the user wants to analyze his system design. In the context of our previous example for a “Trustworthy AI” scenario, the user will be able to select an analysis that checks whether personal data has been made unrecognizable or not.

![Figure 4: Analysis Editor User Interface](images/AnalysisUI.png)

### Output

Once an analysis is complete, the AI Expert is informed of its outcome, indicating whether it is positive or negative. Additionally, the AI Expert has the option to generate a report in different machine-readable formats, providing further details on potential issues and sources of risks in system modeling. This enables the AI Expert to make necessary adjustments and refinements to the system, thereby closing security and risk gaps and establishing trust within the system.

![Figure 5: Report in XML Format](images/ReportXML.png)

Once the model of the system design is finalized, the AI Expert can trigger the sharing of the AI Analysis Report with other components. It's planned to share the AI Analysis Report with the building block "Decentralized Data Visualization". The user (data subject) is then able to view the report to get insights of how their data is processed within an AI scenario. The format of the shared AI Analysis Report looks as follows (subject to change):

```plantuml
@startjson
{
    "name" : "AI Scenario Analysis",
    "success" : false,
    "analyses" : [{
		"name": "PersonalDataAnalysis",
		"success": true,
		"info": "Data contains no  personal information"
    }, {
		"name": "AiAlgorithmsAnalysis",
		"success": false,
		"info": "Algorithm X possible Data Poisoning Attack"
    }, {
		"name": "...",
		"success": "...",
		"info": "..."
    }],
	"report": {
		"html": "<html><head>...</head><body>...</body></html>",
		"xml": "<xml>...</xml>",
		"rdf" : "{\"@context\": {...}}"
	}
}
@endjson
```

![Figure 6: Example Structure of an AI Analysis Report](images/datasample.svg)

## Architecture

The main class Carisma is registered as an Eclipse plugin and provides access to the various structures, serving as the controller for the different components of the tool.

An Analysis is executed on a Model of a certain `ModelType` registered within the `ModelTypeRegistry`. The models themselves are provided by the `ModelManager` and the `ModelLoader` for the corresponding `ModelType`.

CARiSMA executes analyses consisting of various `CheckReferences` to `CheckDescriptors`. These descriptors define the `CarismaCheck`s that have been registered with the `CheckRegistry`. Each `CarismaCheck` may have any number of `CheckParameters` defined, which has a certain `ParameterType`. Checks may define pre- and post-conditions to use in combination with a blackboard to exchange information between them.

The `AnalysisHost` interface provides access to this blackboard, as well as methods for displaying the results of an Analysis in the `AnalysisResultsView`. The Analyzer is the main CARiSMA implementation of the `AnalysisHost` interface.

![Figure 7: CARiSMA Tool Architecture](images/architecture-tool.png)

![Figure 8: CARiSMA Check/Analysis Mechanism](images/check-mechanism.png)

## Dynamic Behaviour

The sequence diagram shows how the component communicates with other components.

![Figure 9: AI expert & User Interactions](images/sequence.svg)

## Configuration and deployment settings

- CARiSMA is configured in the graphical user interface
- Configuration of the Prometheus-X Data Space Connector (PDC), used to share AI Analysis Reports with the visualization building block, is documented by the PDC building block

## Third Party Components & Licenses

CARiSMA is licensed under the [Eclipse Public License v1.0](https://www.eclipse.org/legal/epl-v10.html). CARiSMA is based on the [Eclipse IDE](https://www.eclipse.org/) and on [Papyrus](https://eclipse.dev/papyrus/). To run CARiSMA Eclipse IDE and Papyrus need to be installed. Both products are licensed under [Eclipse Public License v2.0](https://www.eclipse.org/legal/epl-2.0/).

Additional third party libraries are required by / shipped with CARiSMA:

- Apache Commons Lang3: [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
- [xstream](https://x-stream.github.io/): [BSD 3-clause](https://x-stream.github.io/license.html)

## OpenAPI Specification

The component does not provide an API, since it does not receive data from other components / building blocks. All data is created manually within CARiSMA.

## Test specification

### Test plan

The testing strategy will include JUnit based tests of the implementation of CARiSMA (automated CI/CD pipeline via GitHub) and integration tests, covering the communication of different connectors via e.g. Postman and/or additional automated tests, therefore employing a combination of automated and manual testing methods to ensure comprehensive coverage.

### Unit tests

Unit tests for three newly developed components will be implemented:

##### Component Profile

An extension of the Unified Modeling Language (UML) which allows for Trustworthy AI specific annotations to a model.

JUnit test should check that all necessary elements can be annotated with the required stereotypes so that the system can be modeled correctly.

##### Component Check/Analysis

A component which analyses a given model and gives a feedback whether the model is correct

JUnit test should check that correct and incorrect are identified as such by corresponding analysis

##### Component HTML/XML/JSON-LD Report

A component which enables the creation for HTML/XML/JSON-LD reports for a given analysis of a model/system

JUnit test should check that an HTML, XML, JSON-LD report can be created which contains the correct content depending on the input scenario and analysis

### Integration tests

**Connectors:** Verification of all API endpoints (for CARiSMA and Visualization BB) and if they respond correctly to valid and invalid requests. Also check for correct error handling.

### UI test (where relevant)

CARiSMA's graphical user interface is based on the Eclipse IDE and Papyrus, a Eclipse based graphical UML modeling tool. Eclipse's and Papyrus's user interfaces are tested during Eclipse's or Papyrus's development, respectively. Additional UI tests of CARiSMA specific extensions are performed manually. Regularly tested are:

- Analysis definition file (ADF) editor
- Initiation of analysis report cration (export of HTML / XML report)
- CARiSMA perspective (window configuration)

## Partners & roles

This component of the building block "Trustworthy AI: Algorithm assessment" is developed by University of Koblenz and the associated partner Fraunhofer ISST. It complements the AI algorithm assessment approaches of LORIA and Affectlog. For the integration with the building block "distributed data visualization", cooperation with HeadAI, Institut Mines Telecom and Visions may become necessary.

## Usage in the dataspace

While the other components of this building block and other building blocks are generally used during run time, this component of the building block "Trustworthy AI: Algorithm assessment" is used during design time. It creates useful information about the scenarios that involve AI algorithms to process personal data.


# AffectLog's Trustworthy AI (ALT-AI) - **Design Document**

## **Summary**

The AffectLog's Trustworthy AI (ALT-AI) provides a suite of tools for the explanation, visualization, and understanding of complex machine learning models. It acts as a bridge between raw model output and actionable insights, making it easier for data scientists and stakeholders to interpret model predictions, understand feature importance, and evaluate model fairness and performance across different segments. This ALT-AI BB integrates seamlessly with various machine learning frameworks, supporting a wide range of models from simple linear regressions to complex ensemble and deep learning models.

## **Technical Usage Scenarios & Features**

The ALT-AI provides a set of functionalities critical for understanding and interpreting machine learning model behaviors. It helps in identifying model biases, understanding feature contributions, and comparing model performances.

### **Features/Main Functionalities**

- **Model Explanation**: Generates explanations for predictions made by machine learning models, including global explanations that describe overall model behavior and local explanations that detail specific predictions.
- **Feature Importance**: Quantifies the contribution of each feature to the model's predictions, enabling users to understand which features are most influential.
- **Model Comparison**: Allows for the comparison of different models to understand which performs better and why, across various metrics and data segments.
- **Fairness Analysis**: Assesses models for fairness across different groups, helping identify and mitigate biases.

### **Technical Usage Scenarios**

- **Model Development and Validation**: Data scientists can use the ALT-AI BB to interpret model decisions, compare different models, and validate model performance to ensure it meets business requirements.
- **Audit and Compliance**: In sensitive use cases, the ALT-AI BB can help in providing necessary documentation and explanations for model decisions, facilitating compliance with regulations like GDPR.
- **Feature Engineering**: By understanding feature importance, data scientists can better engineer features to improve model performance.

## **Requirements**

- **R1**: ALT-AI MUST support integration with popular Python-based machine learning libraries such as scikit-learn, TensorFlow, and PyTorch.
- **R2**: ALT-AI MUST provide APIs for generating model explanations, and feature importance scores.
- **R3**: ALT-AI MUST ensure the privacy and security of data used for generating explanations.

## **Integrations**

### **Direct Integrations with Other BBs**

- **Decentralized AI Training BB (#1)**: Directly integrates with model training BB to retrieve trained models for analysis.
- **Data Value chain tracker BB (#6)**: Integrates with data value chain tracker BB to apply the same data transformations during the explanation process while also including the causal inference for individual data points.

### **Integrations via Connector**

- **Distributed Data Visualization BB (#7)**: Integrates through connectors to distributed visualization BBs for advanced graphical representations of explanations and feature importances.

## **Relevant Standards**

### **Data Format Standards**

- Adheres to common data exchange formats like JSON and CSV for input and output data, ensuring compatibility with a wide range of data sources and systems.

### **Mapping to Data Space Reference Architecture Models**

- Maps to the Data Space Support Centre (DSSC) guidelines for data management and processing, ensuring interoperability within data spaces.

## **Input / Output Data**

- **Input Data**: Model object and test datasets in supported formats (e.g., DataFrame for Python).
- **Output Data**: Explanation results in JSON format, including feature importance scores, prediction explanations, and fairness analysis results.

## **Architecture**

The ALT-AI comprises several components:

- **Model Adapter**: Adapts various types of machine learning models to a standardized format for analysis.
- **Explanation Generator**: Core component that utilizes ALT-AI functions to generate explanations, and feature importances.
- **Results Processor**: Formats and organizes explanation results for easy consumption and visualization.
- **Security Layer**: Ensures data privacy and security throughout the explanation process.

![](https://github.com/Prometheus-X-association/t-ai/blob/AffectLog360-dd/316105882-5b412b8b-5503-44c4-aa87-727b49acaeff.png?raw=true)

## **Dynamic Behaviour**

Sequence diagram for generating model explanations:


![](https://github.com/Prometheus-X-association/t-ai/blob/AffectLog360-dd/316106084-070d448d-0050-4bc8-94f4-eefc91c10128.png?raw=true)


## **Configuration and Deployment Settings**

- Configuration options include model type, explanation type (global or local), and computational resources allocation.
- Logging operations include tracking of explanation generation processes, error handling, and performance metrics. Error scenarios might involve unsupported model types or data formats, and insufficient computational resources for large datasets.

- Usage limits are defined based on the computational complexity of the models being explained and the size of the dataset. For instance, a limit on the number of features or records that can be processed in a single explanation request may be set to ensure optimal performance.

## **Third Party Components & Licenses**

- **Pandas/Numpy**: Used for data manipulation and numerical operations, both essential for processing input data and explanation results. Licensed under BSD-3-Clause.
- **Scikit-learn/TensorFlow/PyTorch**: Integrations with these libraries are necessary for processing models built using them. Their licenses are BSD-3-Clause, Apache-2.0, and BSD-3-Clause respectively.

## **Implementation Details**

The implementation focuses on creating a flexible, privacy-preserving and efficient architecture deployable within the use case partner's infrastructure that can adapt various machine learning models for explanation. Special attention is given to the scalability of the system, ensuring that it can handle large datasets and complex models without significant performance degradation. Additionally, the implementation ensures that the system is secure and respects data privacy norms, making it suitable for use in sensitive and regulated environments.

## **OpenAPI Specification**

In the future, an OpenAPI specification will be provided for the ALT-AI's RESTful API, detailing available endpoints for submitting models for explanation, retrieving results, and managing user sessions and data security.

## **Test Specification**

### **Test Plan**

The testing strategy will include unit tests, integration tests, and UI tests (where relevant), employing a combination of automated and manual testing methods to ensure comprehensive coverage.

- **Tools**: PyTest for unit tests, Postman for API integration tests, and Selenium for UI tests (if a web interface is provided).

### **Unit Tests**

- **Model Adapter Tests**: Verify that various model types are correctly adapted for analysis.
- **Explanation Generator Tests**: Ensure that explanations, feature importances, and model comparisons are accurately generated for different model types and datasets.

### **Integration Tests**

- **End-to-End Workflow Tests**: Test the complete workflow from model submission through explanation generation to results retrieval.
- **API Endpoint Tests**: Verify that all RESTful API endpoints respond correctly to valid and invalid requests, handling errors gracefully.

### **UI Test (Where Relevant)**

- If a web interface is provided for interacting with the ALT-AI, UI tests will validate the usability and correctness of the interface, including form submissions, results display, and error messaging.

This comprehensive test specification aims to ensure that the ALT-AI operates reliably and efficiently, providing valuable insights into machine learning model behavior while maintaining high standards of usability, security, and compliance.

### Project Title

**Author**
Ramya Gadicharla

#### Executive summary
This project explores whether a single consolidated ACH file can be created that preserves all essential transaction scenarios while eliminating redundancy. By applying clustering, classification, and dimensionality reduction techniques, the goal is to produce a NACHA‑compliant file that represents the full diversity of ACH activity. The consolidated file will streamline validation of ACH processing systems, reduce manual effort, and improve confidence in system reliability

#### Rationale
Why should anyone care about this question?
ACH testing today often requires executing hundreds of separate files, many of which contain repetitive or overlapping scenarios. This leads to wasted time, higher operational costs, and difficulty ensuring complete validation. Without addressing this inefficiency, organizations risk incomplete testing, missed defects, and delays in system updates. A single consolidated file that captures the diversity of ACH activity will:
- Streamline testing cycles
- Reduce manual effort and redundancy
- Improve defect detection and compliance validation
- Enhance confidence in system reliabilit

#### Research Question
What are you trying to answer?
Can we create a single consolidated ACH file that preserves all essential transaction scenarios while eliminating redundancy, enabling efficient and comprehensive validation of ACH processing systems?

#### Data Sources
What data will you use to answer you question?
- For initial testing, I am using a program to generate ACH files
- NACHA format guides and documentation for validating structure, totals, and compliance rules
- In addition to this, I will be using pblicly available sample ACH files from developer libraries


#### Methodology
- Clustering (K‑Means): Group similar ACH records by transaction type, batch attributes, and key fields to identify redundancy and select representative samples.
- Classification (Logistic Regression): Label transactions accurately across categories (PPD, CCD, WEB, debit vs credit, routing groups) to ensure coverage of all classes.
- Dimensionality Reduction (PCA): Visualize variation across ACH files and confirm that the consolidated file captures the full diversity of scenarios

#### Results
What did your research find?
- A single NACHA‑compliant ACH file can be constructed that represents all major transaction categories and edge cases.
- Diversity : The file includes several SEC codes (PPD, WEB, TEL, BOC, CCD, RCK) and different routing numbers, so it covers a range of payment scenarios and institutions.
- Debit‑heavy imbalance: All transactions in the sample were debits. No credits appeared, which means the dataset does not yet represent the full variety of ACH activity.
- Cluster redundancy: Some clusters overlapped, with multiple groups representing debit transactions that differed mainly by routing number. This reduces the uniqueness of the clusterrs
- File integrity: Transaction totals matched correctly in batch and file control records, confirming that the NACHA structure was followed


#### Next steps
- Expand dataset coverage with additional ACH samples from diverse sources.
- Explore addditional clustering methods (DBSCAN, Gaussian Mixture Models) for finer redundancy detection.
- Develop dashboards to visualize coverage and diversity.


#### Outline of project
- Program to generate synthetic ACH file  
- Source program used for analysis

##### Contact and Further Information

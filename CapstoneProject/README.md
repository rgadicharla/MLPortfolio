### Project Title
Behavioral Clustering for ACH Transaction Consolidation

**Author**
Ramya Gadicharla

#### Executive summary
This project explores whether a single consolidated ACH file can be created that preserves all essential transaction scenarios while eliminating redundancy. By applying clustering, classification, and dimensionality reduction techniques, the goal is to produce a NACHA‑compliant file that represents the full diversity of ACH activity. The consolidated file will streamline validation of ACH processing systems, reduce manual effort, and improve confidence in system reliability

#### Rationale
ACH testing today often requires executing hundreds of separate files, many of which contain repetitive or overlapping scenarios. This leads to wasted time, higher operational costs, and difficulty ensuring complete validation. Without addressing this inefficiency, organizations risk incomplete testing, missed defects, and delays in system updates. A single consolidated file that captures the diversity of ACH activity will:
- Streamline testing cycles
- Reduce manual effort and redundancy
- Improve defect detection and compliance validation
- Enhance confidence in system reliability

#### Research Question
Can we create a single consolidated ACH file that preserves all essential transaction scenarios while eliminating redundancy, enabling efficient and comprehensive validation of ACH processing systems?

#### Data Sources
- To answer this question, the project uses:
- A custom synthetic ACH file generator that produces structurally valid NACHA records for controlled experimentation
- NACHA format guides and official documentation to validate record structure, totals, and compliance rules

#### Methodology
1. Data Preparation
- Loaded and cleaned the full ACH dataset.
- Selected key transaction features and standardized numerical fields.
2. Dimensionality Reduction
- Applied PCA to project the dataset into two components for visualization and clustering.
- PC1 and PC2 capture the dominant behavioral variance.
3. Clustering
- Ran clustering (e.g., KMeans) on the PCA space to group transactions into behavioral clusters.
- Assigned each record a Cluster ID, which became the basis for stratified sampling.
4. Consolidation Strategy
- Built the consolidated file using stratified sampling across clusters, ensuring proportional representation.
- Included additional sampling axes such as routing bucket and debit/credit flag to maintain diversity within clusters.
5. Validation
To confirm whether all the clusters were represented, several checks were performed:
- Cluster Proportion Comparison — verified that cluster distributions match between full and consolidated datasets.
- Density Comparison — used 2D KDE plots to ensure the consolidated file covers the same PCA regions.
- Decision Tree Check — trained a model to predict clusters and confirmed that decision boundaries remain consistent.
- Visual Overlays — compared full vs consolidated structure in PCA space.
6. Output
The final consolidated file preserves the structure, diversity, and behavioral patterns of the full ACH dataset while being significantly smaller and easier to use for testing and analysis.

#### Results
- A representative consolidated ACH file can be constructed that preserves the major behavioral patterns and structural diversity of the full dataset while remaining NACHA‑compliant.
- Diversity:
The consolidated file includes multiple routing buckets, transaction codes, and a balanced spread across behavioral clusters, ensuring coverage of a wide range of payment scenarios and institutions.
- Cluster coverage:
All clusters from the full dataset appear in the consolidated file, and cluster proportions remain broadly consistent. Cluster shapes in PCA space are also preserved, indicating that the consolidation maintains underlying behavioral structure.
- Debit/Credit imbalance:
The consolidated sample reflects the natural skew of the original dataset, which is heavily debit‑dominant. Debit transactions remain under‑represented, suggesting the need for targeted sampling if additional coverage is required.
- Cluster redundancy:
Some clusters show partial overlap, especially among debit‑heavy groups that differ mainly by routing bucket. This indicates that certain behavioral patterns are similar and may not require separate representation in future consolidation iterations.
- File integrity:
All batch and file control totals match expected NACHA requirements. Record counts, hash totals, and debit/credit amounts reconcile correctly, confirming that the consolidated file is structurally valid and ready for downstream ACH testing.
- File size constraints
Early experiments used 5000 line ACH files, but this volume caused significant slowdowns during PCA, clustering, and visualization. To maintain performance and ensure reproducible analysis, the working file size was reduced to 1000 ACH records per file


#### Next steps
- Improve credit representation
Add targeted sampling so credit transactions appear in the consolidated file and better reflect real ACH activity.
- Refine clustering
Adjust clustering parameters by including additional ACH file features like SEC code, transaction code groupings, etc. to reduce overlap among transaction groups and improve the uniqueness of behavioral segments.
- Automate the consolidation pipeline
Package PCA, clustering, sampling, and validation into a reproducible workflow for consistent future generation.


#### Outline of project
- Program to generate synthetic ACH files
https://github.com/rgadicharla/MLPortfolio/blob/main/CapstoneProject/SampleACHFileGenerator.ipynb

- Source program used for analysis
https://github.com/rgadicharla/MLPortfolio/blob/main/CapstoneProject/UnifiedACHFileGenerator.ipynb

- Data files
https://github.com/rgadicharla/MLPortfolio/tree/main/CapstoneProject/data

##### Contact and Further Information

- Ramya Gadicharla
 ramya.sameera@gmail.com


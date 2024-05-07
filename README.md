# rbp-disease-prediction
Overview
This repository outlines the methodology for creating a predictive model focused on evaluating translation changes in response to specific treatments. Leveraging Ribo-seq data and various genomic inputs, the model aims to forecast translational outcomes influenced by treatments, rather than solely identifying RBP roles.

## Data Preparation Steps
### Step 1: GENCODE Annotation Conversion
* Downloaded the GENCODE gene annotation file, Release 45.
* Converted the file into a CSV format, adding column headers as per the GENCODE GTF file format description.
* Filtered to retain only exon-related data.
* Refined the 'attributes' column to segregate key information into distinct columns using Python dictionaries.

Step 2: ENCODE RBP Interaction Processing
•	Acquired NarrowPeak bed files for 139 unique RBPs.
•	Formatted the files by adding appropriate headers based on ENCODE's format.
•	Checked for overlaps between RBP peaks and exon data to identify significant interactions.
Step 3: Replicate Consistency Check
•	Processed each RBP's data separately, including six repeated studies.
•	Compiled a final dataset of consistent findings across repeated experiments.
Step 4: CSV to GFF3 Conversion
•	Implemented csv_to_gff3 function for converting the CSV file to GFF3 format.
•	Ensured alignment with gene annotations for accurate Ribo-seq data mapping.
Step 5: Ribo-seq Feature Counting and TPM Normalization
•	Conducted FeatureCount analysis via the Galaxy platform.
•	Normalized the resulting count files based on gene length using TPM normalization.
Step 6: Dataset Compilation
•	Compiled a comprehensive dataset aligning RBP signals with gene IDs.
•	Calculated the mean of SignalValue for each gene.
•	Summed up SignalValues for unique gene IDs.
Step 7: Data Integration
•	Integrated TPM normalized FeatureCounts with RBP signals into a final dataset.
•	Prepared the dataset for model training and evaluation.
Data Analysis and Model Training
Differential Expression and One-Hot Encoding
•	Applied differential expression analysis to quantify translation level differences.
•	Employed one-hot encoding to convert categorical variables for machine learning analysis.
Model Construction
•	Trained machine learning models to categorize genes based on differential expression.
•	Utilized XGBoost and other classifiers, tuning hyperparameters for optimal performance

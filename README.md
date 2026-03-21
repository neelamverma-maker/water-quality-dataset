# water-quality-dataset
Pre-Workshop open‑source water quality dataset
This dataset is about the Chemical composition of water samples, for drinking water quality analysis. The columns represent the concentration of various elements in milligrams per liter (mg/L):
**As/mg/L (Arsenic)
Cu/mg/L (Copper)
Fe/mg/L (Iron)
Li/mg/L (Lithium)
Mn/mg/L (Manganese)
Mo/mg/L (Molybdenum)
Pb/mg/L (Lead)
U/mg/L (Uranium)**

These are all critical indicators in the context of water quality, particularly for drinking water. Their concentrations are measured because they can affect the health and the quality (taste, appearance) of the water.

Element (Symbol
Element (Name)
Category/Significance
Key Health/Quality Impact
As
Arsenic
 Toxic Metalloid/Hazardous Heavy Metal
Strongly linked to serious chronic diseases, including an increased risk of bladder and other cancers.
Pb
Lead
 Highly Toxic Heavy Metal/Hazardous
Harmful in very small quantities; causes cardiovascular disease, developmental abnormalities, and neurologic disorders, particularly in children.
U
Uranium
 Radioactive Element/Hazardous
Can cause toxic effects on the kidneys and increase the risk of cancer.
Cu
Copper
 Essential Element
Excess can cause acute toxicity (gastrointestinal distress) and lead to a metallic taste in water.
Fe
Iron
 Essential Element
Excess leads to discolored water (reddish-brown), staining of fixtures, and an unpleasant taste.
Mn
Manganese
 Essential Element
High levels can be neurotoxic and are associated with a poor taste in water and black staining.
Mo
Molybdenum
 Essential Trace Element
Ingesting high amounts can lead to adverse health effects.
Li
Lithium
 Trace Metal
Monitored to understand its geological source and potential health effects at high levels.

The unit for all the chemical elements is mg/L, which stands for milligrams per liter. This is a standard unit for measuring the concentration of dissolved substances in water, indicating the mass of the element per volume of water.

The dataset does not include any spatial information. There are no columns to identify the location.
Temporal (Time/Frequency): The dataset does not include any temporal information. There are no columns to indicate the date, time, or period when the samples were taken. Therefore, it is impossible to determine the measurement frequency from the data alone.
Based on the analysis of the data, here is an assessment of missing values, outliers, inconsistencies, and measurement limitations:
1. Inconsistencies and Measurement Limitations (The 'BDL' Values)
The most significant data quality issue is the presence of 'BDL' (Below Detection Limit) entries in all concentration columns (except for As/mg/L and Li/mg/L):

Variables Affected: Cu/mg/L, Fe/mg/L, Mn/mg/L, Mo/mg/L, Pb/mg/L, and U/mg/L.
Meaning: 'BDL' indicates a measurement limitation, meaning the concentration of the element was too low to be reliably quantified by the analytical equipment used. 

The true value is somewhere between zero and the detection limit of the instrument.

Impact: Since these values are not numeric, they were treated as missing (NaN) during the quantitative analysis. 
This will reduce the sample data.
From total samples of 1392 / 1353 (39 BDL Removed)

When performing calculations or visualizations, these 'BDL' values must be addressed, typically by:
Excluding the samples with 'BDL' 
2. Missing Values
No Explicit Missing Values: The initial inspection indicated no explicitly missing values (NaNs) across all 174 rows. However, the 'BDL' entries act as implicit missing data for quantitative analysis, as explained above.
3. Outliers
The maximum value for most concentration columns, suggesting the presence of significant outliers:

The maximum value for Arsenic, Manganese, and Lithium suggests a few samples may have concentrations orders of magnitude higher than the typical data, which may represent true high-concentration events, measurement errors, or samples from a different source.
The primary data quality challenges are the 'BDL' entries (a measurement limitation) that reduce the sample size for analysis, and the presence of significant outliers in the concentration data, particularly for Arsenic, Manganese, and Lithium.
Based on the observations the dataset's reliability for decision-making is moderate, and any conclusions should be made with significant caution and appropriate data handling.
Conclusion for Decision-Making
Before using this data for critical decisions (e.g., policy changes, issuing warnings, or large-scale treatment plans), it is strongly recommended to perform a few steps:
Investigate Outliers: Determine the source and validity of the extreme high values in As, Mn, and Li. If possible, confirm the measurements or verify the sample collection process for those specific rows.
Explicitly Handle 'BDL': Decide on a consistent method for handling 'BDL' values. For public health decisions, it is often safer to be conservative, such as assuming the concentration is at the full detection limit, or using specialized statistical methods for censored data.
Acknowledge Limitations: Any final decision or report must clearly state that the analysis is based on data that contains values below the detection limit and is heavily influenced by a few high-concentration outlier samples.
Challenges in Working with This Dataset are as below:

Handling Censored Data ('BDL'): 
Presence of Extreme Outliers
Lack of Spatial and Temporal Context:
What analytical methods would you apply to this dataset?

The analysis of this dataset requires a combination of statistical, visual, and specialized data-handling methods, particularly due to the presence of 'BDL' (Below Detection Limit) values and extreme outliers.

Here are the key analytical methods that should be applied:
1. Data Preparation and Cleaning (Essential First Steps)
2. Descriptive and Compliance Analysis
3. Comparative Analysis (Treated vs. Untreated)
Additional Data That Would Improve the Analysis:

The reliability and depth of the analysis would be greatly enhanced by adding the following data points:
Spatial and Geographic Information:
Source Identifier: A unique ID or name for the well, reservoir, or treatment plant from which the sample was taken.
Geographic Coordinates: Latitude and longitude to map the contamination and analyze patterns related to geology or infrastructure.
Temporal Information:
Collection Date and Time: To analyze trends, seasonality, and the impact of specific events on water quality.
Contextual/Metadata for Contaminants:
Regulatory Limits (MCLs): The Maximum Contaminant Levels (MCLs) that the water is being tested against. This would allow for an immediate and precise calculation of compliance/risk.
Detection Limit Values: The actual numeric detection limit (in mg/L) for each element. Knowing this value would allow for a more statistically sound imputation of the 'BDL' entries (e.g., replacing 'BDL' with half the documented limit).


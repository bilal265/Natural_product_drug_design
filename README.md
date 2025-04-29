# Natural Product vs. Drug Similarity Analysis Report

## Introduction

This report details the analysis performed to assess the structural similarity between a set of drugs and natural products (NPs). The primary method employed is the calculation of the Maximum Common Substructure (MCS) between pairs of molecules. A Tanimoto-like similarity score, based on the heavy atom count of the MCS relative to the total heavy atoms in the compared molecules, was used as the quantitative measure of similarity. The analysis aims to identify relationships and potential structural overlaps between these chemical entities, which can be valuable in drug discovery and design, particularly in understanding how natural products might relate to existing drugs or serve as scaffolds for new ones. The tasks were performed using Python, leveraging libraries such as RDKit for cheminformatics operations, Pandas for data manipulation, and Seaborn/Matplotlib for visualization. The analysis was based on the requirements specified in the `Natural_product_task_2025.pdf` document and utilized the provided datasets: `data_drug.csv` and `data_np.csv`.




## Task Description and Methodology

### Task 1: Analysis of Drug-Natural Product Similarities Based on Maximum Common Substructures

The primary objective of this analysis was to evaluate the structural similarities between drugs and natural products using Maximum Common Substructure (MCS) calculations. The specific tasks included:

1. Calculating MCS for drug vs drug comparisons
2. Calculating MCS for natural product (NP) vs NP comparisons
3. Calculating MCS for drug vs NP comparisons
4. Analyzing and visualizing the results using heatmaps to identify interesting MCS clusters

### Methodology

#### Data Preparation
Two datasets were used for this analysis:
- `data_drug.csv`: Contains drug information with columns NAME and Smiles
- `data_np.csv`: Contains natural product information with columns NAME and SMILES

The datasets were loaded and preprocessed to ensure consistency in column naming and to remove any entries with missing SMILES strings.

#### MCS Calculation
The Maximum Common Substructure (MCS) calculation was performed using the RDKit library's `FindMCS` function. For each pair of molecules, the following information was calculated:
- Number of heavy atoms in molecule A
- Number of heavy atoms in molecule B
- Number of heavy atoms in the MCS
- MCS SMARTS string representation
- Tanimoto-like similarity score

The Tanimoto-like similarity score was calculated using the formula:
```
Similarity = |MCS(A, B)|b / (|A|b + |B|b - |MCS(A, B)|b)
```
Where:
- |A|b is the number of heavy atoms in molecule A
- |B|b is the number of heavy atoms in molecule B
- |MCS(A, B)|b is the number of heavy atoms in the MCS

This similarity score ranges from 0 (no similarity) to 1 (identical structures).

#### Visualization
The similarity results were visualized using heatmaps, which provide an intuitive way to identify clusters of similar structures. Three heatmaps were generated:
1. Drug vs Drug similarity
2. NP vs NP similarity
3. Drug vs NP similarity

The heatmaps use a color gradient from dark purple (low similarity) to bright yellow (high similarity) to represent the similarity scores.

## Results and Analysis

### Drug vs Drug Similarity Analysis

The heatmap below shows the MCS-based Tanimoto similarity between pairs of drugs:

![Drug vs Drug Similarity Heatmap](/home/ubuntu/heatmap_drug_drug.png)

**Observations:**
- The diagonal elements show self-similarity (value of 1.0, bright yellow)
- Most drug pairs show relatively low similarity (dark purple to blue colors), indicating diverse chemical structures in the drug dataset
- Several small clusters of moderate similarity (green-blue regions) can be observed, suggesting groups of drugs that share common substructures
- A few bright spots off the diagonal indicate drug pairs with high structural similarity

### Natural Product vs Natural Product Similarity Analysis

The heatmap below shows the MCS-based Tanimoto similarity between pairs of natural products:

![NP vs NP Similarity Heatmap](/home/ubuntu/heatmap_np_np.png)

**Observations:**
- The natural product dataset shows more scattered regions of moderate to high similarity compared to the drug dataset
- Several distinct clusters of natural products with shared structural features are visible (green-yellow regions)
- The overall similarity pattern suggests that natural products may have more structural diversity within certain chemical classes
- Some natural product pairs show very high similarity (bright yellow spots), indicating nearly identical core structures

### Drug vs Natural Product Similarity Analysis

The heatmap below shows the MCS-based Tanimoto similarity between drugs and natural products:

![Drug vs NP Similarity Heatmap](/home/ubuntu/heatmap_drug_np.png)

**Observations:**
- The overall similarity between drugs and natural products is generally lower than within-group similarities
- A few bright spots indicate specific drug-NP pairs with significant structural overlap
- Several drugs show moderate similarity (blue-green regions) with multiple natural products, suggesting potential scaffolds derived from or inspired by natural sources
- The pattern of similarity is more dispersed, without clear large clusters, indicating selective structural relationships rather than broad chemical class similarities

## Discussion and Conclusion

The analysis of Maximum Common Substructures between drugs and natural products provides valuable insights into their structural relationships. The key findings from this analysis include:

1. **Structural Diversity**: Both the drug and natural product datasets exhibit considerable structural diversity, as evidenced by the predominance of low similarity scores in the heatmaps.

2. **Distinct Clustering Patterns**: Natural products show more distinct clustering patterns compared to drugs, suggesting that natural products may have evolved within certain structural constraints or biosynthetic pathways.

3. **Selective Drug-NP Relationships**: The drug vs NP heatmap reveals selective rather than broad structural relationships, with specific drug-NP pairs showing notable similarity. This supports the historical observation that many drugs are either derived from or inspired by natural products, but with significant structural modifications.

4. **Potential for Drug Discovery**: The identified high-similarity pairs between drugs and natural products could serve as starting points for exploring new drug candidates. Natural products with high similarity to effective drugs might possess similar bioactivities and could be investigated as alternative therapeutic agents.

5. **Scaffold Analysis**: The MCS approach effectively identifies common scaffolds between molecules, which is particularly valuable in medicinal chemistry for understanding structure-activity relationships.

These findings highlight the utility of MCS-based similarity analysis in understanding the structural relationships between drugs and natural products. Such analyses can guide drug discovery efforts by identifying promising natural product scaffolds that could be developed into new therapeutic agents.

## Future Work

Future extensions of this analysis could include:
- Incorporating bioactivity data to correlate structural similarity with functional similarity
- Expanding the datasets to include more diverse chemical structures
- Clustering analysis to formally identify and characterize structural groups
- Detailed examination of the highest similarity pairs to understand the nature of their structural relationships
- Integration with other similarity metrics (e.g., fingerprint-based) for a more comprehensive similarity assessment


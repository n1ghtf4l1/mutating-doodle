#### mutating-doodle

# **Enzyme Stability Prediction**

##### Develop models that can predict the ranking of protein stability (as measured by melting point, ```tm```) after single-point amino acid mutation and deletion. 

### **Goal**

Enzymes are proteins that act as catalysts in the chemical reactions of living organisms. The [objective](https://www.kaggle.com/competitions/novozymes-enzyme-stability-prediction/) is to predict the thermal stability of enzyme variants. The experimentally measured thermal stability (melting temperature) data includes natural sequences, as well as engineered sequences with single or multiple mutations upon the natural sequences.

Understanding and accurately predict protein stability is a fundamental problem in biotechnology. Its applications include enzyme engineering for addressing the world’s challenges in sustainability, carbon neutrality and more. Improvements to enzyme stability could lower costs and increase the speed scientists can iterate on concepts.

### **Context**

**Novozymes** finds enzymes in nature and optimizes them for use in industry. In industry, enzymes replace chemicals and accelerate production processes. They help our customers make more from less, while saving energy and generating less waste. Enzymes are widely used in laundry and dishwashing detergents where they remove stains and enable low-temperature washing and concentrated detergents. Other enzymes improve the quality of bread, beer and wine, or increase the nutritional value of animal feed. Enzymes are also used in the production of biofuels where they turn starch or cellulose from biomass into sugars which can be fermented to ethanol. These are just a few examples as we sell enzymes to more than 40 different industries. Like enzymes, microorganisms have natural properties that can be put to use in a variety of processes. Novozymes supplies a range of microorganisms for use in agriculture, animal health and nutrition, industrial cleaning and wastewater treatment.

However, many enzymes are only marginally stable, which limits their performance under harsh application conditions. Instability also decreases the amount of protein that can be produced by the cell. Therefore, the development of efficient computational approaches to predict protein stability carries enormous technical and scientific interest. 

Computational protein stability prediction based on physics principles have made remarkable progress thanks to advanced physics-based methods such as FoldX, Rosetta, and others. Recently, many machine learning methods were proposed to predict the stability impact of mutations on protein based on the pattern of variation in natural sequences and their three dimensional structures. More and more protein structures are being solved thanks to the recent breakthrough of AlphaFold2. However, accurate prediction of protein thermal stability is still a great challenge.

Our Goal is to develop a model to predict/rank the thermal stability of enzyme variants based on experimental melting temperature data, which is obtained from Novozymes’s high throughput screening lab. Access to data from previous scientific publications are provided. The available thermal stability data spans from natural sequences to engineered sequences with single or multiple mutations upon the natural sequences. If successful, we can help tackle the fundamental problem of improving protein stability, making the approach to design novel and useful proteins, like enzymes and therapeutics, more rapidly and at lower cost.

Novozymes is the world’s leading biotech powerhouse. Our growing world is faced with pressing needs, emphasizing the necessity for solutions that can ensure the health of the planet and its population. At Novozymes, we believe biotech is at the core of connecting those societal needs with the challenges and opportunities our customers face. Novozymes is the global market leader in biological solutions, producing a wide range of enzymes, microorganisms, technical and digital solutions which help our customers, amongst other things, add new features to their products and produce more from less.

Together, we find biological answers for better lives in a growing world. Let’s Rethink Tomorrow. This is Novozymes’ purpose statement. Novozymes strives to have great impact by balancing good business for our customers and our company, while spearheading environmental and social change. In 2021, Novozymes enabled savings of 60 million tons of CO2 in global transport. 

### **Dataset Description**

The goal is to develop models that can predict the ranking of protein stability (as measured by melting point, ```tm```) after single-point amino acid mutation and deletion.

For the training set, the protein stability (experimental melting temperature) data includes natural sequences, as well as engineered sequences with single or multiple mutations upon the natural sequences. The data are mainly from different sources of published studies such as [Meltome atlas—thermal proteome stability across the tree of life](https://doi.org/10.1038/s41592-020-0801-4). Many other public datasets exist for protein stability; please see the competition [Rule 7C](https://www.kaggle.com/competitions/novozymes-enzyme-stability-prediction/rules) for external data usage requirements. There are also other publicly available methods which can predict protein stabilities such as [ESM](https://doi.org/10.1073/pnas.2016239118), [EVE](https://doi.org/10.1038/s41586-021-04043-8) and [Rosetta](https://doi.org/10.1016/B978-0-12-381270-4.00019-6) etc., without using the provided training set. These methods may also be used as part of the competition.

The test set contains experimental melting temperature of over 2,413 single-mutation variant of an enzyme (GenBank: KOC15878.1), obtained by Novozymes A/S. The amino acid sequence of the wild type is:

```
VPVNPEPDATSVENVALKTGSGDSQSDPIKADLEVKGQSALPFDVDCWAILCKGAPNVLQRVNEKTKNSNRDRSGANKGPFKDPQKWGIKALPPKNPSWSAQDFKSPEEYAFASSLQGGTNAILAPVNLASQNSQGGVLNGFYSANKVAQFDPSKPQQTKGTWFQITKFTGAAGPYCKALGSNDKSVCDKNKNIAGDWGFDPAKWAYQYDEKNNKFNYVGK
```

#### **Files**

- **train.csv** - the training data, with columns as follows:
    - ```seq_id```: unique identifier of each protein variants
    - ```protein_sequence```: amino acid sequence of each protein variant. The stability (as measured by ```tm```) of protein is determined by its protein sequence. (Please note that most of the sequences have the same length of 221 amino acids, but some of them have 220 because of amino acid deletion.)
    - ```pH```: the scale used to specify the acidity of an aqueous solution under which the stability of protein was measured. Stability of the same protein can change at different pH levels.
    - ```data_source```: source where the data was published
    - ```tm```: target column. Since only the spearman correlation will be used for the evaluation, the correct prediction of the relative order is more important than the absolute ```tm``` values. (Higher ```tm``` means the protein variant is more stable.)

- **test.csv** - the test data; your task is to predict the target ```tm``` for each ```protein_sequence``` (indicated by a unique seq_id)

- **sample_submission.csv** - a sample submission file in the correct format, with ```seq_id``` values corresponding to **test.csv**

- **wildtype_structure_prediction_af2.pdb** - the 3 dimensional structure of the enzyme listed above, as predicted by AlphaFold

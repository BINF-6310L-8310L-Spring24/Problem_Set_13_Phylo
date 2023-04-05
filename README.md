# Problem_Set_12

This week we will use phylogenetic compatative methods to analyze the dataset presented in "The whale shark genome reveals how genomic and physiological properties scale with body size" from Weber et al 2020

We will analyze the phenotypic trait data because the genomic features *were not* provided in the supplemental files. While the genome versions are listed in the paper, they should have provided the summary statistics as the genome versions may become unavailable in the future. In this case, it would also be appropriate to email the corresponding author to ask for the genome statistics.


The phenotypic data is in the file ```church_data.txt```

This contains the columns 
- Species - species name that exactly matcch the tree
- Class - the class of the organism
- Max_Life - the reported maximum lifespan
- Max_Weight - the reported maximum weight
- Body_Temp - the body temp of the organism
- Metabolic_Rate - the metabolic rate 

The phylogenetic tree is in ```church_spec_final.nwk``` 

This is a newick formatted tree 


### Problem 1 - Read in the data & get log10 values

- Read in the phenotype file 
- Read in the ree using the ```read.tree()``` function 
- Create a new column in the data file containing the log10 values for Max_Life and Max_Weight (use the function ```log10()```)
- Report the log10 values for Max_Life and Max_Weight for *Ailuropoda melanoleuca*

### Problem 2 - Linear relationship between Weight and Lifespan 

- Use the ```pgls()``` function to 



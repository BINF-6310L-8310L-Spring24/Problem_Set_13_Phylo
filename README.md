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


### Problem 1 - Read in the data & get log10 values (1 point)

- Read in the phenotype file 
- Read in the ree using the ```read.tree()``` function 
- Create a new column in the data file containing the log10 values for Max_Life and Max_Weight (use the function ```log10()```)
- Report the log10 values for Max_Life and Max_Weight for *Ailuropoda melanoleuca*

### Problem 2 - Linear relationship between Weight and Lifespan (3 points)

- Use the ```pgls()``` function to obtain a phylogenetic linear model between the log10 of Max Life and Max Weight (use the formula Max_Weight_ln ~ Max_Life_ln). Also estimate the lambda parameter by using ```lambda="ML"```
- Use the ```gls()``` function to obtain a standard linear model between the log10 Max Life and Max Weight 
- Plot the data and add the two regression lines 
- Based on this result do we expect a greater or smaller change in max weight for each unit increase in max life for the PGLS as compared to the GLS? In other words, does the PGLS increase or decrease the slope of the line?

### Problem 3 - phylANOVA (3 points)

To conduct our phylANOVA we will have to do a few pieces of modification to our dataset

- Create a subset of the dataset including only the species in the Mammalia and Actinopterygii classes
- Subset the tree to include only these species using the ```keep.tip()``` functon. This may look something like ```churchTree_sub<-keep.tip(churchTree, church_sub$species)```
- We also need to clean up the tree a bit using the ```collapse.singles()``` function ```churchTree<-collapse.singles(churchTree,root.edge=TRUE)```
- Conduct an ANOVA comparing the Max Lifespan, Max Weight, and Body temperature of Mammals and Actinoptergyii. 
- Which measures are significantly different between Mammals and Actinoptergyii


### Problem 4 - phylPCA (3 points)

Next we will visualize our three variables (Lifespan, Weight, Body Temp) using PCA. 

- Scale the three varaibles using the ```scale()``` function
- Conduct a phylPCA using ```phylPCA``` 
- How much variation is captured in PC1? 
- Combine the PC position data with the original matrix so that you have the species names and classes
- Plot the species on PC1 and PC2. Use the function ```geom_text(aes(label=species))``` to include the spcies names on the plot
- Which three species are clear outliers in the data?


### Knit and upload your document 



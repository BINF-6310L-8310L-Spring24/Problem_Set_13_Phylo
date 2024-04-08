# Problem_Set_13

**BEFORE YOU BEGIN**

To make sure that we all get the same answers, please use the command `set.seed(123)` before beginning the assignment. 

This week, we will use phylogenetic comparative methods to analyze the dataset presented in "The whale shark genome reveals how genomic and physiological properties scale with body size" from Weber et al 2020

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

## Question 1A
Report the log10 values for Max_Weight for *Ailuropoda melanoleuca*

## Question 1B
Report the log10 values for Max_Life for *Ailuropoda melanoleuca*

&nbsp;
&nbsp;

### Problem 2 - Linear relationship between Weight and Lifespan 

- Use the ```pgls()``` function to obtain a phylogenetic linear model between the log10 of Max Life and Max Weight (use the formula Max_Weight_ln ~ Max_Life_ln). Also estimate the lambda parameter by using ```lambda="ML"```
- Use the ```gls()``` function to obtain a standard linear model between the log10 Max Life and Max Weight 
- Plot the data and add the two regression lines
  
## Question 2A
Report the p-value for the PGLS analysis

## Question 2B 
Report the p-value for the GLS analysis 

## Question 2C
Based on this result do we expect a greater or smaller change in max weight for each unit increase in max life for the PGLS as compared to the GLS? In other words, does the PGLS increase or decrease the slope of the line?

## Question 2D
Compare the PGLS and GLS results. Does conducting the PGLS analysis make you more confident that there is a real correlation between Max Weight and Max Life or less confident? 

&nbsp;
&nbsp;

### Problem 3 - phylANOVA 

To conduct our phylANOVA we will have to do a few modifications to our dataset

- Create a subset of the dataset including only the species in the Mammalia and Actinopterygii classes
- Subset the tree to include only these species using the ```keep.tip()``` functon. This may look something like ```churchTree_sub<-keep.tip(churchTree, church_sub$species)```
- We also need to clean up the tree a bit using the ```collapse.singles()``` function ```churchTree<-collapse.singles(churchTree,root.edge=TRUE)```
- Conduct an ANOVA comparing the Max Lifespan, Max Weight, and Body temperature of Mammals and Actinoptergyii. 

## Question 3A
- Which measures are significantly different between Mammals and Actinoptergyii

&nbsp;
&nbsp;

### Problem 4 - phylPCA (3 points)

Next we will visualize our three variables (Lifespan, Weight, Body Temp) using PCA. 

- Scale the three variables using the ```scale()``` function
- Conduct a phylPCA using ```phylPCA```
- Combine the PC position data with the original matrix so that you have the species names and classes
- Plot the species on PC1 and PC2. Use the function ```geom_text(aes(label=species))``` to include the spcies names on the plot

  
## Question 4A
- How much variation is captured in PC1?

## Question 4B
- Which three species are clear outliers in the data?

### Knit and upload your document 



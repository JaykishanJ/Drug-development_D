<h1 align="center"> Welcome to Team Drug_Development_D, HackBio 2021 </h1>
<img src = "https://www.google.co.in/url?sa=i&url=https%3A%2F%2Fng.linkedin.com%2Fcompany%2Fhackbio&psig=AOvVaw2FFYC-OooobrqCYldDzFBg&ust=1629471453825000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCIie76usvfICFQAAAAAdAAAAABAD">
 
## HackBio Internship:
  HackBio Internship is a virtually regimented 5-week research internship that is practice oriented and focused on equipping scientists around the world with advanced bioinformatics and  computational biology skills. Our team consists of 12 budding researches eager to get a hands-on training on drug development and we present you our work.
 
## Slack User_Name | Contribution |
------------- | -------------- |
@Madhu (leader) | Getting data and separating protein and ligands |
@Jay | Creating CHEMBL compound library |
@Hellrider | Prepare files for docking |
@StephanieEzzy | Docking |
@GeePee | Visualisation of compound library |
@WumiAO | Molecular fingerprints |
@kheira | Molecular fingerprints |
@Kerishnee | Clustering |
@Tifee_ | Post-processing |
@karthika | Post-processing |
@Rita | Visualisation of docking |
@Hammed | Visualisation of docking |

## Contents
*[Introduction](#Introduction)\
*[Workflow](#Workflow)\
*[Get Data](#Get-Data)\
*[Separate protein and ligand](#Separate-protein-and-ligand)\
*[Create compound library](#Create-compound-library)\
*[Prepare files for Docking](#Prepare-files-for-Docking)\
*[Docking](#Docking)\
*[Visualisation of Compound library](#Visualisation-of-compound-library)\
*[Calculate Molecular fingerprints](#Calculate-Molecular-fingerprints)\
*[Clustering](#Clustering)\
*[Post-processing](#Post-processing)\
*[Visualtion of docking](#Visualisation-of-docking)

## Introduction

## Workflow
![Picture1](https://user-images.githubusercontent.com/88226429/130089845-a71a5677-7093-4f99-a9e1-bbf79a299023.png)

## Get data 

## Separate protein and ligand

## Create compound library
![Compound Library](https://user-images.githubusercontent.com/86801284/129846114-5d9afd3a-923b-4964-b705-3d1361e89c78.PNG)

we have used two tools to generate librairy of compounds 
frist we need a SMILE notation as reference in oder to get a similar compound. 
### Compound conversion 
this tool we have used to convert our ligand which is in pdf as input and we get  SMILE as output   
### Search ChEMBL database
once we have SMILE of our ligand now we have used **Search ChEMBL database** 
so we have given SMILE input type "file", we given Ligand SMILE as input file “Tanimoto cutoff score”: 40  and we have given  “Filter for Lipinski’s Rule of Five”: Yes 
this used to perform similarity search, with available compound in chEMBL database with referce to our SMILE.
it used to give output as list of SMILE in file so our library is ready now for next step 


## Preparing files for Docking

## Docking

## Visualisation of Compound library
![Galaxy70- Visualisation_on_data_6](https://user-images.githubusercontent.com/88286597/129873861-b2fdadb9-52c9-4346-aad4-fcf1c7d1a1aa.png)

Here, we used a tool - **Visualization of Compounds** - availabe on Galaxy based on OpenBabel to visualize the chemical structures of the compounds generated. The inputs of the parameters used are as listed:
*“Molecular input file”: **Compound library**
*“Embed molecule as CML”: **No**
*“Draw all carbon atoms”: **No**
*“Use thicker lines”: **No**
*“Property to display under the molecule”: **Molecule weight**
*“Sort the displayed molecules by”: **Molecular weight**
*Format of the resultant picture”*: **SVG**

Upon executing these command inputs, the outcome was as shown in the picture above.

## Calculate molecular fingerprints

The ligand SMILES files was labelled using Replace and Concatenate tools which give us 14 molecules with a clear table, the output was renamed as "Labelled compound library"

The labelled compound library was used to do fingerprinting using Babel FP2 fingerprints and it was renamed as "Fingerprints".

## Clustering
This method can be completed once the molecular fingerprints have been determined.
For this step, two different tools, Taylor-Butina clustering and NxN clustering, were used to cluster molecules. 
Taylor-Butina clustering was used to determine the different classification of moelcules into clusters based on the similarity within their structures.
NxN clustering forms a dendrogram that shows the individual molecules that are represented as vertical lines and merged into clusters.
The clustering of meolcules can be completed using galaxy and the following steps:
Taylor-Butina clustering tool with the following parameters:
param-file “Fingerprint dataset”: ‘Fingerprints’ file.
param-file “threshold”: 0.8
NxN Clustering tool with the following parameters:
param-file “Fingerprint dataset”: ‘Fingerprints’ file.
param-file “threshold”: 0.0
param-file “Format of the resulting picture”: SVG
param-file “Output options”: Image
![download](https://user-images.githubusercontent.com/88290959/129894215-48c2fd25-65ae-44bf-9409-15925f485b0f.jpg)

##  Post-processing

After the Clustering & Fingerprinting  of the molecules, from our collection of SD-files, we first extract all stored values into tabular format and then combine the files together to create a single tabular file. 

![Screenshot (349)](https://user-images.githubusercontent.com/71928132/129947028-f28cdbd2-6ed6-4a1e-9b49-52465e4a5303.png)

We have a tabular file available now which contains all poses calculated for all ligands docked, together with scores and RMSD values for the deviation of each pose from the optimum. We also have PDB files for some of the docking poses which can be inspected using the NGLViewer visualization embedded in Galaxy.

## Visualisation of Docking

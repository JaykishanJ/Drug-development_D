<h1 align="center"> Welcome to Team Drug_Development_D, HackBio 2021 </h1>

## HackBio Internship:
  HackBio Internship is a virtually regimented 5-week research internship that is practice oriented and focused on equipping scientists around the world with advanced bioinformatics and  computational biology skills. Our team consists of 12 budding researches eager to get a hands-on training on drug development and we present you our work.

*To know more about HackBio*
<a href="https://twitter.com/TheHackbio?s=08" target="blank"><img align="center" src="http://assets.stickpng.com/images/580b57fcd9996e24bc43c53e.png" alt="tbi_internship" height="30" width="30" /></a>
<a href="https://thehackbio.com/" target="blank"><img align="center" src="https://pbs.twimg.com/profile_images/1274819410814029824/dAaLhOpD_400x400.jpg" alt="HackBioWebsite" height="30" width="30" /></a>
<a href="https://www.linkedin.com/company/hackbio" target="blank"><img align="center" src="https://www.freeiconspng.com/thumbs/linkedin-logo-png/linkedin-logo-3.png" alt="linkedin" height="20" width="20" /></a>
</p>

---
  
 👥 **Contributors**
 
Slack User_Name | Contribution |
--------------- | -------------- |
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

---

📝 **Contents**
◾ *[Introduction](#Introduction)\
◾ *[Workflow](#Workflow)\
◾ *[Getting started with Galaxy](#Getting-started-with-Galaxy)
◾ *[Get Data](#Get-Data)\
◾ *[Separate protein and ligand](#Separate-protein-and-ligand)\
◾ *[Create compound library](#Create-compound-library)\
◾ *[Prepare files for Docking](#Prepare-files-for-Docking)\
◾ *[Docking](#Docking)\
◾ *[Visualisation of Compound library](#Visualisation-of-compound-library)\
◾ *[Calculate Molecular fingerprints](#Calculate-Molecular-fingerprints)\
◾ *[Clustering](#Clustering)\
◾ *[Post-processing](#Post-processing)\
◾ *[Visualtion of docking](#Visualisation-of-docking)

---

💊 **Introduction**
Computer Aided Drug Design focuses on development of potential compounds against a target based on several biological and physicochemical properties. This project is centered around protein-ligand docking, a molecular modelling technique. The goal of protein–ligand docking is to predict the position and orientation of a ligand when it is bound to a protein receptor or enzyme. It is similar to finding the best key (🔑) to a lock (🔒) when you have a bag full of keys.

⚙️ **Workflow**
![poster](https://user-images.githubusercontent.com/88226429/130165702-e2dca6c4-3c28-4500-8e1f-94b24a2b5077.png)

🛠️ **Tools used** (Galaxy)
![tool flowchart](https://user-images.githubusercontent.com/88226429/130165714-391f931e-ddab-4b18-ac5d-2ab700ab5c43.png)

---

## Getting started with Galaxy
Galaxy is an open, web-based platform for accessible, reproducible, and transparent computational research. 
To start with our work, do the following:
1. Create a galaxy account - https://usegalaxy.eu/
2. Create a new history

---
<h1 align="center">Let's go!</h1>

## Get data 
🛠️**Get PDB**
Using the accession code [2brc](https://www.rcsb.org/structure/2BRC) we get the structure of Hsp90 in PDB format
Note that the protein and ligand are bound together

## Separate protein and ligand
🛠️**Search in textfiles (grep)**
1. To get protein: Remove **HETATM** atoms (HETATM contains ligand atoms, water molecules, ions which are not part of the protein) 
2. To get ligand: Choose only **CT5** atoms (CT5 denotes the ligand atoms - you can see they come under HETATM atoms)
🛠️**Compound conversion**
To convert Ligand from PDB format to **MOL** format and also to **SMILES** format

---

## Create compound library
🛠️**Search ChEMBL database**
With the SMILES of the ligand we collected in the before step, we now search for similar compounds based on SMILES in the ChEMBL Database.
We filter using the following parameters:
**Tanimoto coefficient:** 40
**Lipinski's Rule of Five:** Yes
![lipinski](https://user-images.githubusercontent.com/88226429/130171208-702d7c00-301f-4701-bebe-d29f9cc50ca7.png)
#### The Compound library created had the following compounds: 
![compound library](https://user-images.githubusercontent.com/88226429/130171630-46958778-540a-4236-9177-5d382184535d.png)

---

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

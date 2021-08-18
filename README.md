# Drug Development_D

## Get data and Separate protein and ligand-Madhumitha  


## Generate compound library-Jaykishan 
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


## Preparing files for docking-Mahfuz
We need to prepare our receptor and ligands for docking study. For our receptor preparation we used **Prepare receptor** tool. Our PDB file was used and then the tool converted it into PDBQT format. We changed the file name into 'Protein PDBQT'. We also need to change the ligands format also. In previous step we found 13 compound from "Search ChEMBL database" but it was in .smi format. For multiple ligands we need to change the format to SDF. To do that, we used **Compound conversion** tool and it gave us the compound library in SDF format. We renamed it to "Prepared ligands". Now we have our prepared receptor and ligands also. We need to create a config file for docking. **Calculate the box parameters using RDKit** tool was used for creating our docking config file. The x,y,z-axis buffer was set to 5.0, Exhaustiveness = 1 and Random seed parameter box was left empty. The config file later renamed to "Docking config file". We now have all the files for our docking process.


## Docking

## Visualisation-Isaac Godspower(@GeePee)
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

## Cluster molecules using molecular fingerprint

##  post-processing

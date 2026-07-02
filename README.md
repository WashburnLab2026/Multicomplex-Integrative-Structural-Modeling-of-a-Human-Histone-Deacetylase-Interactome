# Multicomplex-Integrative-Structural-Modeling-of-a-Human-Histone-Deacetylase-Interactome

This repository provides information about scripts and different dataset that were used to determine the 3D structure of dimers, trimer, and sixmer complexes.


### Integrative approach to determine 3D structures of complexes

Scripts are organized as follows:  

#### Data pre-processing  

1-) Assign distance restraints from excel (Assign_dist_rest_from_excel)   
This scripts are used to assign distance restraints from a given excel crosslinking table by:  

    a-) Separate a given excel file into INTRA- and INTER-crosslinks.  
    
    b-) Create a tabulated file with fixed target distance restraints, which is used as an input file to guide the docking with HADDOCK.  
    
    c-) Create a tabulated file with variable target distance restraints, which is used as an input file to guide the docking with HADDOCK  

2-) Combining models or chains into one chain (Comb_models_or_chains_into_chain)    
This script combines multiple models and chains from a given protein complex into one chain, then renumberes residues starting at 1.    
    
Parameters:   
    - input_pdb: Path to the input PDB file.    
    - output_pdb: Path to the output PDB file with renumbered residues.    

3-) Extract chains (extract_chains)  
This script extracts one or more specified chains from a given PDB file and writes the selected chains to a new PDB file.  
$python extract_chains.py input.pdb output.pdb A B  (if using the python version instead of jupyter notebook)  

### Data post-processing  

1-) RMSD clustering (RMSD_clustering)  
This script clusters pdb structures based on the root mean square deviation (RMSD). It uses as a input a path to the
directory that contains a list of PDBs of interest. It outputs a heatmap of different cluster, a barplot distribution, and a summary table.  

2-) Assign chain ID to specific segments (Assign_chainID_2_specific_segment)
This script Assigns different chain IDs to specified residue ranges of a given complex PDB file, then renumber those chains from 1.  

    a-) input_directory: Path to the input PDB files directory.  
    b-) output_directory Path to the folder to save output PDBs  
    c-) The given cahin, default chain A  
    d-) residue_ranges: List of tuples, where each tuple contains:  
                            - (start_residue, end_residue, chain_id)  
    e-) output_file: Path to the output PDB file.  
    
3-) Renumbering residues from individual chains (Renumbering_individual_chains)  
This script renumbers the residues of specific chains (e.g., starting from residue number 1) in a given PDB 
and saves the modified structure into a new PDB file.   

Run the script using the command $python renumber_chains.py input.pdb output.pdb A B; (if using the python version instead of jupyter   notebook)  

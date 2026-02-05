# LRRK2 Protein ML based Ensemble Classifier for APO and Bound state with Allosteric Communication Pathways
- apo and bound xtc files from MD simulation were used as input.
## key aspects of ML classifier and analysis
- The input was sub-sampled with every 20th frame to keep the data reasonable.  
- Specific residues and loops were targeted – pocket 4 loop (1618-1626), active site (1918-1938) and activation loop (2020-2040)
## Features extracted and used as addition inputs 
- RMSF for all the residues in question
- Distances between pocket4 loop and active site residues
- Distances between pocket4_loop and activation loop residues
- Dihedral angles (φ/ψ angles that capture secondary structure and loop rearrangements) normalized using sine/cosine
- PCA/KPCA components of all CA positions
## Analysis
- Per frame feature vector was created using the frame data and above features
- Frames from the same trajectory were grouped as they ae not independent
- Model training and evaluation were conducted in a Google Colab Jupyter Lab environment, enabling scalable computation and reproducibility.
- To prevent data leakage and ensure generalizability, Leave-One-Group-Out cross-validation was employed, with each MD replica treated as an independent group. This validation strategy ensured that the model was tested on trajectories it had not seen during training.
- The classifier was tested for accuracy, precision/recall, and confusion matrix.
- tSINE visual intuition was used to show whether apo and bound states occupy distinct conformation manifolds
- DCCM analysis was performed to show how ligand binding can change cross-correlation between residues thus showing allosteric communication pathway
- A heat map of ΔDCCM was created to show top allosteric links.

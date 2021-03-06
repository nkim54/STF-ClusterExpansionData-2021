0. Script
    - All python scripts used in the study
    - An atomic structure, perovskite oxide (POSCAR_ABO3)

1. Step_1_Define
    - Defining a cluster pool for the atomic structure
    - Script: step_1_cluster.py
        - choose sublattices (atom_ind_group) containing substitute atomic species
        - Setting the maximum number of sites (cut_cluster) and the maximum distance between sites (cut_dist) within a cluster
    - Deliverable: the cluster pool (file_out)

2. Step_2_Coount
    - DFT data sets for each composition (Fe_XXXX - Set)
    - For each DFT data set, collect cluster information and system energies
    - step_2_count_s.py
        - For each atomic configuration (file_poscar) in the dataset, count the number of each cluster in the cluster pool (file_in) and
        - collect the system energy from the DFT calculation result (file_oszicar), 
    - Deliverable: the cluster information and the system energies (file_out)

3. Step_3_Select
    - Select key clusters using LASSO regression and k-fold CV analysis on the data sets of the systems and their energies
    - step_3_lasso_mix.py
        - Choose the number of fold (fold_pick)
        - Choose the LASSO regularization parameter (alpha_pick)
    - Deliverable: the selected clusters (file_cluster)

4. Step_4_Entropy
    - After generating random samples (step_1_sample.py, step_2_collect.py)
    - calculate configuration entropies (step_3_entropy.py) 

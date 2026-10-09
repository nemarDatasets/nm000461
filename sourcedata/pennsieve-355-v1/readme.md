
# Utility of iEEG networks in modeling brain activity depends on re-referencing and connectivity choice
Data for the manuscript titled *Utility of iEEG networks in modeling brain activity depends on re-referencing and connectivity choice.*

Data is separated into two centers: Hospital of the University of Pennsylvania (HUP) and Medical University of South Carolina (MUSC). Within each folder, `gw` is the set of networks that are used for all analysis and `LR` is the subset of networks used for the seizure onset zone lateralization analysis. Each file titled `patientList.mat` consists of a Matlab struct datatype where each row is a patient and each column represents one field of the metadata. Each mat file in the results folder contains the networks for each of the 24 preprocessing pipelines detailed in the manuscript, as well as masks for gray/white or left/right.


Note that the data in this repository is the functional connectivity networks, the raw EEG data is available on iEEG.org.
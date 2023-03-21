# DAS Microseismic Detection
Please review lisencing information in LICENSE.txt  \
\
Code to run through entire processing and prediction process of our DAS microseismic prediction ML workflow.

Written by Paige Given and Fantine Huot with Contributions from Ariel Lellouch, Bin Luo, Robert G. Clapp, Tamas Nemeth, Kurt Nihei, and Biondo L. Biondi

# To start singularity 
The singularity file has all of the dependencies needed to run this notebook. Download the .sif file from the singularity_download.txt file. 

To unzip, run (in terminal): gzip -d dasml.sif.gz

To start singularity, run (in terminal): singularity shell --nv dasml.sif

# To run notebook
The notebook is outlined in the following format:
1) Load dependencies
2) Check GPU devices connected (if applicable)
3) Set datapath and load data. Here change *datapath* and *input_file_pattern* to match desired filepath.
4) Pre-processing: includes \
**bp filter:** band-pass filters the data.\
**normalize:** normalizes data to standard deviation. \
**median:** remove median amplitude from data to reduce noise. \
**run prediction:** runs the model prediction on the data. \
**preprocess:** runs bandpass on data, reshapes to model input size, clips amplitude values, and converts to float 32 format. \
*Alter input parameters for pre-processing as needed* \
5) Load model and compile. Set datapath to *ckpt* filepath.
6) Run pre-processing and detection with sliding windows on data.
7) Convert logits to probabilities and visualize results. 

# Acknowledgements
We would like to thank Chevron Technical Center for the recorded data with which the model was trained.

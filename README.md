# seg_sta_nois

Tools for segmentation and feature extraction of Lossless derivative EEGIP London dataset.

Copy this 'seg_sta_nois' folder to the 'eegip/london/derivatives/lossless/derivatives' folder. 

Use EEGLAB with Matlab working directory set to:

eegip/london/derivatives/lossless

Add to the Matlab path:

addpath('code/dependencies/eeglab_asr_amica/');
addpath('derivatives/seg_sta_nois/code/scripts/');

Then start EEGLAB:

eeglab redraw


To run the segmentation use the batch_context EEGLAB extension to execute the "seg_sta_nois.htb" script (located in 'derivatives/seg_sta_nois/code/scripts') on the *.qcr.set files in the lossless derivatives directory.

Use the getERPfeatures script to extract measures for the resulting segmented files.

getERPfeatures(inlistfname,outfname);
... where 'inlistfname' is a text file containing input *eeg.set files (one per line including path) and 'outfname' is the name of the output file contain ing the feature table (the derivatives/seg_sta_nois/output path is recommended). 'inlistfname' files can be generated in bash (on Windows computers GitBash is recommended) with the folloing command executed from the 'lossless' directory:

find . -type f -name "*-SEG*.set" > derivatives/seg_face_noise/code/misc/fnames.txt

In this case, inorder to write the output to 'outfeatures.csv in the 'output' directory the specific call (from the lossless working directory in Matlab) would be:

getERPfeatures('derivatives/seg_face_noise/code/misc/fnames.txt','derivatives/seg_face_noise/output/outfeatures.csv'); 

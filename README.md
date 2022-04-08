# TEXture Analysis of CT and PET in NSLC cancer patients treated with Stereotactic body radiation therapy (TEXAS study)
The aim of this study is to analyze different models based on radiomic features to predict disease relapse from pre-SBRT imaging.
In this repository, you will find two different trained models (linear SVM and ensemble subspace discriminant) in MATLAB workspace format (.mat). The training has been performed on 76 patients from 3 different centres and the models have been validated on 41 patients from 4 other centres. The interested reader can find more details in Bertolini et al., Novel harmonization method for multi-centric radiomic studies in Non-Small Cell Lung Cancer (submitted. DOI will be provided upon publication).

How to use these models:
Needed platform: Matlab 2020a and higher on Windows.

Harmonization steps:
1) Lesion ROI (called GTV in the referenced work) needs to be shifted on the contralateral lung on the same axial level as the original ROI. This task can be performed by a radiologist or radiation oncologist to ensure that a correct shift is done. Please rename the GTV ROI as 'GTV CT' and the contralateral one as 'GTV CT C'. <u><b>These needs to be the only structures present in the exported RT-STRUCT set to be used in the next step.</b></u> If there are other structures present (OARs, or planning structures), please make a a copy of your clinical structure set and delete the others.
2) The user needs to create a set of folders needed for the software to correctly select the needed files. The CT images needs to be in the folder named '01_CT' and the structure set exported in step 1) needs to be moved in '01_CT_CONTRA'. This step needs to be repeated for every patient included in the analysis (each patient needs to have its own folder with the above described sub-folders). Please refer to the following figure for the folder paths and names. 

![SnipImage](https://user-images.githubusercontent.com/101640135/162413815-237905ea-899b-4493-a843-4a9e2c3c5a53.JPG)

3) Run the script " ". The user will need to select which folder contains the needed data (the software provides the needed information) and the output is a structure set saved in the folder '01_CONTRA_MOVED' and it contains the two ROIs exported in step 1) with the additional 12 shifts. It's possible to visualize the correct execution of the script by importing the new structure set in your TPS again.
4) Extract the radiomic features using the structure set generated in step 3). The radiomic features needed in the models are listed in the Supplementary Material of the above mentioned work.
5) Run the script " " which will perform the harmonization and give a .mat file with the harmonized features.
6) These features can be used with the model weights stored in " " and " " to perform the predictions.
7) Let us know your results!

We advise to use this model when dealing with NSCLC patients, as detailed in our article as other lung cancer diseases have not been tested or explored. We believe in trasparency and free science as our vision for this project, thus the sharing of our models' weights publicy. If you use it for validation in your patient cohort, please let us know (valeria.trojani@ausl.re.it) and cite the following article Bertolini et al., Novel harmonization method for multi-centric radiomic studies in Non-Small Cell Lung Cancer (submitted. DOI will be provided upon publication) in your work. Feedback, comments and questions are also welcome at the above address.

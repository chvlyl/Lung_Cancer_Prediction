# Lung Cancer Prediction

## Goal
Predict lung cancer based on CT images

## Data
1. Data Science Bowl 2017

The goal of this competition was to predict lung cancer wihtin one year based on the CT images. Data can be downloaded from [Kaggle](https://www.kaggle.com/c/data-science-bowl-2017). All images are in DICOM format, which can be visualized in 3DSlicer. This competition had two phases (stage1 and stage2). Total 471,537 images from 2,101 subjects were included in this dataset. The table below gives detailed numbers. 

<img align="center" height="60%" width="60%" margin="auto" alt="DSB data" src="https://github.com/chvlyl/Lung_Cancer_Prediction/blob/master/img/DSB_data_details.png">


Those images are high-resolution lung CT scans provided by the National Cancer Institute. The orignal paper was published in NEJM 2011 [Reduced Lung-Cancer Mortality with Low-Dose Computed Tomographic Screening](http://www.nejm.org/doi/full/10.1056/NEJMoa1102873). The goal of the original study was to use low-dose CT screening as a way to reduce lung cancer mortality. 

Note that this study had CT images from 26,722 subjects, which means the data science bowl data is only a subset of the orignal dataset. It's not clear to me that how the data science bowl data was selected from the original dataset. Note that the participants in the original study were old people (age between 55 and 74), had a smoking history. Since this was screening study, not all participants necessarily had lung nodules. 

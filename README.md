# Lung Cancer Prediction

## Goal
Predict lung cancer based on CT images

## Data
1\. Data Science Bowl 2017

The goal of this competition was to predict lung cancer wihtin one year based on the CT images. Data can be downloaded from [Kaggle](https://www.kaggle.com/c/data-science-bowl-2017). All images are in DICOM format, which can be visualized in 3DSlicer. This competition had two phases (stage1 and stage2). Total 471,537 images from 2,101 subjects were included in this dataset. The table below gives detailed numbers (I merged the label files from the two stages and generated the following summay tables. The merged label file is here: [Combined_Stage1_Stage2_Labels.csv](https://github.com/chvlyl/Lung_Cancer_Prediction/blob/master/0_Data/1_DSB2017/labels/Combined_Stage1_Stage2_Labels.csv)). 

<img align="center" height="50%" width="50%" margin="auto" alt="DSB data" src="https://github.com/chvlyl/Lung_Cancer_Prediction/blob/master/img/DSB_data_details.png">

Each subject has multiple CT images (also called slices). Each image slice is a 2D image. However, since each subjects has multiple slices, we can consider the image as 3D. Note that the number of slices is different across subjects. 

<img align="center" height="50%" width="50%" margin="auto" alt="DSB data" src="https://github.com/chvlyl/Lung_Cancer_Prediction/blob/master/img/DSB_data_details2.png">


Those images are high-resolution lung CT scans provided by the National Cancer Institute. The orignal paper was published in NEJM 2011 [Reduced Lung-Cancer Mortality with Low-Dose Computed Tomographic Screening](http://www.nejm.org/doi/full/10.1056/NEJMoa1102873). The goal of the original study was to use low-dose CT screening as a way to reduce lung cancer mortality. 

Note that this study had CT images from 26,722 subjects, which means the data science bowl data is only a subset of the orignal dataset. It's not clear to me that how the data science bowl data was selected from the original dataset. Note that the participants in the original study were old people (age between 55 and 74), had a smoking history. Since this was screening study, not all participants necessarily had lung nodules. 


## Load DICOM files
DICOM is the standard file format for medical images. The DICOM file not only contains the images but also the meta information about the images. There is a python package "dicom" can be used to load the DICOM format files. 
```python
dicom.read_file('image_file')
```
Note that in this dataset, each patient has multiple image slices (each image slice is a DICOM file) and the number of slices varies by patients. After reading in the DICOM file, use the ```ImagePositionPatient```,```SliceLocation``` or ```InstanceNumber``` attribute to access the order of each slice.


## Hounsfield Unit (HU)
In order to make the biomedical image comparable with different imaging acquisition parameters, the Hounsfield units (HU) are used. After normalization, the air and water have -1000 HU and 0 HU, respectively. Soft tissues have relatively small HU while bones have large HU.  

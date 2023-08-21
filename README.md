# Bluepoint Lung Ultrasound (BLUS) dataset

We provide a dataset obtained in a prospective study on COVID-19 patients, conducted between February and May 2021. The study included 63 patients (33 COVID-positive and 30 COVID-negative), with the inclusion criteria being symptoms of a lung infection. 

The dataset comprises lung ultrasound recordings at six blue points for each patient, a database of clinical variables, and severity assessment by medical experts. These parts are described more in detail in the following:

### Lung ultrasound videos

Our dataset contains a set of lung ultrasound videos that were recorded in a standardized setting. All recordings were conduced with a Philips Lumify US device with a convex probe. The videos show one position for 60 - 100 frames. In contrast to other ultrasound datasets, the US videos were taken according to the standard [BLUE protocol](https://annalsofintensivecare.springeropen.com/articles/10.1186/2110-5820-4-1) [1], where six points (three for each lung) are scanned. This leads to 6 videos per patient. Since some points could not be scanned for individual patients, there are sometimes less videos per patient, resulting in a total of 362 videos. The videos are labeled according to the following schema:

`patient_<PATIENT-ID>_<BLUEPOINT>`, e.g. `patient_1_L3.mp4`, where the blue points are denoted as L1, L2, L3 (left lung), R1, R2, R3 (right lung). 

All videos are available as `.mp4` files in the folder [lus_videos](lus_videos).

### Clinical variables

The file [clinical_variables.csv](clinical_variables.csv) contains medical information for each patient. This includes patient characteristics, symptoms, comorbidities, **blood test data**, vital parameters, and the **PCR test result** testing for COVID-19. An explanation for the variables and their respective unit is provided in file [variable_explanations.csv](variable_explanations.csv). 

### Severity assessment

Last, we asked two medical experts to rate the severity of the lung infection visible on the LUS videos. They were asked to follow the scoring algorithm by Soldati et al [2], with scores from 0-3:
* Score 0: The pleura line is continuous, regular. Horizontal artifacts (A-lines) are present.
* Score 1: The pleura line is indented. Below the indent, vertical areas of white are visible (B-Lines).
* Score 2: The pleura line is broken. Below the breaking point, small to large consolidated areas (darker areas) appear with associated areas of white below the consolidated area (White Lung/ B-Patches).
* Score 3: The scanned area shows dense and largely extended white lung with or without larger consolidations.

The medical experts further noted whether B-lines and / or A-lines are visible in the video.

The severity scores and B-line/A-line informaiton are provided *per video* in the file [severity.csv](severity.csv). 

### References
[1] Lichtenstein, Daniel A. "Lung ultrasound in the critically ill." Annals of intensive care 4.1 (2014): 1-12.
[2] Soldati, Gino, et al. "Proposal for international standardization of the use of lung ultrasound for patients with COVID‐19: a simple, quantitative, reproducible method." Journal of Ultrasound in Medicine 39.7 (2020): 1413-1419.


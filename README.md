# COVID Bluepoint Lung Ultrasound (BLUES) dataset

The **COVID-BLUES** dataset contains bluepoint-specific lung ultrasound videos recorded in a prospective study on COVID-19 suspects between February and May 2021. The study included 63 patients (33 COVID-positive and 30 COVID-negative), with the inclusion criteria being symptoms of a lung infection. 

The dataset comprises lung ultrasound recordings at six BLUE points for each patient, a database of clinical variables, and severity assessment by medical experts. These parts are described more in detail in the following:

### Lung ultrasound videos

<p align="center">
  <img src=https://github.com/NinaWie/COVID-BLUeS-dataset/blob/main/sample_video.gif alt="Sample LUS video">
</p>


Our dataset contains a set of lung ultrasound videos that were recorded in a standardized setting. All recordings were conduced with a Philips Lumify US device with a convex probe. The videos show one position for 60 - 100 frames. In contrast to other ultrasound datasets, the US videos were taken according to the standard BLUE protocol by [*Lichtenstein (2014)*](https://annalsofintensivecare.springeropen.com/articles/10.1186/2110-5820-4-1), where six points (three for each lung) are scanned. This leads to 6 videos per patient. Since some points could not be scanned for individual patients, there are sometimes less videos per patient, resulting in a total of 362 videos corresponding to 31,746 frames. The videos are labeled according to the schema `patient_<PATIENT-ID>_<BLUEPOINT>`, e.g. `patient_1_L3.mp4`, where the blue points are denoted as L1, L2, L3 (left lung), R1, R2, R3 (right lung). 
In some cases, two videos are available for the same blue point. These cases are labeled `patient_<PATIENT-ID>_<BLUEPOINT_2>`; see for example `patient_15_L2_2.mp4`.

All videos are available as `.mp4` files in the folder [lus_videos](lus_videos). 
*NOTE*: If you split videos into frames for your ML model, make sure to not mix frames from the same patient across training and testing data.

### Clinical variables

The file [clinical_variables.csv](clinical_variables.csv) contains medical information for each patient. This includes patient characteristics, symptoms, comorbidities, **blood test data**, vital parameters, and the **PCR test result** testing for COVID-19. An explanation for the variables and their respective unit is provided in file [variable_explanations.csv](variable_explanations.csv). 

### Severity assessment

Last, two medical experts rated the severity of the lung infection visible on the LUS videos. They were asked to follow the scoring scheme by [*Soldati et al, 2020*](https://onlinelibrary.wiley.com/doi/full/10.1002/jum.15285), with scores from 0-3.

The medical experts further noted whether B-lines and / or A-lines are visible in the video.
The severity scores and B-line/A-line informaiton are provided *per video* in the file [severity.csv](severity.csv). 

## License
The COVID-BLUES dataset is available via the **CC BY-NC-ND 4.0** [license](https://creativecommons.org/licenses/by-nc-nd/4.0/).

## Related dataset
If you are looking for more, similar data, have a look at the [POCUS dataset](https://github.com/jannisborn/covid19_ultrasound) which contains >200 videos collected from various public sources and divided in three categories (COVID-19, bacterial pneumonia, healthy).

## Attribution & Citation
The dataset was recorded by **Maastricht University Medical Center (UMC+)** in the Netherlands. 

If you use the COVID-BLUES dataset in your research, please cite the following:

(Citation follows)
```bib
```

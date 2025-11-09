# COVID Bluepoint Lung Ultrasound (BLUES) dataset

The **COVID-BLUES** dataset contains bluepoint-specific lung ultrasound videos recorded in a prospective study on COVID-19 suspects between February and May 2021. The study included 63 patients (33 COVID-positive and 30 COVID-negative), with the inclusion criteria being symptoms of a lung infection. The findings of the study and a description of the dataset have been published in [Wiedemann et al. (2025), *IEEE Journal of Biomedical and Health Informatics*](https://ieeexplore.ieee.org/abstract/document/10903196). Please [cite](#citation) that paper if you use this data. 

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


## Huggingface

The dataset is also available on Huggingface [here](https://huggingface.co/datasets/jannisborn/COVID-BLUES/tree/main).
Install requirements:
```bash
pip install datasets==3.5.0
pip install av
pip install torchvision
```
Access dataset with: 
```py
from datasets import load_dataset
dataset = load_dataset("jannisborn/COVID-BLUES", split="train")
# Select one video
dataset[0]["video"] # torchvision VideoReader

# Load clinical variables
variables = load_dataset("jannisborn/COVID-BLUES", data_files="clinical_variables.csv")["train"]
# Load severity scores
severity = load_dataset("jannisborn/COVID-BLUES", data_files="severity.csv")["train"]
```



## License
The COVID-BLUES dataset is available via the **CC BY-NC-ND 4.0** [license](https://creativecommons.org/licenses/by-nc-nd/4.0/).

## Related dataset
If you are looking for more, similar data, have a look at the [POCUS dataset](https://github.com/jannisborn/covid19_ultrasound) which contains >200 videos collected from various public sources and divided in three categories (COVID-19, bacterial pneumonia, healthy).

## Citation
The dataset was recorded by **Maastricht University Medical Center (UMC+)** in the Netherlands. 

If you use the COVID-BLUES dataset in your research, please cite the following:

```bib
@article{wiedemann2025covid,
  author={Wiedemann, Nina and Boer, Dianne de Korte-de and Richter, Matthias and van de Weijer, Sjors and Buhre, Charlotte and Eggert, Franz A. M. and Aarnoudse, Sophie and Grevendonk, Lotte and Röber, Steffen and Remie, Carlijn M.E. and Buhre, Wolfgang and Henry, Ronald and Born, Jannis},
  journal={IEEE Journal of Biomedical and Health Informatics}, 
  title={COVID-BLUeS - A Prospective Study on the Value of AI in Lung Ultrasound Analysis}, 
  year={2025},
  volume={29},
  number={9},
  pages={6301-6310},
  keywords={COVID-19;Artificial intelligence;Videos;Lungs;Ultrasonic imaging;Analytical models;Pathology;Medical diagnostic imaging;Data models;Training;Lung ultrasound;computer vision;COVID-19},
  doi={10.1109/JBHI.2025.3543686}
}
```

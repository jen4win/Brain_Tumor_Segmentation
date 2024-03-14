# Brain Tumor Segmentation

## Content
This repository centers around the Brain Tumor Segmentation Challenge 2020 (BraTS2020). 
Glioblastomas are frequent brain tumors and show very aggressive characteristics. The 5-year survival rate is limited to 5-7 %.
Due to a constant need for radiologists to diagnose tumors and other injuries but their limited availability, the need for a reliable model is huge.
The goal of this project was to deploy a model which is able to detect a brain tumor and to separate it into the different tumor areas necrotic core (non-active part of the tumor), enhancing part (active tumor) and edema (surrounding region with increased pressure, causing complications).

## Data
The data was taken from kaggle (https://www.kaggle.com/datasets/andrewmvd/brain-tumor-segmentation-in-mri-brats-2015/data). 
As the folders in this link combine three subsequent years of the same images, this project aimed to model the data of 2020.

## Models
During our project we created two models.
1. UNet from scratch
   This serves as our baseline model, which was trained on the patients of the BraTS2020 challenge after splitting them into training, validation and testing groups.
   When applying this model on the test patients we got a dice score of 60%.
    
2. Transfer Learning model with ResNet50 as a encoder backbone for the U-Net.
   This model is our advanced one, which has the pretrained encoder backbone of ResNet50. This is a model trained in the Imagenet Competition on more than 1.000 image classes. The decoder part of the U-Net was then responsible for finding the patterns in the MRI scans and giving the classification into the 4 segmentation classes as an     output. 

## Requirements
All the required packages are given in the file requirements.txt
For the successful deployment of the app an extra file named app_requirements.txt is added.

## Contributors
Eugenia Kirkunow
Pawel Biedunkiwicz
Somayyeh Nemati
Jennifer Winkler

## Set up the Environment
### **`macOS`** type the following commands : 



- For installing the virtual environment and the required package you can either follow the commands:

    ```BASH
    pyenv local 3.11.3
    python -m venv .venv
    source .venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt
    ```
Or ....
-  use the [Makefile](Makefile) and run `make setup` or install it manually with the following commands:

     ```BASH
    make setup
    ```
    After that active your environment by following commands:
    ```BASH
    source .venv/bin/activate
    ```

### **`WindowsOS`** type the following commands :

- Install the virtual environment and the required packages by following commands.

   For `PowerShell` CLI :

    ```PowerShell
    pyenv local 3.11.3
    python -m venv .venv
    .venv\Scripts\Activate.ps1
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

    For `Git-bash` CLI :
  
    ```BASH
    pyenv local 3.11.3
    python -m venv .venv
    source .venv/Scripts/activate
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

    **`Note:`**
    If you encounter an error when trying to run `pip install --upgrade pip`, try using the following command:
    ```Bash
    python.exe -m pip install --upgrade pip
    ```


   
## Usage

In order to train the model and store test data in the data folder and the model in models run:

**`Note`**: Make sure your environment is activated.

```bash
python example_files/train.py  
```

In order to test that predict works on a test set you created run:

```bash
python example_files/predict.py models/linear_regression_model.sav data/X_test.csv data/y_test.csv
```

## Limitations

Development libraries are part of the production environment, normally these would be separate as the production code should be as slim as possible.



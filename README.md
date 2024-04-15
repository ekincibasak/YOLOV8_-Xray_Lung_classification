# Annotated YOLO Results for Automatic Diagnosis of Lung Diseases

This repository contains the Jupyter Notebook, `annoted_yolo_results.ipynb`, showcasing the results of our research titled "Automatic Diagnosis of Lung Diseases Utilizing X-ray Images Enhanced with Deep Learning".

## Data Source

We utilized the [Roboflow](https://roboflow.com/) platform to annotate our dataset. The annotated data, combined with public datasets, is available on Kaggle at [Chest X-ray Masks and Labels](https://www.kaggle.com/datasets/nikhilpandey360/chest-xray-masks-and-labels).

## References

- [Roboflow](https://roboflow.com/)
- [Ultralytics Documentation](https://docs.ultralytics.com/tr)
## Unannotated Data and Results

In addition to the annotated data, we also experimented with unannotated lung images. We developed code to generate bounding boxes for all lung images and analyzed the results. Although the accuracy was not as high as with the annotated data, the results were still promising. Due to the lower accuracy, these results were not included in the published article, but they can be found in the `not_annotated_results.ipynb` notebook in this repository.


#YOLOv8 Dataset Structure for Lung Images
This section provides a detailed explanation of structuring your dataset for YOLOv8 training with lung images.

##Overview
When preparing a dataset for YOLOv8, organizing your data into a specific structure is crucial. This guide outlines the directory structure and steps to achieve this.

##Code Explanation:
Import Libraries
We begin by importing the necessary libraries:

os: Handles directory and file operations.
random: Used for shuffling the image files.
shutil: Enables file copying between directories.





import os
import random
import shutil
Directory Definitions
Define the following directories to manage your dataset:

input_directory: Contains the resized lung images.
output_directory: Stores the YOLO labels.
train_directory: For the training images and labels.
val_directory: For the validation images and labels.
test_directory: For the test images and labels.





input_directory = '/kaggle/working/resized_images'
output_directory = '/kaggle/working/yolo_labels'
train_directory = '/kaggle/working/train'
val_directory = '/kaggle/working/val'
test_directory = '/kaggle/working/test'
Directory Creation
Create the train, val, and test directories using os.makedirs().









os.makedirs(train_directory, exist_ok=True)
os.makedirs(val_directory, exist_ok=True)
os.makedirs(test_directory, exist_ok=True)
Data Split Percentages
Define the percentages for splitting the dataset into training, validation, and test sets.





train_percentage = 0.7
val_percentage = 0.15
test_percentage = 0.15
File List and Shuffling
Generate a list of image files in input_directory and shuffle them randomly.


image_files = [file for file in os.listdir(input_directory) if file.endswith('.png')]
random.shuffle(image_files)
Data Splitting
Copy the images and their corresponding labels to the respective train, val, or test directories based on the calculated splits.


train_split = int(train_percentage * len(image_files))
val_split = int((train_percentage + val_percentage) * len(image_files))
##Usage:
Replace input_directory with the path to your resized lung images.
Replace output_directory with the path to your YOLO labels.
Adjust the split percentages (train_percentage, val_percentage, test_percentage) as required.
Execute the code to organize your dataset into training, validation, and test sets.
##Conclusion
By adhering to this structure and following the provided steps, you can effectively organize your lung image dataset for YOLOv8 training, ensuring it's ready for use in your machine learning workflow.







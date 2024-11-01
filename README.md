# Master Thesis Code Repository

This repository includes the code developed for the Master's thesis project on detecting the influence of opinion leaders within limited social networks.

## Data to Reproduce Results

The data used for this analysis, including the cleaned input data, trained Doc2Vec model intermediate and final outputs, is available for download on Zenodo.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14020130.svg)](https://doi.org/10.5281/zenodo.14020130)
 
The original dataset used to execute the pipeline in the provided example is from:
Dornel, B. (2021). *New York Times Articles & Comments (2020), Version 1* [Data set]. Kaggle. Retrieved February 29, 2024, [https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020](https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020)

## Opinion Leader Detection Pipeline

The pipeline consists of seven individual notebooks located in the `Pipeline` folder, designed to be executed sequentially. Each notebook produces outputs that are used as inputs for subsequent notebooks.
 
## Processing Custom Data

If you wish to process your own dataset through this pipeline, the input dataset containing the comments should be structured as follows:

| Column Label     | Description                                                        |
|------------------|--------------------------------------------------------------------|
| **commentID**    | Unique ID of the comment                                           |
| **userID**       | Unique ID of the user who made the comment                         |
| **parentID**     | Unique ID of the parent comment (NA if the comment is not a reply) |
| **articleID**    | Unique ID of the article where the comment was posted              |
| **createDate**   | Date and time when the comment was created*                        |
| **approveDate**  | Date and time when the comment was visible to others*              |
| **commentBody**  | Text content of the comment                                        |

*If only one of the two dates is available, use it for both the createDate and approveDate columns.

## Requirements

This code has been developed and tested on a Windows 11 machine with the following specifications:
- **CPU**: i5-14600T
- **RAM**: 32 GB
- **GPU**: NVIDIA RTX 3060 with 12 GB VRAM (CUDA acceleration is not strictly necessary but speeds up the sentiment analysis process)
- **Storage**: ~100GB of free space (inkl. Memory paging)

In case of memory errors it is possible to reduce the batch-size in Notebook 3 while calculating the pairwise cosine similarity.

To run this code, you will need:
- Python >= 3.11
- Required packages (listed in [`requirements.txt`](./requirements.txt))

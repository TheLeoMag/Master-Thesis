# Master Thesis Code Repository

This repository contains the code developed for the Master's thesis project on detecting the influence of opinion leaders within limited social networks. This codebase includes a complete pipeline as well as the data to reproduce the reported results.

## Table of Contents
1. [Master's Thesis Document](#masters-thesis-document)
2. [Data for Reproducing Results](#data-for-reproducing-results)
3. [Opinion Leader Detection Pipeline](#opinion-leader-detection-pipeline)
4. [Using Custom Data](#using-custom-data)
5. [System Requirements](#system-requirements)
6. [Installation](#installation)


## 🚧Master's Thesis Document🚧

For a explanation of the methods and findings, please refer to the Master's thesis: [Thesis PDF](./path/to/your-thesis.pdf). *(Note: Link to be updated once the thesis is finalized)*

## Data for Reproducing Results

The data used for this analysis, including the cleaned input data, trained Doc2Vec models, and intermediate and final outputs, are available for download on Zenodo.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14020130.svg)](https://doi.org/10.5281/zenodo.14020130)

> **NYT Dataset**: The New York Times dataset used in this project is from:  
Dornel, B. (2021). *New York Times Articles & Comments (2020), Version 1* [Data set]. Kaggle. Retrieved February 29, 2024, from [https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020](https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020)

> **DST Dataset**: The Der Standard dataset used in this project is from:  
Schabus, D., Skowron, M., & Trapp, M. (2017, August). One million posts: A data set of German online discussions [Data set]. In Proceedings of the 40th International ACM SIGIR Conference on Research and Development in Information Retrieval (pp. 1241-1244). 

## Opinion Leader Detection Pipeline

The pipeline consists of seven individual notebooks located in the `Pipeline` folder, designed to be executed in sequence. Each notebook produces outputs that are used as inputs for the subsequent notebooks.


## Using Custom Data

The input dataset needs to be structured as follows:

| Column Label     | Description                                                        |
|------------------|--------------------------------------------------------------------|
| **commentID**    | Unique ID of the comment                                           |
| **userID**       | Unique ID of the user who made the comment                         |
| **parentID**     | Unique ID of the parent comment (NA if the comment is not a reply) |
| **articleID**    | Unique ID of the article where the comment was posted              |
| **createDate**   | Date and time when the comment was created                         |
| **approveDate**  | Date and time when the comment was visible to others               |
| **commentBody**  | Text content of the comment                                        |

> *Note*: If only one of the two dates is available, use it for both the `createDate` and `approveDate` columns.

## System Requirements

This code was developed and tested on a Windows 11 machine with the following specifications:
- **CPU**: i5-14600T
- **RAM**: 32 GB
- **GPU**: NVIDIA RTX 3060 with 12 GB VRAM (CUDA acceleration is not strictly necessary but speeds up the sentiment analysis process)
- **Storage**: Approximately 100GB of free space (including memory paging)

In case of memory errors, it may be necessary to reduce the batch size in Notebook 3 during the pairwise cosine similarity calculation.

## Installation

To run the pipeline code, you will need:
- Python >= 3.11
- Required packages (listed in [`requirements.txt`](./requirements.txt))

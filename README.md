# Master Thesis Code Repository

This repository contains the code used in my Master's thesis on detecting the influence of opinion leaders in limited social networks. This codebase provides a full opininon detection pipline, with all files necessary to replicate my findings. 

## Project Structure

The repository is organized as follows:

- **Pipeline**: Each jupyter-notebook in the directory should be run in the provided sequence for the pipeline to function correctly. 
- **Data** 🚧: Contains the trained model files as well as all supporting files created during the pipeline processing. All files in this folder should be placed directly in the project directory for the code to work without path modifications. *(TO DO)*
- **Testing** 🚧: Contains the Jupyter notebooks used to test the hypotheses presented in the Master's thesis. *(TO DO)*
- 
The original dataset used to execute the pipeline in the provided example is from:
Dornel, B. (2021). *New York Times Articles & Comments (2020), Version 1* [Data set]. Kaggle. Retrieved February 29, 2024, from [https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020](https://www.kaggle.com/datasets/benjaminawd/new-york-times-articles-comments-2020)

## Execution Guide

To run the pipeline, follow these steps in sequence:

1. **0_Data_exploration_Comments.ipynb** - Initial data exploration and preprocessing.
2. **1_Sentiment_Orientation.ipynb** - Analyze sentiment orientation of comments.
3. **2_Comment_embeddings.ipynb** - Generate comment embeddings for similarity analysis.
4. **3_Constructing_link_structure.ipynb** - Construct link structures between comments.
5. **4_Network_Modeling.ipynb** - Model the network based on comment links.
6. **5_User_Vectors.ipynb** - Calculate user vectors based on network properties.
7. **6_Clustering.ipynb** - Perform clustering to identify user groups.

Run each notebook in the order provided for the pipeline to execute correctly.

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
- **GPU**: NVIDIA RTX 3060 with 12 GB VRAM
- **Storage**: ~100GB of free space (inkl. Memory paging)

In case of memmory errors it is pissible to reduce the batch-size in Notebook 3 while calculating the pairwise_cosine similarity.

To run this code, you will need:
- Python >= 3.11
- Required packages (listed in [`requirements.txt`](./requirements.txt))

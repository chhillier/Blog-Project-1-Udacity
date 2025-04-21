# Roman Era Pottery Classification Dataset

## Introduction

##### This is a project for the Udacity Nano degree program. It is the first project in the course. We chose from a variety of datasets and I picked this particular dataset. It involves classifying a great number of groups within the features. I typically use continuous variables and response variables so this was a good lesson with the oneshot encoders and trying to figure out what to do with so many different pottery groups.

#### The ReadMe will be further broken down into the requirements file. Why particular packages were used. Importing the dataset and figuring out what to do with the data. Exploring it and making several pipelines from the data to see what the outcomes were.

## Requirements

#### Use [pip install -r requirements.txt] no brackets to install all the packages from the requirements file. It includes the dependency files as well and the versions. I will highlight the main packages here :

+ Pandas - Used for data filtering and importing. Describes the data
+ Matplotlib and Seaborn - Used for making the cross tabs
+ Sklearn : .preprocessing, .pipeline, .compose  - Used to transform the data and easily reproduce those transformations
+ Sklearn : .ensemble, .linear_model - Used to model the data
+ Sklearn.metrics - Used to accurately score the model's performance

## Importing Data

#### Note here that the delimiter is a semicolon ; and not a comma. Also note that the lat long need switched if you try to make up a scenario and you pick a spot in Germany and it doesn't work. If you use lat long as features make note of that. I did not because I felt it would introduce data leakage into my response, although I feel this dataset is easy to get a good score on.

## Exploring Data

#### Crosstabs shows feature relationships with the response. If you wanted to go further you could look at the within features crosstabs and look for relationships there. Remove either X or Y or the lat long because they contain the same data. Instead of doing the top 7 most relics dug up you could do top 15 or top 20. I'd also assume the sites feature spills over the answer to the response as well, but there are so few features we can't just use one. Although, I did do PCA and only one feature was needed to explain 99% of the variance in the model.

## Preprocessing and Modeling

#### Split the data with train_test_split feeding in the response using the label encoder. All transformations were done on the training set and then applied to the test set. Picked two different Logistic regression models and a random forest model. Used a default logistic regression model for a baseline, then used a weighted model to make up for the imbalanced dataset. Training and testing scores revealed a slight overfit, but all models performed well enough. Since all models performed similarly, I went with the base model. No need for additional computing.

## Scenario

#### Picked Dressel 20 because it had the most chance of picking the wrong location, also used the site with the least relics recovered to make it harder for the model to predict. Went with the higher of the two codes for Italia. Tried different areas in Britania as well, although it isn't in the notebook cells. It gets them correct every time, I assume data is still leaking into the response as mentioned before.

## Conclusion

#### Hardest part of the project was the EDA. Figuring out how to split this thing without losing a bunch of data was the most time consuming part. I feel a lot of the features give away the answer whether by using the lat long, site, or even code. Example if an Italian code was carved into the pottery it will most likely be close to its origin, Italy. There will be outliers of course but in this case it generally gives the answer.

## Data Source

The `stamps.csv` dataset used in this analysis originates from the research published in the following paper:

* Rubio-Campillo, X., Montanier,, J.M., Rull, G., Bermúdez Lorenzo, J.M., Moros Díaz, J., Pérez González, J., Remesal Rodríguez, J. (2018) *The ecology of Roman trade. Reconstructing provincial connectivity with similarity measures*, Journal of Archaeological Science, 92, pp. 37-47. doi:[10.1016/j.jas.2018.02.010](https://doi.org/10.1016/j.jas.2018.02.010)

**To obtain the data:**

* **Option 1 (Preferred):** Check the journal article page (via the DOI link above) for supplementary materials or links to an official data repository associated with the publication.
* **Option 2 (Where Found):** If an official source isn't readily available, the dataset was located within this GitHub repository: (https://github.com/xrubio/ecologyStamps.git)

Please download the `stamps.csv` file from the appropriate source and place it in the `ecologyStamps/data/` directory within this project folder to run the analysis notebook/script.


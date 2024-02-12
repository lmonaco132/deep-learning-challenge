## Overview

The purpose of this analysis is to create a model which can predict the success of ventures, to help Alphabet Soup determine where to assign its funding. The model will use neurel nets with multiple hidden layers, predicting target which is binary representing if a venture was successful or not, with input features that have other information about the venture such as the amount of funding requested, the type of organization, and what the funding will be used for. <br>

The target for this model is:
* IS_SUCCESSFUL, a binary variable which represents if a venture was successful or not

The features for this model are:
* APPLICATION_TYPE, the type of application as defined by Alphabet Soup
* CLASSIFICATION, government classification of the organization
* USE_CASE, the use for the funding
* ORGANIZATION, organization classification
* STATUS, active status
* INCOME_AMT, classification of the amount of income the org has
* SPECIAL_CONSIDERATIONS, a binary representing if the venture has special considerations
* ASK_AMT, the amount of funding requested

The features removed from the dataset are:
* NAME, the name of the organization
* EIN, an identification number


## Results

### Data Pre-Processing
The variables NAME and EIN were removed before the model was trained, as unique identifiers are not useful for training data. The APPLICATION_TYPE and CLASSIFICATION variables were changed slightly such that the values which had very few instances were binned together in a newly created "other" category, which ensures that our model has enough data for all of the categorical values. The numerical variables were also scaled using Standard Scaler, so that any difference in range of the values would not negatively impact the training of the model.

### Compiling, Training, Evaluating the model
I used 2 hidden layers, with 10 nodes in the first hidden layer, and 7 nodes in the second hidden layer. This is because adding more hidden layers and more neurons increases the accuracy of the model, but at the cost of processing power and time. Two hidden layers is a good sweet spot, where increasing further requires more time than is reasonable for model training.
I was not able to achieve target model performance, falling just slightly short of 75% accuracy with my model's accuracy of 73%. Possible ways to increase this accuracy may include increasing the number of nodes available to the model, which has the trade-off of requiring more computational resources.
To potentially increase model performance, I tested the model with the organization column removed, as it seemed to me to be less relevant to the success of a venture than the other features. However, the model created from this data had slightly lower accuracy (72%), so I used the original data for the next attempt. I then tried increasing the number of nodes available in the hidden layers, which also failed to meaningfully increase the accuracy of the model. Finally, I increase the number of epochs to 150, but this still failed to increase the accuracy. Ultimately the accuracy of all these (similar) models remained at about 73%, just shy of the target 75%.

## Summary
In summary, I trained a neural network model on the data from Alphabet Soup with the goal of creating a model which could predict the success of ventures for funding. The model fell short of target accuracy, which is why I would ultimately not recommend using this model. A different model which could solve this classification & prediction problem is a logistic regression model, which works very well for the purpose of classification and prediction, and is well-suited to the structure of this data, with many features of different types (some numerical, others categorical) with a binary response.
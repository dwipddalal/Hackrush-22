# Hackrush-22

## Stanford or Standard?

 We worked on developing ML algorithms to predict the future enrolment of students in a university based on historical data. Every training instance comprised of the course name, the year it was offered and the name of the Professor offereing the course. 


## From data extraction all the way to model selection

|Feature | Unique Values|
|--------|--------------|
|Courses| 656|
|Time Steps | 177 |
| Faculty | 560 |


### Lets explore the features ### 
The data provided demanded us to extract the features in the most efficient and relevant manner. We extracted the year of offering of a course from the timestep and normalized it.  To extract the information of the courses we used a novel and ingenious method. We used label binarizer to create 656 different columns for every Course. Label Binarizer essentially marked the presence of a course corresponding to it's column(new feature) for every training example. We repeated this for the Faculty feature. Essentially we now had 1+656+560 features. We also observed through confusion matrix that the amount of enrolment was depended heavily on the time (linearly), moderately on courses and faculty. Therefoer we increased the weight given to timestep. Final feature size: 5+656+560+5.


### Lets look at the train set size ###
Initially we trained on the entire dataset. 
1. We observed huge overfitting of the data to the train set. The enrolments of the initial years were too less when compared to the ones 200 years later, present in the test set. The train set had majority of data from initial years. This caused fractured performance on the test data. 
2. We also concluded that the dataset provided was much larger than the efficient size. Therefore, we trained the model on nearly 4,000 data samples with timesteps from latter years that optimized the model performance.  
3. Our list of expanded features allowed us to train on smaller data samples size.


### That's fine, but, which model do we choose??

Well, this readme has already been over worked upon. Let's keep this short. 
We worked our way around every possible approach, from state of the art Transformers to the cliche Linear Regression. 
We observed that we received great results with approaches using ensembling. The idea was to use Linear Regression and XGD Regressor(they gave best results) and generate multiple models using soft voting on these two models. We developed multiple such models thorugh soft voting and then applied ensembled learing on the prediction of these generated models to get the final predictions. A dense neural network was trained to predict the final results. 

An intersting thing to observe is that most of the Deep Learning approaches involving Transformers, LSTMs couldn't match the results achieved with the above approach. This, very possible, could be due to them overfitting the data, especially the predictions based on earlier time steps.


### That's it!!

A team of four budding friends with a universal passion for Machine Learning worked their way through solving this problem, consuming loads of free pizza and caffine for 48 hours straight, all worth the first position!

Please find the Kaggle Competition here.  [here](https://www.kaggle.com/competitions/hackrush22-ml-challenge)


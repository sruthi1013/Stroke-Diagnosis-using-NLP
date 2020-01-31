# Project 3: Classification of Reddit posts

## Problem Statement

Strokes are occurring more commonly than ever, and there is a lack of awareness in the world about stroke symptoms Many late diagnoses happen and some are even misdiagnosed because symptoms are similar to that of a migraine

The goal of this project is to predict if someone has a stroke based on their post in a discussion forum, using a model which has been trained using data from subreddits "r/stroke" and "r/migraine". The prediction model tries to find the most important words which distinguish between stroke and migraine, and use those words to make a diagnosis.


## Contents:

1. Data Collection
2. Data Cleaning
3. Exploratory Data Analysis
4. Natural Language Processing
5. Modeling
6. Analysis of Bag of Words
7. Conclusions
8. Recommendations
9. Next Steps

## Models Summary

| Model                        	| Logistic Regression                   	| Logistic Regression                             	| MN Naive Bayes  	| MN Naive Bayes            	| Random Forests    	| Random Foresrs            	|
|------------------------------	|---------------------------------------	|-------------------------------------------------	|-----------------	|---------------------------	|-------------------	|---------------------------	|
| Metric                       	| Recall                                	| Recall                                          	| Recall          	| Recall                    	| Recall            	| Recall                    	|
| Features                     	| Title and posts                       	| Title, posts and comments                       	| Title and posts 	| Title, posts and comments 	| Title and posts   	| Title, posts and comments 	|
| Vectorizer                   	| Count                                 	| Count                                           	| TFIDF           	| Count                     	| TFIDF             	| TFIDF                     	|
| Cross Validation Score       	| 0.67                                  	| 0.77                                            	| 0.92            	| 0.93                      	| 0.47              	| 0.76                      	|
| Training Score               	| 0.72                                  	| 0.83                                            	| 0.94            	| 0.94                      	| 0.53              	| 1.0                       	|
| Testing Score                	| 0.70                                  	| 0.82                                            	| 0.91            	| 0.95                      	| 0.54              	| 0.81                      	|
| Important features- Stroke   	| Worst,Nausea,Extreme,Visual,Caffeine  	| Bleed,Sensation,Success,Older,Strange           	|                 	|                           	|                   	|                           	|
| Important features- Migraine 	| Medicine,Typical,Memory,Vomit,Year    	| Aspirin,Sumatriptan,Vertigo,Progress,Mouth,Induce 	|                 	|                           	|                   	|                           	|
| Model fit                    	| Overfit                               	| Slightly overfit                                	| Overfit         	| Slightly underfit         	| Slightly underfit 	| Extremely overfit         	|


## CONCLUSIONS
1. The number of posts taken from r/stroke is 980, and from r/migraine is 4239. But, the average number of words per observation is 654 and 383 for r/stroke and r/migraine respectively, which balances the number of features contributed from each of the subreddits.
2. Sentiment analysis didn't reveal any significant differences in sentiment between the two subreddits, and was measured as mostly neutral.
3. After testing roughly 17,000 models using Grid Search on Logistic Regression, Random Forests, Naive Bayes, Count Vectorizer and TFIDF Vectorizer, 6 best models were trained with the whole dataset.
4. The Porter Stemmer was used on all the models, since it worked the best with our particular data and models.
4. Models whose had titles+posts+comments received slightly more scores than those which had only titles+posts. This means that comments added value to the classification, and didn't have noise.
5. Multinomial Naive Bayes model had the best sensitivity score of 0.95, and Logistic regression had 0.82.
6. The distribution of probabilities for Naive Bayes is spread more in the middle, whereas the distribution for Logistic Regression is more concentrated on both ends, which means that eventhough Naive Bayes had a better score, Logistic Regression predicted the values with more certainity, which would ensure its good performance on a new dataset.


## RECOMMENDATIONS
1. The Logostic Regression model can be used to predict if anyone is having a stroke based on their post in 'r/DiagnoseMe' subreddit, or a similar discussion forum.
2. A similar model can be used to classify migraines and strokes using medical journals. This model can then be used on clinical notes at a hospital as an initial screening for the prediction of stroke.


## NEXT STEPS
1. Test with Support Vector Machines and KNN models.
2. Further analyse the features and add more stop words.
3. Write a program to continually monitor the posts in 'r/DiagnoseMe' and automatically post replies/comments to posts which are predicted as strokes, suggesting they see a doctor as soon as possible.




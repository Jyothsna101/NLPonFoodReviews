# NLP on AmazonFineFoodReviews

## Dataset: Amazon Fine Food Reviews

## About Dataset: The reviews of exquisite meals from Amazon make up this dataset. All 500,000 reviews up to October 2012 are included in the statistics, which cover a period of more than ten years. Reviews include information about the product and the user, ratings, and a plain text review. Reviews from all other Amazon categories are also included.

## Contents: 

  1. Reviews.csv: Pulled from the corresponding SQLite table named Reviews in database.sqlite
  2. database.sqlite: Contains the table 'Reviews'
  
## Data Includes: 

    Reviews from Oct 1999 - Oct 2012
    568,454 reviews
    256,059 users
    74,258 products
    260 users with > 50 reviews
    
## Data Exploration:

<img width="229" alt="Screen Shot 2022-07-15 at 11 33 26 AM" src="https://user-images.githubusercontent.com/52540495/179256839-d0e77895-ccba-4e0f-9a4d-872ec7250983.png">

## DataCleaning:

The dataset has ten variables, of which five are numerical and 568454 observations. Each observation contains a ProductID, UserID, Profile Name, Score, Summary, and Text. The distinctive identifiers for products and users, respectively, are ProductID and UserID. The total number of users who stated whether they found the review to be useful or not is known as the Helpfulness Denominator. At the same time, the Helpfulness Numerator represents the total number of users who felt the study to be helpful. The rating provided ranges from 1 to 5. The frequency of score 5 is the highest, as seen here, and the other scores are all at the same level. The first 1500 observations would be filtered out and designated as the training set if their scores are shown in below image.

<img width="398" alt="image" src="https://user-images.githubusercontent.com/52540495/178850727-7b6e77bc-2f14-4482-b8ff-556c0771689d.png">

Preparing the data is the first and most crucial step in subject modeling. To do this, we will remove all nouns from the reviews and then develop topic models using the LDA approach utilizing only nouns. Then we can all the standard familiar English stop words from the nltk package. After looking for the words that occur the most frequently, we additionally add our own stop words. Doing so would make the text smaller, and the training would take less time. The text is then lemmatized to reveal a word's base word. Call lemma is the word's root. Doing this would remove all word derivatives, leaving only the base term. We finally removed all numbers from the text as part of the data cleaning process. We now have a dataset ready for topic modeling, as shown below.

<img width="468" alt="image" src="https://user-images.githubusercontent.com/52540495/178850763-e415f985-7d5b-461f-97a0-5fbf642f388d.png">

## Analysis: 

Following text cleaning, we created a bag of words containing the words and their corresponding frequencies using a count vectorizer. There are 3744 words total, and the frequency table is shown below to give us an idea. 

<img width="468" alt="image" src="https://user-images.githubusercontent.com/52540495/178850837-f7050a12-c3a8-4b9c-84b3-435cf9c54529.png">

We now develop an LDA model to cluster the data into 10ten distinct segments and generalize it to various themes. 
The following model parameters were used for the LDA: 

  1.	Total topics: 10 
  2.	There have been ten iterations. 

When performing topic modeling, the ideal situation is to reduce the complexity of the model, and the intra- and inter-cluster distances should be minimized and maximized, respectively. According to the experiments, subjects with ten topics produced the least ambiguity and the most significant inter-cluster space. 

We have the following based on the LDA algorithm's clusters: 

<img width="830" alt="Screen Shot 2022-07-15 at 11 17 27 AM" src="https://user-images.githubusercontent.com/52540495/179253742-5a2fc4fc-0307-4be9-bd3c-c6f63f6efc01.png">

We would determine the LDA model's complexity and evaluate its effectiveness. A probability model's complexity is a statistical indicator of how effectively it can forecast a sample. You estimate the LDA model when applied to LDA for a particular value of k. Compare your documents' real topic mixes or word distribution to the theoretical word distributions provided by the topics. This model's perplexity is estimated to be 1058.6359087208268. 

## Conclusion:  

To analyze the text for "Amazon Fine Food Reviews" and pinpoint the most critical and significant terms to comprehend the general perception of the public about the fine foods from Amazon. First, we cleaned up the data by pulling out the nouns and removing stop words, derivate words, and numerals. After that, we produced ten topics and the LDA model to put topic modeling techniques into practice. We looked at all the topics' keywords and concluded that the reviews left by consumers are mostly about cookies and chocolates and drinks like tea, coffee, juice, and soup. 

# Analysis Overview

In this analysis I've been given the task of analyzing Amazon reviews written by members of a paid service called Amazon Vine. Amazon vine is a program that allows publishers to receive reviews for their products. I was able to choose from several provided datasets for this project, and I chose a dataset which contains musical instrument reviews. Using Pyspark and working with a Google Collab notebook, I first extracted the dataset, transformed it and and connected it to a RDS instance through AWS. I connected this instance to PGADMIN (Postgres) and analyzed the reviews using Pyspark. I compared data for both paid and unpaid members of the Amazon Vine service, as was able to come up with a few conclusions based off of this data.


*Screenshot of dataset*
![mod_16_2](https://user-images.githubusercontent.com/100390727/175826426-7877b1e9-d660-446b-affb-fe27feac87c6.png)


# Results

## How Many Vine Reviews and non-Vine reviews were there?
* In order to complete this task I first had to extract my dataframe using Pyspark dependencies and methods on my Google Collab notebook. I created a dataframe called "paid_reviews_total" to find the number of paid (vine) reviews in our original dataframe. I then used the "count()" method to get this number, which is 60. 
* Similarily, I created another dataframe called "unpaid_total" and used the same "count()" method to find the number of unpaid (non-Vine) reviews. The number of non-Vine reviews is 14477, which is a significanly higher number than what I got for the paid reviews (60).

## How Many Vine Reviews were 5 stars? How Many non-Vine reviews were 5 stars?
* To find this information, I began with first creating another dataframe called "paid_five_star." I filtered my previous dataframe on the "star_rating" column to find all values equal to 5, and then I ran the "count()" method once again. The number of paid five star reviews is 34.
* Another dataframe was created to find the amount of 5 star reviews by non-vine users. I called this dataframe "unpaid_five_star" and once again filtered my previous unpaid dataframe by the "star_rating" column where every value is equal to 5. The number of non-Vine reviews there were 5 stars is 8212. It's not surprising that there are more non-Vine reviews with 5 stars than Vine reviews with 5 stars, because as observed above, we have a significanly higher total number of non-Vine reviews in our dataset.

## What Percentage of Vine Reviews were 5 stars? What Percentage of non-Vine reviews were 5 stars?
* To find the percentages of 5 star reviews for Vine vs non-Vine, I began by creating another new dataframe called "paid_five_star_pcnt." This dataframe divides the amount of paid five star reviews by the total of paid reviews, and then multiples this value by 100 to give us a percent. The percentage of Vine reviews that were 5 stars is 56.67%.
* To find the percentage of non-Vine reviews, I did exactly what I did above except that I divided the amount of unpaid five star reviews by the total numer of unpaid reviews and multiplied this by 100. The percentage of non-Vine reviews that were 5 stars is 56.72%

*Screenshot of lines of code to answer questions above*
![mod16_1](https://user-images.githubusercontent.com/100390727/175826483-b3451786-83c6-4b7d-be7e-b79eb7c04b9f.png)

# Summary
All in all, it appears that the number of Vine reviews in this dataset are lacking. There is a significanly higher number of reviews written by non-Vine reviewers, which tells me that perhaps there should be an effort by the vine service to recruit more users so there is a more fair comparison between reviews that are paid and those that are unpaid. It's worth noting the similarity in the percentage of 5 star reviews for users vs. non-users, with the difference being .05%. More than half of reviews written by paid users are 5 stars, and the same can be said of unpaid users. Another analysis that could be performed here would be to look at the number of reviews that are 1 star, ie. the number of negative reviews that are being submitted by both Vine users and regular users. This correlation could give us more info about both types of reviewers and perhaps we could draw more conclusions about the Vine service.


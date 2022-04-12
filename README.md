# Amazon_Vine_Analysis

## Overview of Project

### Purpose

The Amazon Vine program allows manufacturers to pay a fee and provide products to Amazon Vine members in exchange for reviews.  The purpose of this project is to determine if there is a favorable bias in those Vine reviews. 

### Deliverables
 
 - Perform ETL on Amazon Product Reviews
 - Determine Bias of Amazon Vine Reviews
 - Written Report of Analysis

### Resources
 - Data Sources: [Amazon Review datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt), [Amazon Baby Reviews dataset](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Baby_v1_00.tsv.gz
) 
 - Technology: AWS RDS, AWS S3, PySpark, pgAdmin, Google Colab

### Overview of Code

Code for Deliverable 1, ETL on Amazon Reviews, was written in Google Colab with PySpark.  Amazon data was first loaded to a Spark DataFrame, then transformed to match [schema](https://github.com/aberloro/Amazon_Vine_Analysis/blob/main/challenge_schema.sql) set up for pdAdmin, and finally written to the RDS instance. See [Amazon_Reviews_ETL](https://github.com/aberloro/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb). 

Code for Deliverable 2, Bias of Amazon Vine Reviews, was also written in Google Colab with PySpark.  After data was loaded and converted to a spark dataframe, it was transformed to keep relevant columns, filtered, and analyzed to calculate the percentage of vine vs non-vine reviews. See [Vine_Review_Analysis](https://github.com/aberloro/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb).

## Results
 
### A Look At Vine (paid) Reviews

![vine_analysis](https://user-images.githubusercontent.com/93740725/162853331-21f9a39b-6530-4ce1-be9d-41165b7d28fb.png)

From the screen grab above, we see that there were a total of 463 paid Vine reviews, 43.63% or 202 of which were 5-Stars.  


### A Look at Non-Vine (unpaid) Reviews

![non_vine_analysis](https://user-images.githubusercontent.com/93740725/162853352-176a5203-bb35-4ff1-8a6a-320a8f77cc51.png)

From the screen grab above, we see that there were 25,094 unpaid reviews, 47.95% or 12,033 of which were 5-Stars.

### Paid vs Unpaid 
 - There were significantly more unpaid reviews than paid Vine reviews: 25k unpaid to 463 paid.
 - There were significantly more unpaid 5-Star reviews than paid 5-Star reviews: 12k unpaid to 202 paid 5-Star reviews.
 - There were fewer 5-star reviews per-capita for the paid-vine group than the unpaid group: 43.63% paid to 47.95% unpaid 5-star reviews.  


## Summary 

Looking strictly at the percentages of 5-star reviews in each group, paid and unpaid, there does not appear to be a favorable bias for purchasing reviews: the paid group shows a *smaller* percentage of 5-star reviews than the unpaid group.  

Additional analysis is needed to make better conclusions.  A two- population t-Test should be executed to see if there is a difference in the mean distribution of ratings between paid and unpaid reviews. 

Also, this is just one of many Amazon product datasets.  The same analysis should be run on other product categories to see if the current observations are consistent in other datasets as well. 



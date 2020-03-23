+++
author = "Hervé Choi"
date = 2020-03-23T23:00:00Z
description = "Photo by Marcos Luiz Photograph on Unsplash"
image = "/images/marcos-luiz-photograph-R6xx6fnvPT8-unsplash.jpg"
image_webp = ""
title = "Capstone Progress"

+++
We just had our Capstone final in-class presentation today. The sky is a bit bluer now, even in rainy Vancouver.

I have been looking at lung cancer tumour features in CT images and try to correspond them with survival outcomes of the patients. Before I was trying to build classification models to predict whether the patient can survive past 1 year, 3 years and 5 years. The accuracy score has been lacklustre for all the models.

Then a while ago we had a data scientist from Lululemon came and talked to us. He used k-means clustering to group the customers and try to see what are some common characteristics of the customers. Then the epiphany hit me: maybe I could do the same!

So I went back and did the clustering. I looked at the elbow plot and debated between 4 or 5 clusters. Then I thought 5 clusters were probably a bit too much to present, so I went to have 4.

Then when I plotted the survival curves (those Kaplan-Meier plots from my medical physics days), two of the four were practically right on top of each other. Maybe I had to scale it down to 3.

And 3 it was. Then there was a gap between the bands around Cluster 0 and Cluster 1, indicating there is a statistically significant difference between them. Yes!

It turned out the survival probabilities at the 1-year and 3-year marks were significantly different in the statistical sense. 5-year was not - I am guessing it is because of the low number of patients surviving that long.

Then I looked at the features that had the greatest statistical significance in the differences of their distributions for the two clusters. Surprisingly, the top 5 were not volume-related features, but uniformity- or coarseness-related.

Someone then suggested I should introduce the cluster as an additional feature in the original model. I did not want to redo my entire analysis because that would be too time-consuming. I just re-ran the decision tree for 1-year.

Nothing. No change. The accuracy score with the test data actually got worse (must be because there were over-fitting with the training set).

Maybe it was because both clusters have median survival times of greater than 1 year? Maybe the cluster information could not help the 1-year classification problem?

Okay, so I tried again for the 3-year classification problem. Again, nothing.

At that point, I just went to bed. All the other models performed more or less the same, so I should not waste my time redoing the rest.

Now I need to focus on which features are clinically useful. If a feature changes drastically for a patient that gets rescanned after 10 minutes, maybe I should throw it out of my model. That will be more work, which is great.
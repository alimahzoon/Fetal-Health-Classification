## Fetal-Health-Classification

Provided by: Ali Mahzoon

---
### Problem
Reduction of child mortality is reflected in several of the United Nations' Sustainable Development Goals and is a key indicator of human progress.
The UN expects that by 2030, countries end preventable deaths of newborns and children under 5 years of age, with all countries aiming to reduce under‑5 mortality to at least as low as 25 per 1,000 live births.

Parallel to notion of child mortality is of course maternal mortality, which accounts for 295 000 deaths during and following pregnancy and childbirth (as of 2017). The vast majority of these deaths (94%) occurred in low-resource settings, and most could have been prevented.

In light of what was mentioned above, Cardiotocograms (CTGs) are a simple and cost accessible option to assess fetal health, allowing healthcare professionals to take action in order to prevent child and maternal mortality. The equipment itself works by sending ultrasound pulses and reading its response, thus shedding light on fetal heart rate (FHR), fetal movements, uterine contractions and more.

---
### Questions:
1. Which supervised learning model works best and why?
2. What are the most important evaluation metrics and why?
3. What features impact the model the most?

----
### Dataset and Approach
* Dataset and Tools:
   * Given data by Automated Analysis of Cardiotocograms
   * Scikit learn library
   * Supervised learning algorithms


* Approach:
  * Create a multiclass model to classify CTG features into the three fetal health states.
    1.  Normal
    2.  Suspect
    3.  Pathological

  * Model selected based on high evaluation metrics of baseline models.
  * GridSearch used to improve the model
  * Data visualized by Seaborn and Matplotlib

  ---
### Findings
By doing a simple exploration on my data, it is easily understandable that my data is highly imbalanced. As we can see in the following image 77.8 percent of the data is classified as Normal, 13.9 percent as Suspect, and 8.3 percent as Pathological.

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/pie.png "Pre EDA")

There are 484 Pair plots available in the EDA, which show the relationship between each pair features in the dataset. For instance, in the following image we can see 3 pair plots in three different situations. In other words, the left pair plot shows the relationship between mean_value_of_short_term_variability and percentage_of_time_with_abnormal_long_term_variability, as we can see in this case our classes (Normal, Suspect, Pathological) are separable. The middle pair plot is more useful to separate Pathological (green points) from Normal (gray points). The right pair plot is barely useful because the separation of data by combination of these two features (histogram_max and histogram_number_of_peaks) is highly unlikely due to the closeness of data points (located on top of each other).

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/pairplot.png "Pair Plot")

I used 10 different  supervised learning algorithms to find the best model for this dataset. My top two algorithms are Hist Gradient Boosting and Gradient Boosting. My best evaluation metrics for train and test set are as follows:

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/classreport.png "Classification Report")

And features that matter the most are:

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/featureimportance.png "Feature Importances")

histogram mean is the most important feature because as we can see data is more separable.

* majority of the suspected points are around 140 and greater that 140
* majority of the normal points are around 140 and less than 140
* and majority of the pathological points are around 100 and less than 100

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/impfeature.png "Post EDA")

And my least important feature is severe_decelerations

![Image](https://github.com/alimahzoon/Fetal-Health-Classification/blob/main/Images/lessimpfeature.png "Post EDA")




---
### Conclusion
As we saw in our models the most important features to classify fetal health are the ones with different densities in different points. Another important point to consider is that features with variances close to zero are not useful either to learn from or for prediction.

---

### Recommendations
This dataset is based on fetal heart rate. Although there is a misunderstanding among people that says long term abnormality is dangerous for child and maternal  health, short term abnormality must take into consideration for both baby and mother to reduce mortality among them.

---
### Citation
Ayres de Campos et al. (2000) SisPorto 2.0 A Program for Automated Analysis of Cardiotocograms. J Matern Fetal Med 5:311-318 (<a href="https://onlinelibrary.wiley.com/doi/10.1002/1520-6661(200009/10)9:5%3C311::AID-MFM12%3E3.0.CO;2-9" target="_top">link</a>)

# Android Malware Detection System Using Machine Learning

> ## Purpose:
Project at [IIITD](https://www.iiitd.ac.in/)
under the course [CSE343 : Machine Learning](http://techtree.iiitd.edu.in/viewDescription/filename?=ECE363 "Course Description") under the guidance of Professor [Anubha Gupta](https://www.iiitd.ac.in/anubha "Profile")

> ## Contributors:
- [Bijendar Prasad](https://Findcoding "GitHub Profile")

> ## Motivation:

As the android market continues to expand, so does the prevalence of malicious apps. According to [ZDNet](https://www.zdnet.com/article/play-store-identified-as-main-distribution-vector-for-most-android-malware), as many as 10%-24% of apps available on the Play store could be malicious in nature. These apps may appear innocuous at first glance, but they can wreak havoc on a user’s system in a variety of harmful ways. Unfortunately, current methods for detecting malware are both resource-intensive and exhaustive, and they struggle to keep up with the rapid pace at which new malware is being developed.

**What can help us to overcome these challenges ?**
- Developing a comprehensive strategy to assess and analyze data from confirmed malicious applications.
- Creating a model that can accurately predict the presence of malicious applications based on their permissions.
- Introducing a machine learning-based malware detection model that utilizes publicly available metadata information. This model will be evaluated to determine its effectiveness as a first-stage filter for detecting Android malware.


> ## Introduction:

Despite the growing threat of malware, there is still no reliable and robust method for detecting malicious applications. However,
with the increasing use of machine learning in various fields, we believe that this issue can be addressed through the application
of machine learning techniques. Our project aims to conduct a thorough and systematic investigation into the use of machine
learning for malware detection, with the ultimate goal of developing an efficient ML model capable of accurately classifying
apps as either **benign (0)** or **malware (1)** based on their requested permissions. 
This study Proposes:
- Conducting an in-depth examination and evaluation of Android metadata and permissions as predictors of malware.
- Introducing a machine learning-based malware detection strategy that utilizes publicly available metadata information.
- Analyzing the effectiveness of this model and assessing its potential as a first-stage filter for detecting Android malware.



> ## Dataset Description:
- Dataset has been taken from [kaggle](https://www.kaggle.com/saurabhshahane/android-permission-dataset/) 
- Data contains the details of the permission of almost 30k app
- There are 183 features in the dataset like Dangerous Permissions Count, Default : Access DRM content, Default : Move application resource, etc.
- There is one target class (binary- 0/1) named - ‘Class’, indicating Benign(0) and Malware(1) applications.
- There are 29,999 records with 20,000 malwares and 9,999 benign apps.

**Prerocessing, Visualization and Analysis:**
The data is first imported from a CSV file and loaded into a dataframe for ease of
use. The necessary attributes are then extracted from the dataset. To gain a better understanding of the data, several plots are
generated. The data is checked for null or missing values, and any such values are replaced with the mean of the corresponding
column. The distribution of malware and benign applications across various settings is then analyzed, and the results are
visualized through a series of plots created using **Matplotlib** and **Seaborn**.


> ## Plots:

<div float="left">
<img src="Plots\3.png" width=250 alt="Unsampled Class Distribution" hspace="10">
<img src="Plots\5.png" width=250  alt="Undersampled Class Distribution" hspace="10">
<img src="Plots\4.png" width=250  alt="Oversampled Class Distribution" hspace="10">
</div>
<br>
<div float="left">
<img src="Plots\2.png" width=700 alt="Columns Name vs Missing Values" hspace="10">
</div>

<br>

> ## Exploratory Data Analysis(EDA):
The EDA for the Android Permission Dataset provided valuable insights into the relationships between different features in the
dataset and helped us identify the most important features for predicting the app rating. It also provided a foundation for further
analysis using machine learning techniques.
<div float="left">
<img src="Plots\e1.png" width=350 alt="" hspace="10">
<img src="Plots\e2.png" width=350  alt="" hspace="10">
</div>
<br>
<div float="left">
<img src="Plots\e3.png" width=250 alt="" hspace="10">
<img src="Plots\e5.png" width=250  alt="" hspace="10">
<img src="Plots\e4.png" width=250  alt="" hspace="10">
</div>

> ## Methodology:

After preprocessing the data, it is split into testing and training sets at an **8:2 ratio**. We attempted both under and oversampling
techniques on the dataset, but the results were not promising. We then applied various classifiers, including logistic regression,
decision trees, and Naive Bayes, but the outcomes were unsatisfactory. Upon further inspection of the dataset, we discovered
that it contained several multivariate data tables, which required us to apply **PCA** to each dataset. We plotted the variance
percentage after using PCA and chose to use the inverse transform. We then applied Random Forest to the dataset, which
resulted in a significant improvement in accuracy. We then used the boosting approach to further increase prediction accuracy,
both on an unsampled dataset and on one with reliable features selected. The results showed that the model was improving.
Finally, we applied **SVM** and **MLP** to the final dataset and achieved our best results. When comparing the results obtained after
feature selection and **boosting**, we can see that we have made significant progress and achieved our final accuracy.

<br>

<img src="Plots\p2.png" alt="PCA features vs Variance Percentage" width=800>
<br>
<img src="Plots\o1.png" alt="" width=800>
<br>
<img src="Plots\o2.png" alt="" width=800>

> ## Libraries Used:
- [Numpy](https://numpy.org/)
- [Pandas](https://pandas.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- [Seaboran](https://seaborn.pydata.org/)
- [Scikit-Learn](https://scikit-learn.org/)
- [Imblearn](https://imbalanced-learn.org/stable/)
- [Xgboost](https://xgboost.ai/)

> ## Results and Analysis:

### On Basic Models

| Models| Unsampled | Oversampled | Undersampled |
| --- | --- | --- | --- |
| **Logistic** | Training Accuracy 0.69<br>Test Accuracy 0.68<br>Recall Score 0.95<br>ROC Score 0.53 | Training Accuracy 0.63<br>Test Accuracy 0.62<br>Recall Score 0.66<br>ROC Score 0.61 | Training Accuracy 0.63<br>Test Accuracy 0.63<br>Recall Score 0.67<br>ROC Score 0.62 |
| **Naive** | Training Accuracy 0.68<br>Test Accuracy 0.67<br>Recall Score 0.97<br>ROC Score 0.52 | Training Accuracy 0.53<br>Test Accuracy 0.53<br>Recall Score 0.98<br>ROC Score 0.51 | Training Accuracy 0.53<br>Test Accuracy 0.53<br>Recall Score 0.99<br>ROC Score 0.50 |
| **Decision Tree** | Training Accuracy 0.67<br>Test Accuracy 0.67<br>Recall Score 0.99<br>ROC Score 0.51 | Training Accuracy 0.57<br>Test Accuracy 0.55<br>Recall Score 0.68<br>ROC Score 0.54 | Training Accuracy 0.55<br>Test Accuracy 0.56<br>Recall Score 0.79<br>ROC Score 0.55 |

*As we can see that sampling is not effective in our case so move forward with unsampled data only.*


| Models | Optimal Parameter | Accuracy  | Recall | ROC |
| --- | --- | --- | --- | --- |
| **SVM** | default | Training Accuracy 0.85<br>Test Accuracy 0.85 | 0.94 | 0.80 |
| **Random Forest** | n_estimators=200, n_jobs = -1 | Training Accuracy 0.87<br>Test Accuracy 0.86 | 0.93 | 0.81 |
| **MLP** | random_state = 42, max_iter = 300 | Training Accuracy 0.85<br>Test Accuracy 0.85 | 0.95 | 0.80 |

By looking at the result all the three models performs more or less the same with Random Forest  with Accuracy of 86%. As we seen in the Tabulation that, Accuracy follows the order as follow: **Random Forest > MLP > SVM**

> ## Conclusion:

- Learning
Different ways to visualize the data for better understanding of features. Machine Learning models like Logistic Regression, Naive Bayes and Decision Tree to model the problem. How to use platforms like Kaggle and Google Colab. How to work and collaborate in teams.

> ## References:

- [[1](https://www.ijrdet.com/files/Volume11Issue2/IJRDET_0222_03.pdf)] Android Malware Prediction using Machine Learning Techniques: A Review

- [[2](https://www.sciencedirect.com/science/article/pii/S1877050921014186)] An Efficient Android Malware Prediction Using Ensemble Machine Learning Algorithms

- [[3](https://www.kaggle.com/saurabhshahane/android-permission-dataset/)] Android Permission Dataset


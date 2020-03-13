# MachineLearningGradProject

This repo hosts my graduate capstone project for Data Science 100 at UC Berkeley, partnered with Illan Halpern. We built an image classifier from scratch using tailored methods (exploratory data analysis, feature selection, training and regularizing models, etc), and with two neural nets: LeNet trained locally and ResNet18 trained with transfer learning.

# Task and Method

The task for this project was to develop an image classifier from scratch. We were given 1500 sample images, split into training and testing sets (80-20), such as the one below:

![Example image file](sample_image.png) 

Using scikit-learn, we extracted features, such as the Histogram-of-Gradients (HOG):

![Example image feature](sample_image_HOG.png)

We then analyzed how well these features distinguished among categories. For instance, the maximum of the HOG matrix and the average saturation both distinguished categories well: 

![Average saturation](features/avg_sat.png) ![Maximum of HOG](features/max_hog.png)

while our fancier attempts to develop cross-correlations within color channels, such as the correlation function of the green and blue channels, did not:

![Green-Blue correlation](features/gb_corr.png)

# Model selection

Once we had a sufficiently large feature matrix, we fitted to a variety of models in scikit-learn. In particular, we fit LogisticRegression, K-NearestNeighbors, RandomForest and SVM classifiers, which each had their strengths -- except for LogisticRegression, which performed worse when evaluated on the test set. In both plots below, the dashed line is random guessing.

![LogisticRegression](model_performance/logreg.png) ![SVM](model_performance/SVM.png)

In all, this tailored approach reached roughly 40% prediction accuracy on the test set.

# Neural networks

Finally, we implemented two neural networks in order to improve this performance. We began by implementing LeNet, a relatively simple early architecture designed to work on the MNIST handwritten digits dataset:

![LeNet Architecture](LeNet.jpg) \[LeCun et al, 1998\]

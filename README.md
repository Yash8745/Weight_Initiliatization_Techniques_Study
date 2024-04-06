
Comparing Different Weight Initialization techniques in a Neural Network.

**Introduction:**

In recent years there have been many techniques to initialize the weights in a neural network. The way these weights are initialized play a huge role in how these parameters are learnt and weather the model will converge to an optimal solution or not. Tees techniques varies from the most basic like zero initialization or constant initiation to complex techniques’ default TensorFlow uses TensorFlow Weight Initialization Techniques.

**Dataset**

The dataset used for this assignment was the iris dataset provided by the sklearn datasets library.

iris = load\_iris()

It contains sample of 150 iris flowers across 3 species namely setose versicolor and virginica

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.001.png)

I contain 4 features that are flower sepal length sepal width petal length and petal width which are use to predict the 3 species denotes by numbers 0,1,2 for setose and virginica respectively

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.002.png)



**Weight Initialization Techniques**

1\.   Zeros:

All weights are set to zero. Not commonly used in practice as it leads to symmetry problems. Neurons with the same weights will always have the same gradients during backpropagation.

2\.   Ones:

All weights are initialized to one. Similar to zeros, it's not widely used due to symmetry issues.

3\.   Random Normal:

Weights are initialized using random values drawn from a normal distribution (Gaussian distribution) with mean 0 and a specified standard deviation.

4\.   Random Uniform:

Weights are initialized using random values drawn from a uniform distribution between a specified range. 

5\.   Truncated Normal:

Similar to random normal, but values that exceed a certain threshold (usually two standard deviations) are discarded and redrawn. Helps prevent large weight values that might slow down training.

6\.   Glorot Normal (Xavier Normal):

Specifically designed for sigmoid and hyperbolic tangent (tanh) activation functions.

Weights are initialized from a normal distribution with mean 0 and variance calculated based on the number of input and output units.

Addresses the vanishing/exploding gradient problem for these activation functions.

7\.   Glorot Uniform (Xavier Uniform):

Similar to Glorot Normal but using a uniform distribution. Suitable when the weights need to be bounded.

8\.   He Normal:

Designed for rectified linear unit (ReLU) activation functions. Weights are initialized from a normal distribution with mean 0 and variance adjusted based on the number of input units. Addresses the issue of dying ReLUs where neurons become inactive during training.

9\.   He Uniform:

Similar to He Normal but using a uniform distribution.

**Implementation**
1\. Data Visualization

First step was to visualize the data and check how the data is spread across the 4 features. For that I plotted the graph for petal length vs the petal width (fig 1) and the graph for sepal length vs sepal width (fig 2)

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.003.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.004.png)

Fig 1                                                                                                         Fig 2

2\. Preprocessing

We split the data into Test Train and Validation set using the ratio 16:4:5

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.005.png)

The values of the test set were encoded in 0,1 and 2 so I encoded it using one hot encoding into a vector of shape [1,3]

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.006.png)

3\. Model

Test initializer’s function was created that contain the model the is compiled and fit using the training and validation data. The contain 3 fully connected dense layer with 2 hidden layer and 1 output layer, first and the second layer containing 64 neurons and output layer contain 3 neurons

Model is evaluated on accuracy to test between different the different weight initialization techniques

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.007.png)

4\. Results Visualization

Validation and train loss is recorded and their graph is plotted to check for overfitting

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.008.png)

A bar graph is also created to compare the accuracies

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.009.png)

**RESULTS**

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.010.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.011.png)

With zero weight initialization the model was overfitted on the training data and didn’t perform well on the validation set. Initialization with all ones lead to reaching a local minimum where loss was reduced but didn’t show accuracy while testing on test set

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.012.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.013.png)

Random weight Initialization was little bit better than zeros and ones initialization and was very consistent through the training phrase

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.014.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.015.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.016.png)![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.017.png)

![](Aspose.Words.4e47be18-5c3a-4933-b1f4-218c6868f771.018.png)

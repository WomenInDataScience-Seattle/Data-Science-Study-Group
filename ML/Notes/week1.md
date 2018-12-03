# Definitions 

## Machine Learning (Supervised Learning and Unsupervised Learning)

  - Arthur Samuel described it as: "the field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.
  - Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

## Supervised Learning 
  - In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.
  - Supervised learning problems are categorized into "regression" and "classification" problems. 
    - **Regression** predict results within a continuous output
    - **Classification** predict results in a discrete output. In other words, we are trying to map input variables into discrete categories. 
   

## Unsupervised Learning
  - Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.
  - Derive the structure by clustering the data based on relationships among the variables in the data.
  - No feedback based on the prediction results.
    - Eg, organize computing clusters, social network analysis, market segmentation, astronomical data analysis, the "[Cocktail Party Algorithm](https://en.wikipedia.org/wiki/Cocktail_party_effect)"

## Cost Funcation and Model

- Training set (input, feature) is represented as x(<sup>i</sup>). Output is represented as y(<sup>i</sup>). i=1,...,m, which is an index ti the training set. 
- To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X → Y so that h(x) is a “good” predictor for the corresponding value of y. 

- [Cost function](https://www.coursera.org/learn/machine-learning/supplement/u3qF5/cost-function-intuition-i): We can measure the accuracy of our hypothesis function by using a cost function. This takes an average difference (actually a fancier version of an average) of all the results of the hypothesis with inputs from x's and the actual output y's.
  - Linear regression: Squared error function (Mean squared error, MSE)
  - In linear regression, finding the global minimun of J(theta) corresponds to find the best slope of the fit.  

## Gradient Descent (GD)

Gradient descent is an optimization algorithm used to minimize some function by iteratively moving in the direction of steepest descent as defined by the negative of the gradient. In machine learning, we use gradient descent to update the parameters of our model. Parameters refer to coefficients in Linear Regression and weights in neural networks.
  - Learning rate (what if it is too small, too large or fixed?)
  - Simultaneously update thetas
  - Batch gradient descent. "Batch" means each step of GD uses all training samples.
  - Convex function, i.e., bowl shape function, only has global minimun (no local minima), which is the cost function used in the **linear regression**.
  

 
Reference: https://ml-cheatsheet.readthedocs.io/en/latest/gradient_descent.html
https://www.coursera.org/learn/machine-learning/supplement/2GnUg/gradient-descent


 ## Linear Algebra
 
 https://www.coursera.org/learn/machine-learning/supplement/xRMqw/lecture-slides
 
 
# Softwares 

  - Python will be used for this study group.
Optional:
  - Octave 
  - matlab
    
   
# Resources 

**Coursera**
  - [Forum](https://www.coursera.org/learn/machine-learning/discussions/weeks)
  - [Discussion board](https://www.coursera.org/learn/machine-learning/discussions)
  - [Meet and greet](https://www.coursera.org/learn/machine-learning/discussions/forums/FsTdcb2TEeS_cyIACw-CIA?page=1&sort=lastActivityAtDesc)
  - Slides are attached at the end of each session

**Dataset and projects**
[Kaggle](https://www.kaggle.com)
[UCI ML Dataset](http://archive.ics.uci.edu/ml/index.php)
[Amazon Transcribe – Automatic Speech Recognition](https://aws.amazon.com/transcribe/)
[Tensorflow-for-Poets](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#5) 

**Blogs**
https://machinelearningmastery.com/blog/
https://towardsdatascience.com/
https://www.kdnuggets.com/
https://www.dataquest.io/blog/
https://dataskeptic.com/

**Vedios**
[Caltech course](https://work.caltech.edu/telecourse.html)
[CS109-Harvard](http://cs109.github.io/2015/pages/videos.html)
[DataCamp](https://www.datacamp.com/)
[YouTube](https://www.youtube.com/user/kaggledotcom/playlists)

**Textbook and materials**
[Textbook](https://web.stanford.edu/~hastie/Papers/ESLII.pdf)
[Cheatsheet](https://stanford.edu/~shervine/teaching/cs-229/cheatsheet-supervised-learning)

**Conferences and events**
[Applied Advanced Analytics with R](http://www.cvent.com/events/applied-advanced-analytics-with-r-feb-28-mar-1-2019/event-summary-37ae6734473a4c079aabbb6506b22bdf.aspx)
[Conference of Statistical Practice](https://ww2.amstat.org/meetings/csp/2019/index.cfm)


  

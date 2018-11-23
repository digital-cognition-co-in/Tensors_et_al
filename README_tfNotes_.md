### Own Learning Notes / Video Transcript == Tensorflow and deep learning - without a PhD by Martin Görner

### YouTube Link -1 [GoogleCloudYouTube](https://www.youtube.com/watch?v=vq2nnJ4g6N0)
### YouTube Link -2 [GoogleCloudYouTube](https://www.youtube.com/watch?v=vq2nnJ4g6N0)

#
Flattened vector of All Pixels from 1 Image == 28X28 == 784 Pixels 

10 Neurons 

- A neuron does a WEIGHTED Sum of ALL of its INPUTS , which are the PIXELS 
- It adds another CONSTANT - Bias.
- Bias == Constant . An additional degree of freedom 
- Neuron will then FEED this SUM through an ACTIVATION Function. 
- We will see several of those ACTIVATION Functions , the one thing they have common in case of Neural Networks is that they are ALL NON LINEAR.
- Why only 10 NEURONS - as we have TEN CATEGORIES of DIGITS = 0-9
- One of the NEURONS will LIGHT UP and thus have recognized a DIGIT.
- As its a CLASSIFICATION Problem - we use SOFTMAX - activation function.

- SOFTMAX - activation function -- is an EXPONENTIAL NORMALISED .Make all the WEIGHTED SUMS -- elevate that to the EXPONENTIAL
- Once we have TEN EXPONENTIALs --- Compute the NORM of this VECTOR and DIVIDE it with its NORM. 
- Get VALUES between 0 and 1 -- these VALUES are to be INTERPRETED as PROBABILITY.
- WHICH -- NORM --- Any Normalization Function --- Usually for SOFTAMX we use -- L1 or L2 [EUCLIDIAN DISTANCE] will do as well.
- Softmax is a EXPONENTIAL -- it will pull the data apart - increase the DIFFRENCES .
- When we divide the complete VECTOR -- ONE Value will be CLOSE to 1 and all the other VALUES being very CLOSE to ZERO.

#
Y = tf.nn.softmax(tf.matmul(X,W)+b)

#

tensor shapes == X[100,784] , W[784,10] , b[10]
#
- We train the NEURAL NET to deduce the WEIGHTS and BIASES on its own. 
- When we TRAIN the - nn - initialize WEIGHTS and BIASES to soem RANDOM Values ?? [ WHAT RANDOM - within what RANGE etc ??]
- One HOT ENCODING Values - 0-9 . The VECTOR of ACTUAL PROBABILITIES. This is ONE HOT ENCODED with the 1 at the INDEX of the DESIRED CATEGORY or NUMBER. 
- The Other VECTOR is the VECTOR of PREDICTED / COMPUTED-  PROBABILITIES . 
- Now we need to CALCULATE the DISTANCE between these two VECTORS. 
- Euclidian distance would also do but the best for a CLASSIFICATION problem is the -- CROSS ENTROPY . 
- CROSS ENTROPY is SUM across the VECTORS of Values on top NUMBERS Above - 0-9. Multiplied (Dot product) of the LOG of the VALUES Below. 
- As all the VALUES on the BOTTOM are less than 1 . All the LOG VALUES  shall be negative , thus the returned value has been given a NEGATIVE sign. 
- We need the SYSTEM to PREDICT Values as close as possible to the ACTUAL PROBABILITIES. Thus we will guide the system through thwe TRAINING phase to MINIMIZE this Distance and this is thus called the ERROR Function. 

### Matplotlib Graphs 
#
- Accuracy - % of correctly classifed images
- Weights - Minus 1 to Plus 1 
- Biases - Minus 2 to Plus 2

### Tensorflow Code

tf.Variable --- variables of TF are values we are wanting TF to compute for us. 
#
tf.placeholder --- a placeholder for the images
#

```
import tensorflow as tf 
X = tf.placeholder(tf.float32,[None,28,28,1]
# 1 for the GRAY CHANNEL 
# 3 for the RGB
# None for Image Batch Size 
# 28 , 28 - Shape of Image Pixels

W = tf.variable(tf.zeros([784,10]))
b = tf.Variable(tf.zeros([10]))

init = tf.initialize_all_variables()
```
Training the model in TF terms means computing the VARIBALES == Weights and Biases. 
#
#### the TF Model - represents One layer of the Neural net
#

```
Y = tf.nn.softmax(tf.matmul(tf.reshape(X,[-1,784]),W)+b)

# tf.reshape - will flatten the IMAGE pixels into one big VECTOR - all the pixels in one line.
# tf.matmul - for MATRIX Multiplication of X and W.

Y_ = tf.placeholder(tf.float32,[None,10])

# placeholder for the GROUND TRUTH - known labels of the IMAGES - Values == 0-9
# None - will be passed in as a PARAM ?
# the - 10 - is One Hot Encoded ? How ? 

# The LOSS FUNCTION or the ERROR FUNCTION 

cross_entropy = -tf.reduce_sum(Y_ * tf.log(Y))

# tf.reduce_sum = sum accross the VECTOR. 
# Multiplication of known LABELS == Y_ , with log of PREDICTED LABELS == Y.

```













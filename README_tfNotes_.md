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
- The Python Class of the Weights Variable is ```# <class 'tensorflow.python.ops.variables.Variable'>``` . If we were to Print() the Weights variable in the terminal - we get to see ```<tf.Variable 'Variable_1:0' shape=(784, 10) dtype=float32_ref> ```. We dont see a ARRAY of any sort ?? Why ??

- When we TRAIN the - nn - initialize WEIGHTS and BIASES to soem RANDOM Values ?? [ WHAT RANDOM - within what RANGE etc ??]
- One HOT ENCODING Values - 0-9 . The VECTOR of ACTUAL PROBABILITIES. This is ONE HOT ENCODED with the 1 at the INDEX of the DESIRED CATEGORY or NUMBER. 
- The Other VECTOR is the VECTOR of PREDICTED / COMPUTED-  PROBABILITIES . 
- Now we need to CALCULATE the DISTANCE between these two VECTORS. 
- Euclidian distance would also do but the best for a CLASSIFICATION problem is the - CROSS ENTROPY. 
- CROSS ENTROPY is SUM across the VECTORS of Values on top NUMBERS Above - 0-9. Multiplied (Dot product) of the LOG of the VALUES Below. 
- As all the VALUES on the BOTTOM are less than 1 . All the LOG VALUES  shall be negative , thus the returned value has been given a NEGATIVE sign. 
- We need the SYSTEM to PREDICT Values as close as possible to the ACTUAL PROBABILITIES. Thus we will guide the system through thwe TRAINING phase to MINIMIZE this Distance and this is thus called the LOSS / ERROR Function. 

### Matplotlib Graphs 
#
- Accuracy - % of correctly classifed images
- Weights - Minus 1 to Plus 1 
- Biases - Minus 2 to Plus 2

### Tensorflow Code
#
tf.Variable - variables of TF are values we are wanting TF to compute for us. 
#
tf.placeholder - a placeholder for the images
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
#
#### Own Notes - and queries with regards TF Code 
#

```
# input X: 28x28 grayscale images, the first dimension (None) will index the images in the mini-batch
X = tf.placeholder(tf.float32, [None, 28, 28, 1])
# correct answers will go here
Y_ = tf.placeholder(tf.float32, [None, 10])
# weights W[784, 10]   784=28*28
W = tf.Variable(tf.zeros([784, 10]))


"""
The weights being passed in as INITIAL Weights
"""

weights_1 = tf.Variable(tf.zeros([784, 10]))
print("The weights being passed in as INITIAL Weights ---->>",type(weights_1))
# <class 'tensorflow.python.ops.variables.Variable'>
print("The weights being passed in as INITIAL Weights ---->>",weights_1)

"""
The Python Class of the Weights Variable is ```# <class 'tensorflow.python.ops.variables.Variable'>``` . 
If we were to Print() the Weights variable in the 
terminal - we get to see ```<tf.Variable 'Variable_1:0' shape=(784, 10) dtype=float32_ref> ```. 
We dont see a ARRAY of any sort ?? Why ??
"""


# biases b[10]
b = tf.Variable(tf.zeros([10]))


```

#### GradientDescentOptimizer - one of the many available optimizers

#
```
optimizer = tf.train.GradientDescentOptimizer(0.003) # Learning rate == 0.003
train_step = optimizer.minimize(cross_entropy) # our Loss Function 

# % of correct classifications - found in batch

is_correct = tf.equal(tf.argmax(Y,1)tf.argmax(Y_,1)) ## One Hot Decoding == tf.argmax


# accuracy of classification 

accuracy = tf.reduce_mean(tf.cast(is_correct,tf.float32))

```
#
#### Its called - Gradient descent , as we Follow in the Direction pointed by the Gradient and Descent. 
#
- Gradient descent - we are in the space of weights and biases...
- The Gradient points us downwards as its got a Negative Sign ...
- We take a little step - downwards into the direction pointed by the Gradient...
- Step means we MODIFY the Weights and Biases by a DELTA - so that we achieve a smaller LOSS or ERROR...
- This is the basic TRAINING - whenever we pass in a New Batch of Training Images - we repeat this process and everytime reduce the ERROR or LOSS Function.
 
#
- TF has a deffered execution model.
- When we execute the functions we dont return VALUES - we return an In-memory COMPUTATION GRAPH.
- TF needs to know the full graph to do a Formal Derivation ?? Thus in place of providing values a COMPUTATION GRAPH is provided to TF.
- TF is built for Distributed Computing thus a COMPUTATION GRAPH. To distribute a GRAPH over multiple machines TF needs to know what the COMPUTATION GRAPH is. 
- Due to this deffered approach - to get VALUES the user needs to go through another loop. We need to define a TF session and extract values from the sessions computation. ```sess.run(init)``` , will give actual values.
- Define a Session with - ```tf.session()```. Then call this session at one EDGE of the GRAPH  
- Feed the Placeholders , created earlier with actual data - training Images and training Labels.  Using the Dictionary - ```train_data{X:batch_X,Y_:batch_Y}```

#### Five Fully Connected Layers
#

- First layer will compute Weighted Sums of the Pixels.
- Next layer will compute Weighted Sums of the Inputs from First Layer.
- We keep SOFTMAX as the OutPut layer - for other layers use SIGMOID , the most basic classical continous function that goes from - 0 to 1.
- With Five Layers - we have a set of weights and biases for each layer.

#

#### RELU better than SIGMOID

#

- We use RELU as its better than SIGMOID - why ? 
- ``` Y = tf.nn.relu(tf.matmul(X,W)+b)``` - RELU returns - Zero for all negative values and One (Identity) for all positive values.
- Start Fast and then Slow Down - Learning rate decay on an exponential curve.
- Compared to the SIGMOID - RELU gives Higher Accuracy to begin with. The RELU Accuracy curve has a STEEP Rise and then flattens at @ 85% Accuracy.

#### Overfitting 

#
- Overfitting 
- DropOut - basis probability remove a certain % of Neurons during training - and again get them back in the network to run on TEST data. 
- TF dropout function , ``` Y = tf.nn.dropout(Yf,pkeep) ```.

#

- 


#












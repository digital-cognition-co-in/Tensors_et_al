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
We will see several of those ACTIVATION Functions , the one thing they have common in case of Neural Networks is that they are ALL NON LINEAR.
Why only 10 NEURONS - as we have TEN CATEGORIES of DIGITS = 0-9
One of the NEURONS will LIGHT UP and thus have recognized a DIGIT.
As its a CLASSIFICATION Problem - we use SOFTMAX - activation function.

SOFTMAX - activation function -- is an EXPONENTIAL NORMALISED .
make all the WEIGHTED SUMS -- elevate that to the EXPONENTIAL
Once we have TEN EXPONENTIALs --- Compute the NORM of this VECTOR and DIVIDE it with its NORM. 
Get VALUES between 0 and 1 -- these VALUES are to be INTERPRETED as PROBABILITY.
WHICH -- NORM --- Any Normalization Function --- Usually for SOFTAMX we use -- L1 or L2 [EUCLIDIAN DISTANCE] will do as well.
Softmax is a EXPONENTIAL -- it will pull the data apart - increase the DIFFRENCES .
When we divide the complete VECTOR -- ONE Value will be CLOSE to 1 and all the other VALUES being very CLOSE to ZERO.

#
Y = tf.nn.softmax(tf.matmul(X,W)+b)

#

tensor shapes == X[100,784] , W[784,10] , b[10]
#







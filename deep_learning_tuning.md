# Neural Networks and Deep Learning (notes from '17)
Neural Network (glorified logistic regression)  
IDEA - CODE - EXPERIMENT  
Neural Network Hyperparameters:
- learning rate alpha
- no of iterations
- Size of hidden layer
- activation function
- Algorithm specifics: momentum etc
- Number of hidden layers (what makes it deep)
- momentum
- mini-batch size
- regularizations

Deep Learning features:
- Deep learning = neural networks with MANY hidden layers. 
- is now succesful as it scales with more data. Other learners plateau with more data while deep NNs increase in accuracy. For smaller datasets all algorithms are comparable and performance largely depends on the match of domain and algorithm.  
- use 'relu' (y = x in x >=0; y = 0 in x < 0)  
- work well to abstract features from complex datasets. Every additional layer can tackle different low level features, like having a PCA mode in each layer.  
- Circuit theory and deep learning. a small deep network can compute mapping functions that would require a big shallow network.  
- Types of neural networks:
    - Standard
    - Convolution neural network
    - Recurrent neural network
    - Hybrid schemes: NN and RL etc

# Improving Deep Neural Networks: Hyperparameter tuning, Regularization and Optimization
 Its OK to have a mismatched train & dev/test set. A NN can learn the lower level features and fine tune to dev/test set. How to handle bias and variance: see structuring ML projects  
 Regularization:
- L2
- dropout: randomly drop units from NN
- data augmentation: symmetry operations, filters on data
- early stopping (classic)  

Regularization emphasises the larger features  
Other deep learning features:
- Mini-batch gradient descent: like bootstrapping, train on batches of data  
- momentum: exponentially weighted moving average of gradient descent, nudge gradient descent in the average direction of its motion.  
- RMSprop: 
- Adam: adapted moment estimation
- Learning rate decay: stop jumping close to the minima
- local optima: there aren't really local optima but saddle points, bad because they slow down learning
- Hyperparameter tuning (tiered by Ng):
    - alpha
    - beta, mini-batch size, hidden units
    - no of layers, learning rate decay
    - beta1/2, epsilon
- randomly select in hyperparameter space rather than grid
- sample hyperparameters on the log-scale (then fine-tune if necessary)
- pandas [babysit a model] vs caviar [run several models in parallel]
- Batch normalization: normalize the values inside a network. like a regularization. need to unnormalize for the testing phase.
- Multi-class classification: softmax regression.
- DL frameworks
 	- Caffe/2
 	- CNTK
 	- DL4J
 	- Keras
 	- Lasagne
 	- mxnet
 	- PaddlePaddle
 	- TF
 	- Theano
 	- Torch
- How to choose a DL framework:
    - ease of programming (dev and deployment)
    - running speed
    - truly open (w/ good governance)

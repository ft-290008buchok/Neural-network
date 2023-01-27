<img width="957" alt="лого для сети" src="https://user-images.githubusercontent.com/71639489/215088694-dad63d41-0676-4b45-b123-ba3496422b75.png">
Simple way to learn neural network on C++   

# 


![neural network](https://img.shields.io/badge/neural_network-000000?style=for-the-badge&logo=&logoColor=white)
![neural network](https://img.shields.io/badge/error_Back_Propagation-000000?style=for-the-badge&logo=&logoColor=white)
![neural network](https://img.shields.io/badge/c++-000000?style=for-the-badge&logo=&logoColor=white)
![neural network](https://img.shields.io/badge/stochastic_gradient_descent-000000?style=for-the-badge&logo=&logoColor=white)

# Neuran-network
It is a mini frame work for creating and training a neural network by the method of error back propagation with stochastic gradient descent for the C++ language. The  module is for designing a neural network with any number of layers of any size.

# Tests
With the help of this framework, a neural network was created to classify handwritten letters. The network was trained on a dataset of 75 immages of letters (50 x 50), in which there were 5 classes of letters (15 for each one).

Learning outcomes:

    Classification of the training sample - accuracy 100 %
    Classification of the test sample - accuracy 92 %


A more detailed description of the tests can be found [here](https://github.com/ft-290008buchok/Letter_classifier).

# Functionality
The type of activation function is a sigmoid. The type of error function is the Mean Squared Error. The learning algorithm is a method of error back propagation. The type of gradient descent is stochastic gradient descent.

    activation function:      (sigmoid) f(s) = (1 + e^(-a * s))^(-1), a = 0.4
    error function:           (MSE) (x1 - t1)^2 + ... + (xn - tn)^2, x - output layer neuron out, t - output reference value
    type of gradient descent: stochastic gradient descent
  
The name of the neural network class is classifier.

The classifier constructor accepts several parameters:   
1 - number of layers   
2 - list with the sizes of layers starting from the output and ending with the input   
3 - learning rate (step of gradient descent)   
4 - the range in which the weights of the neural network will be generated before the start of training   
5 - the number of epochs   
6 - slope of the sigmoid   

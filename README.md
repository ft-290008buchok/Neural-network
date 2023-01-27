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

For example, you can create a neural network with the following parameters  

    classifier cl(4, { 5, 50, 500, 2500 }, 1.0, 1.0, 8, 0.4);
 
 This neural network has 4 layers 5 x 50 x 500 x 2500 - size of output layer, hidden layers and input layer respectively, learning rate = 1, the initial weights of the neural network are generated in the range (-1; 1) and 8 epochs will be passed during training, and sigmoid looks like f(s) = (1 + e^(-0.4 * s))^(-1). 

To load the date set, the classifier::selection_load(dataset) method is used, the Date set must be represented as a structure
dataset.

    struct dataset
    {
    public:
        std::vector<int> data;
        int size_for_one_letter;
        int letters_number;
        int immage_size;
        std::vector<std::vector<int>> marks;
    };
    
The data vector stores all the images of the date set as a one-dimensional array in which the pixel intensity values of each image are recorded one by one (the images must be black and white). 
size_for_one_letter stores the number of training examples per class, letters_number stores the number of classes, immage_size stores the number of pixels in one image, and the marks vector stores the labels of the training sample as a two-dimensional array, the size of one label is equal to the size of the output layer, in this project it is 5, and the number of labels is letters_number * size_for_one_letter.

Label format:

All label values are zero, and the value whose number matches the class to which the image belongs is equal to one.
For example, if the 24 image in the data set belongs to the 3rd class, and there are 5 classes in total, then the 24 label will look like this - {0, 0, 1, 0, 0}.

To learn, you just need to call the classifier::learn() method.

    cl.learn();


To check the accuracy of training on a training sample, you can call the classifier::accuracy_test_on_dataset() method. 

    cl.accuracy_test_on_dataset();
    

The result of the classification of the dataset elements will be output to the console, 0 will be output for each element if the classification is performed incorrectly or 1 if the classification is performed correctly, and the overall classification accuracy for the entire data set will also be output. The perfect test result on a date set looks like this

![Screenshot 20-01-2023 220843 — копия](https://user-images.githubusercontent.com/71639489/213861107-25707bbb-ac91-4760-8c1b-8fc7ee49244d.jpg)



And to classify a new image using a trained neural network, the classifyer::classify(std::vector<int>::iterator immage) is used.

    cl.classify(simmage);
    

It takes as input an iterator of the vector of the input image, represented as a one-dimensional array, the length of which is equal to the size of the input layer of the neural network (by analogy with the dataset format), and returns the class number assigned to it by the neural network.


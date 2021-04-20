# DL_dog_breed_classification

DL_dog_breed_classification is a Project mandatory in the Udacity Nanodegree Program that i am pursuing.
i will be commenting on the key learning on the project here.

## Installation

I was using the workspace of Udacity. So this is out of the scope of this repository unfortunately.

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites
#### Skills / Knowledge
understand and/or have experience with:
- the functioning of MLP: Model architecture building, feedforward design, backpropagation, optimizer definition, loss function definition 
- the functioning of CNN: the layers, the filters and the best practices of the design of the Convolutional layers: the number of the filters, the dimensionality computation especially with the appropriate padding, stride and kernel size.
- the functioning of transfer learning and how to choose the strategy giving the quantity of the new data and the similarity of the data and the use case.

#### Infrastructure 
The data (for train validation and test)
What things you need to install the software and how to install them


## Key learning (and practice)
**1. For the Model from the scratch**
### Data collection: or real time data handling
- define a data loader to read in batch the data for train, validate and test, with the corresponding transformer.

### Data preprocessing
- design the needed transformer 
- adapt the transformer (of the training data) to the uses case and to the expected data: make a good use of data augmentation as it has a surprisingly huge impact on the performances. 
### Data mining
#### Model architecture building 
Build the logic of features extraction from the images, reducing the dimensionality of the image and adding the number of filters each layer. Check consistency between the outputs of the layer source and the inputs of the layer target every time. 
#### Feedforward design
put all of that in action: Stack in a sequential order the layers with the needed activation functions and pooling.
#### Optimizer and loss function definition
Since it is a classification, the loss function is the Cross-Entropy Loss function. And we start by the basic Stochastic Gradient Descent Optimizer.
#### Backpropagation
- don't forget to initialise the optimizer gradient to zero at the beginning of each iteration (each batch of each epoch). 
- perform the error computation: the difference between the output of the forward pass thru the network and the desired target. 
- perform an optimizer step. 
-  And iterate this on 
### Model hyper-parameters optimization 
- When training and validating, we keep the focus on both training loss and validation loss, both should be decreasing. Optimize the number of epochs, the learning rate if the Losses are fluctuating. Stop the training when the validation Loss is starting to increase. 
- The test accuracy has a minimum threshold, if it is not met, this could mean that the model architecture  or the train data transformer were insufficient to enable the model to generalize or to have enough prior knowledge on the 2d distribution and can't extract enough features. I changed the model architecture by adding a new conv layer, (this solved the issue of not decreasing validation Loss)

**2. For the Transfer learning**
### Strategy:
- small new data
- similar data and use case
==> at the end of the conv net.
### Data Collection and preprocessing :
the same as above
### Data mining
#### Model architecture building 
- Freese the weights not to be updated
- Overwrite the last layer with the needed number of classes (the classifier las fully connected layer) 
#### Feedforward design
- define the Loss criterion 
- define the optimizer on the parameters of the last layer (the only weights to be updated in the whole network)
# Acknowledgments
This was possible thanks' to the course of Udacity, especially the ask a mentor pool :)

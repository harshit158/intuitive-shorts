# Design Pattern 1: Useful Overfitting

Overfitting is useful when:  
1. There is no noise -> Labels are accurate for all instances 
2. Entire input space can be tabulated (you have all the possible examples)
3. Knowledge Distillation from Larger ML model into smaller ML model
<br>  
  

Points:  
1. The best fitting model is a "large" model that has been properly "regularized"
2. A complex enough model should be able to overfit on a small enough batch of data, provided everything is setup correctly.

<br>

# Design Pattern 2: Checkpoints
**Checkpointing**: Saving full model state (entire internal state) so that model training can be resumed from a point  
Example of model's state:  
1. Dropout
2. Learning rate, if the model uses scheduler  
3. History of previous inputs, in case of RNNs 

<p align="center"><br><img  src=docs/chknoequal.png width=600></br></p>

* Exporting model only exports information necessary to create prediction function (Eg: weights and biases for linear model) whereas checkpointing saves entire state

* Tensorflow and Keras automatically resume training from checkpoint if checkpoints are found in the training path
* This is not available in Pytorch. This is how its done in pytorch:

<p align="center"><br><img  src=docs/pytorch_chkpnt.png width=800></br></p>


**Uses of Checkpointing**
1. Resilience: Robustness against machine failure
2. Generalization: Early stopping
3. Tuneability: Fine tune from a particular point of time (particular checkpoint)
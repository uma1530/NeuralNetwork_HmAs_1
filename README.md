# NeuralNetwork_HmAs_1

CODE 1 :

Step 1: Creating a Random Tensor
We generate a tensor of shape (4,6) with random values between 0 and 1 using tf.random.uniform().
tf.random.uniform(shape=(4,6)) generates a tensor with shape (4,6), filled with random values from a uniform distribution between 0 and 1.
The numpy() function is used to print the tensor values in NumPy format.
Step 2: Finding Rank and Shape
In TensorFlow, we can determine a tensor’s rank (number of dimensions) and shape (size along each dimension).

Step 2: Finding Rank and Shape
tf.rank(tensor) returns the number of dimensions.
tf.shape(tensor) returns the shape as a TensorFlow tensor.

Step 3: Reshaping and Transposing
Now, we reshape the tensor from (4,6) to (2,3,4) and transpose it to (3,2,4).

Step 3: Reshaping and Transposing
Now, we reshape the tensor from (4,6) to (2,3,4) and transpose it to (3,2,4).
tf.reshape(tensor, (2,3,4)) modifies the shape without changing the data.
The total number of elements (4×6 = 24) must match (2×3×4 = 24).

Step 4: Broadcasting and Addition
What is Broadcasting?
Broadcasting allows TensorFlow to perform operations on tensors of different shapes by automatically expanding the smaller tensor to match the larger tensor’s shape.

Example of Broadcasting
We create a small tensor of shape (1,4), then add it to the (3,2,4) tensor.

Final Summary
Step	Operation	Shape
1	Create a random tensor	(4,6)
2	Find rank and shape	Rank = 2, Shape = (4,6)
3	Reshape tensor	(2,3,4)
4	Transpose tensor	(3,2,4)
5	Broadcast and add (1,4) tensor	(3,2,4)


CODE 2 :

Step 1: Import Required Libraries
tensorflow: Used for defining and computing loss functions.
numpy: Used for handling arrays (true values and predictions).
matplotlib.pyplot: Used for visualizing loss values using a bar chart.

Step 2: Define True Labels (y_true) and Model Predictions (y_pred)
y_true represents the true class labels in a one-hot encoded format, where each row corresponds to a sample.
[0, 1, 0] → The second category is the correct class.
[1, 0, 0] → The first category is the correct class.
y_pred1 and y_pred2 represent two sets of model predictions.
Values represent the predicted probabilities for each class.
y_pred2 is a slight variation of y_pred1 to analyze the impact of small changes on loss values.

Step 3: Compute Mean Squared Error (MSE) Loss
MeanSquaredError() computes the squared difference between y_true and y_pred, then averages over all samples.
.numpy() converts the TensorFlow tensor to a NumPy float.
mse1 and mse2 store the computed loss values.

Step 4: Compute Categorical Cross-Entropy (CCE) Loss
CategoricalCrossentropy() measures how well the predicted probability distribution matches the true class distribution.
.numpy() extracts the computed loss as a float.
cce1 and cce2 store the loss values.

Step 5:Plot Loss Function Values using Matplotlib
Creates a bar chart comparing loss values.
labels: Stores names for bars (representing different loss values).
loss_values: Stores corresponding loss values.
plt.bar():
Plots bars for each loss.
Uses different colors (blue, cyan, red, orange).
plt.show(): Displays the bar chart.

CODE 3:

Step 1:Importing Required Libraries
Tensorflow (tf):
A popular deep learning framework that provides tools to create, train, and evaluate neural networks.
We use it to build the MNIST model, define layers, set optimizers, and train the network.

Matplotlib (plt):
A Python library for creating graphs and visualizations.
Used here to plot accuracy trends of the two optimizers (Adam and SGD).

Step 2:Loading the MNIST Dataset
MNIST is a dataset of handwritten digits (0–9), containing 70,000 grayscale images.
Each image is 28×28 pixels in size, and each pixel has an intensity between 0 (black) and 255 (white).
mnist.load_data():

Loads the dataset and returns:
Training Set:
x_train: 60,000 images for training.
y_train: 60,000 corresponding labels (digit 0–9).
Testing Set:
x_test: 10,000 images for testing.
y_test: 10,000 corresponding labels.

Step 3: Normalizing the Data
Why Normalize?
Pixel values range from 0 to 255, making them too large.
Deep learning models work better when inputs are in a smaller range (e.g., 0–1).
Normalizing improves model stability and training speed.
We divide by 255 to scale values between 0 and 1.

Step 4:Defining the Model Architecture
Creates a feedforward neural network using the Sequential API.
Layers in the Model:

Flatten Layer (Flatten(input_shape=(28, 28)))

Converts 2D image (28×28) into a 1D array of 784 values.
This allows the dense (fully connected) layer to process the data.
Dense Layer (Dense(128, activation='relu'))

A fully connected layer with 128 neurons.
Uses ReLU (Rectified Linear Unit) as the activation function, which helps the network learn complex patterns.
Output Layer (Dense(10, activation='softmax'))
Uses Softmax Activation, which outputs probabilities for each digit class.

Step 5:Training and Evaluating the Model
Function train_model(optimizer, optimizer_name):

Trains a model with a specified optimizer (Adam or SGD).
Returns training history, which contains accuracy values.
model.compile():

Optimizer:
Determines how the model updates weights to minimize error.
Loss Function (sparse_categorical_crossentropy):
Measures how far the predicted values are from actual labels.
Used for multi-class classification problems.
Metric (accuracy):
Monitors how well the model predicts correct labels.
Training (model.fit()):

Step 6:Plotting Accuracy Trends
history_adam.history['val_accuracy'] → Accuracy trend for Adam.
history_sgd.history['val_accuracy'] → Accuracy trend for SGD.
Graph Labels:

xlabel("Epoch") → X-axis represents the number of epochs.
ylabel("Validation Accuracy") → Y-axis represents the model's accuracy on test data.
title("Adam vs. SGD on MNIST") → Title of the plot.
legend() → Labels Adam and SGD on the graph.
plt.show() → Displays the plot.

CODE 4:

Step 1:Import Required Libraries

tensorflow: The main library for building and training neural networks.
datetime: Used to generate unique log directory names for TensorBoard.
tensorflow.keras: Keras is TensorFlow's high-level API for building models.
mnist: Contains the MNIST dataset, which consists of 28x28 grayscale images of handwritten digits (0-9).

Step 2: Load and Preprocess the MNIST Dataset
The dataset consists of 60,000 training images and 10,000 test images.
Each image is 28x28 pixels and has pixel values ranging from 0 to 255.
We normalize the pixel values by dividing by 255.0 so they fall in the range [0,1]. This helps the model train faster and improves performance.

Step 3:Define the Neural Network Model
Flatten(input_shape=(28, 28))

The input images are 28x28 matrices.
This layer converts each 2D image into a 1D vector (28 × 28 = 784 values).
This makes it easier for the Dense layers to process.
Dense(128, activation='relu')

A fully connected layer with 128 neurons.
ReLU (Rectified Linear Unit) activation function is used to introduce non-linearity:
f(x)=max(0,x) (If x is negative, output is 0; otherwise, it's x).
Dropout(0.2)

Dropout is a regularization technique that randomly disables 20% of neurons during training.
This helps prevent overfitting by making the model rely on multiple neurons instead of memorizing patterns.
Dense(10, activation='softmax')

The output layer has 10 neurons (one for each digit 0-9).
Softmax activation converts the output into a probability distribution (sum of all outputs = 1).
The neuron with the highest probability corresponds to the predicted digit.

Step 4:Compile the Model
optimizer='adam':
Adam (Adaptive Moment Estimation) is an efficient gradient descent algorithm.
It adapts the learning rate for each parameter, improving convergence.
loss='sparse_categorical_crossentropy':
Since we have 10 classes (digits 0-9), we use categorical cross-entropy.
"Sparse" means the labels are integers (0-9) rather than one-hot encoded vectors.
metrics=['accuracy']:
The model tracks accuracy during training and evaluation.

Step 5:Setup TensorBoard Logging
TensorBoard Callback
log_dir:

Stores logs in a folder named "logs/fit/", followed by a timestamp.
This ensures each training session has a unique log directory.
tf.keras.callbacks.TensorBoard(log_dir=log_dir, histogram_freq=1):

This callback logs training progress for visualization in TensorBoard.
histogram_freq=1 logs weight/bias histograms every epoch.

Step 6:Train the Model
epochs=5: The model trains for 5 passes over the dataset.
validation_data=(x_test, y_test): The model is tested on unseen test data after each epoch.
callbacks=[tensorboard_callback]: Logs training data for TensorBoard.
loss: Training loss (should decrease over time).
accuracy: Training accuracy (should increase over time).
val_loss: Validation loss (should also decrease).
val_accuracy: Validation accuracy (should approach 98%).

Step 7:7. Launch TensorBoard
After training, open a terminal and run:

Serving TensorBoard on google colab; to access it type one of:
    - %load_ext tensorboard
      %tensorboard --logdir logs/fit
      
Open the provided link in a browser to visualize:

Expected TensorBoard Graphs
Loss Trend (Should decrease)

Training Loss (orange)
Validation Loss (blue)
Accuracy Trend (Should increase)

Training Accuracy (orange)
Validation Accuracy (blue)


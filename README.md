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

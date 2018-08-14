## Activation Functions: Neural Networks
Sigmoid, tanh, Softmax, ReLU, Leaky ReLU EXPLAINED !!!

https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6

## How to make a custom activation function with only Python in Tensorflow?
https://stackoverflow.com/questions/39921607/how-to-make-a-custom-activation-function-with-only-python-in-tensorflow/45258567#45258567

Why not simply use the functions that are already available in tensorflow to build your new function?

For the spiky function in your answer, this could look as follows
```
def spiky(x):
    r = tf.floormod(x, tf.constant(1))
    cond = tf.less_equal(r, tf.constant(0.5))
    return tf.where(cond, r, tf.constant(0))
```
I would consider this substantially much easier (not even need to compute any gradients) and unless you want to do really exotic things, I can barely imagine that tensorflow does not provide the building blocks for building highly complex activation functions

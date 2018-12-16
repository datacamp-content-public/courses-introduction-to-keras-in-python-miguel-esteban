---
title: Insert title here
key: 4aa97343ec6ed6da2044ce7c1bf8ab70

---
## Binary Classification

```yaml
type: "TitleSlide"
key: "2552584a8c"
```

`@lower_third`

name: Miguel Esteban
title: Data Scientist & Founder


`@script`
You're now ready to learn about binary classification, which it's the same as saying a two-class classification. So let's dive in.


---
## When to use binary classification ?

```yaml
type: "TwoColumns"
key: "184e6e3fbc"
center_content: true
```

`@part1`
- Fraudulent or non fraudulent client.
- Swimming or running.
- Winter or Summer.
- Cat or Dog.
- Survived or died.
- ...


`@part2`
**Separate Blue and Red Circles.
**
![](https://assets.datacamp.com/production/repositories/4255/datasets/2bb6403d0f63d721f8ec54dd28954a3b07c577af/binaryClassificationExample_2.png)


`@script`
You will use binary classification when you want to solve problems where you predict whether an observation belongs to one of two possible classes. For instance distinguishing between fraudulent or non fraudulent clients, swimming or running, telling whether a picture shows a cat or a dog, if someone will survive or die, etc. A simple binary classification problem could be learning the boundaries to separate the blue and red circles shown in the image. So let's try to do so.


---
## Our Dataset

```yaml
type: "TwoColumns"
key: "955fcee383"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/5bf612d61aaf330495682c6b6d053801726f8b03/circle_dataset.jpg)


`@part2`
**Separate Blue and Red Circles.
**
![](https://assets.datacamp.com/production/repositories/4255/datasets/2bb6403d0f63d721f8ec54dd28954a3b07c577af/binaryClassificationExample_2.png)


`@script`
The dataset for this problem is very simple. The predictors correspond to the X and Y coordinates of each circle in the graph. The y variable encodes the labels, which are 1 for red circles and 0 for the blue circles.


---
## The NN architecture

```yaml
type: "FullImageSlide"
key: "dde3977ea4"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/0ac38616114bffe1b1e8031d88ba5f5421396ca5/nn_bin_class_1.jpg)


`@script`
This is the neural network we will build to classify red and blue dots in our graph.


---
## The NN architecture II

```yaml
type: "FullImageSlide"
key: "6f00141876"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/a2700675a47a36b8dbd19d9891fa78b4803e0fdd/nn_bin_class_2.jpg)


`@script`
In this case I have two neurons as an input layer, one for the x coordinate and another for the y coordinate of each of the red and blue circles in the graph.


---
## The NN architecture III

```yaml
type: "FullImageSlide"
key: "d85bfa61aa"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/1c7f14318c26b4b8887031ef1edb65d0d5999083/nn_bin_class_3.jpg)


`@script`
Then we have a number of hidden layers, this will vary depending on our data and experimentation. We just have one in this example.


---
## The NN architecture IV

```yaml
type: "FullImageSlide"
key: "7152c0432c"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/a7e4e63f43f1ba0e17d7b59a58720279e704d3cf/nn_bin_class_4.jpg)


`@script`
We finally end up with a single output neuron which makes use of the sigmoid activation function. It's important to note that, regardless of the activation functions used for the previous layers, we need the sigmoid activation function for this last output node.


---
## The sigmoid function.

```yaml
type: "FullImageSlide"
key: "5a9b2b811d"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/ed50e362b3e2a6f4d5f23aa3863860c1d8b1af4a/nn_bin_class_5.jpg)


`@script`
The sigmoid activation function squashes our neuron output to a number between 0 and 1. We can see this output as the probability of our observation to be in one class or another. So we can set a threshold and say everything below 0.5 will be a blue circle and therefore everything above will be classified as a red one.


---
## Let's build it.

```yaml
type: "TwoRows"
key: "060307d6c5"
center_content: true
```

`@part1`
```python
from keras.models import Sequential
from keras.layers import Dense
```{{1}}
```python
# Create sequential model
model = Sequential()
```{{2}}
```python
# Add input layer and a hidden layer
model.add(Dense(4,input_shape=(2,),activation='tanh'))
```{{3}}
```python
# Add output layer, using sigmoid activation
model.add(Dense(1,activation='sigmoid'))
```{{4}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4255/datasets/f72bb9abe50c4d3c70571ab871b64faddb2525aa/nn_rotated_1.jpg){{5}}


`@script`
So let's build our model in keras. 

- We start by importing the sequential model and the dense layer.
- We then create a sequential model.
- We add a hidden layer of 4 nodes and we define an input shape, which consist of 2 neurons,we will use the tanh, or hyperbolic tangent activation function, for this hidden layer. 
- We finally add an output layer which contains a single neuron, we make use of the sigmoid activation functions so that we achieve the behavior we expect from this network.

Our model is ready to be trained.


---
## Compiling and training.

```yaml
type: "FullCodeSlide"
key: "52aaa381af"
```

`@part1`
```python
from keras.optimizers import SGD
```{{1}}
```python
# Compile our model, we'll use binary-crossentropy
model.compile(optimizer=SGD(lr=0.5),
              loss='binary_crossentropy',
              metrics=['accuracy'])
```{{2}}
```python
model.train(X,y,epochs=20)
```{{3}}
![](https://assets.datacamp.com/production/repositories/4255/datasets/1b4f75fe245abddd0bc082df7e4b72ec8aabb589/binaryClassificationExample_1.png){{4}}


`@script`
Just as before, we need to compile our model before training. 
We will use stochastic gradient descent as an optimizer and binary crossentropy as our loss function. 

Cross-entropy loss increases as the predicted probability diverges from the actual label. Imagine we predicted .012 (a very close to 0 result, therefore very close to a blue circle), when the actual observation label was 1, (a red circle). This would be a very bad outcome for our network and therefore result in a high loss value.

We finally train our model for 20 epochs passing X and y.

The boundaries this model learned to classify our circles is shown in the graph below.


---
## Let's practice!

```yaml
type: "FinalSlide"
key: "2b83e62a1e"
```

`@script`
Now you've learned the basics it's time to have some fun with this new architecture you've learned.


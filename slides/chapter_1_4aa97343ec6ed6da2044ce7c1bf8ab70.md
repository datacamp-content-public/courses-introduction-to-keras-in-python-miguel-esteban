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
![](https://assets.datacamp.com/production/repositories/4255/datasets/2c3b85207be989718296699359a34fa49ec18da1/binaryClassificationExample_1.png)


`@script`
You will use binary classification when you want to solve problems which consist of predicting whether an observation belongs to one of two possible classes. For instance distinguishing between fraudulent or non fraudulent clients, swimming or running, telling whether picture shows a cat or a dog, if someone will survive or die, etc. A simple binary classification problem could consist in learning boundaries to separate blue from the red circles as shown in the image. So let's dive into how we would solve this problem.


---
## An architecture for our problem.

```yaml
type: "FullImageSlide"
key: "dde3977ea4"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/0ac38616114bffe1b1e8031d88ba5f5421396ca5/nn_bin_class_1.jpg)


`@script`
Our neural network architecture closely depends on the type of problem we are solving. For binary classification we have an input layer of N neurons, matching the number of features of our dataset.


---
## An architecture for our problem II

```yaml
type: "FullImageSlide"
key: "6f00141876"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/a2700675a47a36b8dbd19d9891fa78b4803e0fdd/nn_bin_class_2.jpg)


`@script`
In this case I have two neurons as an input layer, one for the x coordinate and another for the y coordinate of each of the red and blue points of our graph.


---
## An architecture for our problem III

```yaml
type: "FullImageSlide"
key: "d85bfa61aa"
disable_transition: true
center_content: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4255/datasets/1c7f14318c26b4b8887031ef1edb65d0d5999083/nn_bin_class_3.jpg)


`@script`
Then we have a number of hidden layers, this will vary depending on our data and experimentation.


---
## An architecture for our problem IV

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
The sigmoid activation function squashes our neuron output to a number between 0 and 1. We can look at this output as the probability of our observation to be in one class or another. So we can set a threshold and say everything below 0.5 will be in class A and therefore everything above will be classified as our class B.


---
## Let's build it.

```yaml
type: "TwoRows"
key: "060307d6c5"
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
# Add output layer, using the sigmoid activation
model.add(Dense(1,activation='sigmoid'))
```{{4}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4255/datasets/f72bb9abe50c4d3c70571ab871b64faddb2525aa/nn_rotated_1.jpg){{4}}


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "2b83e62a1e"
```

`@script`



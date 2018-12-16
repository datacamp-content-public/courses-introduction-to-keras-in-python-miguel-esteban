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
You will use binary classification when you want to solve problems which consist of predicting whether an observation belongs to one of two possible classes. For instance distinguishing between fraudulent or non fraudulent clients, swimming or running, telling whether picture shows a cat or a dog, if someone will survive or die, etc. A simple binary classification problem could consist in learning boundaries to separate blue from the red circles as shown in the image.


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
In this case I have two neurons as an input layer, you can think of them as the x and y components of each of the points on a graph.


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
## An architecture for our problem.

```yaml
type: "FullImageSlide"
key: "3054fd6daf"
```

`@part1`



`@script`
We finally end up with a single output neuron which makes use of the sigmoid activation function. It's important to note that, regardless of the activation functions used for the previous layers, we need the sigmoid activation function for this last output node.


---
## The sigmoid function.

```yaml
type: "TwoRows"
key: "38db70007c"
```

`@part1`



`@part2`



`@script`
The sigmoid activation function squashes our neuron output to a number between 0 and 1. We can look at this output as the probability of our observation to be in one class or another. So we can set a threshold and say everything below 0.5 will be in class A and therefore everything above will be classified as our class B.


---
## Let's build it.

```yaml
type: "TwoColumns"
key: "cacbf0008f"
```

`@part1`



`@part2`



`@script`
Building such a model is easy! We start defining a sequential model. We then add an input layer of a chosen number of nodes, the input shape will match the number of predictor variables in your dataset. For this generic case let's suppose we have 3 predictive variables. We can then add as many hidden layers as needed, we can also choose any activation function for these. We finally add a single node as our output, and we make use of the sigmoid activation function. You've just defined a binary classification model!


---
## Binary Cross Entropy

```yaml
type: "TwoColumns"
key: "1ff3fc83a6"
```

`@part1`



`@part2`



`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "2b83e62a1e"
```

`@script`



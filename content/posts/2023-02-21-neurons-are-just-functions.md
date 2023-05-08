---
title: Neurons Are Just Functions
date: 2023-02-21
description: 🧠 == f(x)
cover: /img/neurons-are-just-functions/cover.webp
tags: [neuralnetworks]
---

A neuron simply takes in data, performs a function on it, and outputs a result.

## The Power Of A Single Neuron

Let's use one neuron to perform a function! A great tool for playing with neural networks is TensorFlow Playground. You can find the link [here](https://playground.tensorflow.org/#activation=linear&batchSize=10&dataset=gauss&regDataset=reg-plane&learningRate=0.001&regularizationRate=0&noise=0&networkShape=1&seed=0.93595&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false). If you click on it, you'll see the example I'm about to cover.

{{< figure src="/img/neurons-are-just-functions/img-2.png" alt="demo" position="center" caption="Our neural network with only one neuron." captionPosition="center" >}}

- Our goal is to draw a clear line that separates the orange and blue scatterplot.

- The function of the neuron is to take two x-inputs and combine them to calculate a diagonal line that will divide the scatterplot.

- Click the play button to see the neuron in action! After several attempts, it will "learn" the values of `x1` and `x2` that are needed to draw the dividing line.

{{< figure src="/img/neurons-are-just-functions/img-1.png" alt="demo" position="center" caption="Our function is receiving two x-inputs. The first one draws a vertical line and the second one draws a horizontal line." captionPosition="center" >}}

## Limitations

As we saw, a single neuron can succeed in this simple classification task. However, what if we had a more complex shape to classify?

Several datasets are available in TensorFlow Playground. If you try changing the shape to something else, you'll see that the neuron will fail. These complex shapes require more lines to be drawn.

{{< figure src="/img/neurons-are-just-functions/img-3.jpg" alt="demo" position="center" caption="This dataset is too complex for one neuron." captionPosition="center" >}}

## Add More Neurons!

To properly classify this scatterplot, we need to:

- Add two more neurons (3 total)
- Change the 'Activation' field from `linear` to `tanh` (this topic is for another day)

After some iterations, the three neurons will succeed! You can find the TensorFlow Playground link for this demo [here](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=3&seed=0.32906&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false).

![demo](/img/neurons-are-just-functions/img-4.png)

## Conclusion

Neurons perform mathematical functions and take parameters (x1, x2, x..., x99) to output a result. Having more neurons makes it possible to perform more complex tasks.

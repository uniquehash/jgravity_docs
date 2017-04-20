# jgravity_docs

This repo is contains all documentation for working on the jgravity project.

The [jgravity project](https://drive.google.com/open?id=0B-1wnpl3HILiNFM4VXhBeVE4UUE)is an attempt to simulate the universe as detailed by the [The	Janus	Cosmological	Model](https://www.savoir-sans-frontieres.com/JPP/telechargeables/English/janus/The%20Janus%20Cosmological%20Model.pdf).

To summerize, the Janus Model conceives two types of matter that have simple relationships between each other. We conceive these two types of matter as Positive Matter and Negative Matter. Positive Matter atracts other Positive Matter, and repels Negative Matter, whereas Negative Matter attracts other Negative Matter and repels Positive Matter. 

The central intuition of the Janus Model is that by using **positive mass** to represent Positive Matter, and **negative mass** to represent Negative Matter we should be able to use basic gravitational mathematical concepts to explain much of the behavior observed in our cosmos.

The core of this project is the [physics simulation](https://github.com/all-hack/jgravity_docs/blob/master/physics_simulation.md) the process of actually simulating the Janus Model. There are two other parts of almost equal importance: a graphical renderer, and concurrent processing optimizations.

**graphical renderer**
A graphical renderer allows us to visualize the data and make sense of it, something we would be unable to do by simply looking at rows of numbers in a file.

**concurrent processing optimizations**
The vey nature of simulating physics is computationally intensive, but when we think of it on the scale of the *universe* it becomes quite absurd. For this project to be useful it will be absolutely necessary to maximize the amount of processing power available to us. It will be imperative to use multi-threading to maximize the processing power of each computer, and multi-server to increase the maximum total power available.

At this point a lot of this project is not figured out, however we have begun putting together some [first principles of our sytem](https://github.com/all-hack/jgravity_docs/blob/master/first_principles.md). There are [optimizations](https://github.com/all-hack/jgravity_docs/blob/master/optimizations.md) we are thinking about, but until we have some benchmarks of how much a single threaded program can handle, they seem difficult to concretize.










# DOOM RL with Grad-CAM



### What is this?

Hey, this is my project where I trained a Reinforcement Learning (RL) agent to play **DOOM** (specifically the VIzDoom environment).



The main goal was to compare different neural networks architecture to see which one learns best, custom CNN or NaturalCNN. I also add an **Explanaible AI** component using **Grad-CAM** because I wanted to see what the agent was actually looking at when it decided to shoot or move.



### Tech Stack

I ran this on Google Colab. Here are the main libraries I used:

- **VizDOOM:** The game environment (obviously).

- **Stable-Baselines3:** For the PPO implementation and vectorized environments.

- **Gymnasium:** To wrap the DOOM env so SB3 can talk to it.

- **PyTorch:** For NN.

- **MoviePy:** To record agent playing.



### Installation

If you want to run this, you'll need the dependencies. I put a cell at the top of notebook, but basically:

---

```
pip install stable-baselines3[extra] gymnasium vizdoom moviepy
```



### The Architectures

I tried to experiment with the different feature extractors (CNNs) to process the game frames. The notebook compares how these architectures handle the visual input and how fast they converge.



### Results

The results were pretty interesting.



###### Learning Curves



![](D:\ML\Doom\learning_curve.png)

Here is the training process of Custom CNN on `basic.cfg` over time. You can see how the agent started out clueless and eventually figured out the game mechanics. Eventually the reward stablizes.



###### Final Comparison

![](D:\ML\Doom\comparison_chart.png)



After training, I compared the two models (CustomCNN and Nature CNN) on `defend_the_center.cfg` scenario. Nature CNN, being the superior and more refined backbone, obviously won.



### Grad-CAM

This generates a heatmap over the game frame showing which pixels activated the neural network the most. Basically, it lets us see if the agent is focusing on monsters or just staring at the floor.

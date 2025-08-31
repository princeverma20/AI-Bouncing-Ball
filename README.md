## Genetic Algorithm (Neuro Evolution)
Bouncing Ball Game

### Overview:

In this project I have implemented AI bouncing ball game using Neural Network whose
weights are controlled by Genetic Algorithm. (Neuro Evolution). The Bouncing ball game is
contain paddle and the ball and the aim is to avoid ball to hitting the ground. Paddle can move
in 2 directions (left or right) and it is controlled by the output of fully connected neural
network. Since, we don’t have specific training data to train neural network, we use streaming
data as input to neural network and its weights is updated using genetic algorithm (using
score as fitness). Runing instruction is given at the end.

### Implementation:

This project contains 4 py files –

#### Game.py – contains bouncing ball game logic.
#### Genetic_Algorithm.py – to generate the agents to play bouncing ball game.
#### Neural_Network.py – to control the paddle.
#### Dynamic_plot.py – used to plot the dynamic graph of fitness vs generations.

#### Details:

<li> Game.py: This file contains logic to play bouncing ball game. Used as GUI (TkInter library in
python). Contains randomly moving ball and the paddle to bounce the ball. Objective here is
learn the movement of paddle using NN and GA. Which will be explained further below. </li>

<li>Genetic_Algorithm.py:

#### Steps:

  Generate a random population of weights for neural network. Neural network
  architecture used is 2 input node, 1 hidden layer with 2 nodes and one output node.
  So chromosome length is 6 (Bias is handled separately) with random floating
  numbers. Population size is 10.
  
  Genotype and phenotype mapping here is random floating numbers as weights which
  controls output of neural network which in return controls the movement of paddle.
  Evaluation of fitness: Each Agents (population) is allowed to play a game and its score
  (no of times successful hits) is recorded.
  
  Fitness function = Score – abs(x_position of ball - x_position of paddle)/(total
  window length i.e. 600)
  abs(x_position of ball - x_position of paddle)/(total window length i.e. 600) is used
  to determine how far is the ball from paddle just before ball hits the ground. This
  ensures the paddle come near ball at each generation i.e. near miss is better.
  
  Selection: Top 20% Agents (based on fitness) are selected.
  
  Cross Over – 2 Random choice of selected agents (20%) for crossover and mutation.
  
  Child1 and child2 from parents are created hoping better solution found and increase
  the diversity.
  
  Mutation: Mutation rate used is 0.3. Randomly select the single index of the
  chromosome and previous weight + randomly generated number between (-2, 2).
  
  This process is repeated for 100 generations (excepts the first step).
  Observation: Can obtain score of 25 in around 5-6 generations. Can obtain more if we train
  more. However, its is likely to get stuck at local maxima. (stuck at score 25 can see in below
  graph)
  
  ![sim1](https://user-images.githubusercontent.com/32418025/41754774-c286480c-75cb-11e8-8564-4d26a8baf97e.png)

<li> Neural Network.py: Structure of neural network implemented here is 2 input node, single
hidden layer with 2 nodes and one output node. </li>

  Input to NN contains 2 features –

  Feature 1: x_position_ball – x_position_paddle
  Feature 2: y_position_ball – y_position_paddle
  Output node is given to the paddle controller. If output is <= 0.5 turn left else turn right. The
  weights of the NN is represented as chromosome from genetic algorithm.

  <b>Note:</b> Random initialization of weights is done + or – around base or reference value. This is
  because to save simulation time. This value is found using experimentation.

<li> Dynamic_plot.py: This used to get dynamic plot of fitness vs no of generations. </li>

### Simulation Results and Discussion:

![sim2](https://user-images.githubusercontent.com/32418025/41754810-fe09cf2a-75cb-11e8-88bb-0afea46274f8.png)
![sim3](https://user-images.githubusercontent.com/32418025/41754819-0861ff42-75cc-11e8-9702-bab23761bca3.png)

### Conclusion:

From the above simulation we can see that for fitness is reached around 21 for 10th
generation. Moreover, similar fitness value also reached at generation 5, 6 and 7. Hence,
there may be another solution which can give better solution. This needs to be experimented.
From above simulations we can see that GA stuck at local maxima. We need to include more
diversity in order to get out from the local maxima. More generations is also likely to help to
kick off from local maxima.

### Instruction to run code:

<li> Folder structure – Genetic_Algorithm -> Demo, python_vitrual_environment. </li>
<li> Demo -> Dynamic_plot.py, Neural_network.py, Genatic_Algorithm.py, Game.py </li>
<li> Create python virtual environment in Genetic_Algorithm folder. </li>

Required Packages –
<li> certifi==2018.4. </li>
<li> curses-util==0.0. </li>
<li> cycler==0.10. </li>
<li> fuzzywuzzy==0.16. </li>
<li> kiwisolver==1.0. </li>
<li> matplotlib==2.2. </li>
<li> numpy==1.14. 5 </li>
<li> Pillow==5.1. </li>
<li> pygame==1.9. </li>
<li> pyparsing==2.2. </li>
<li> python-dateutil==2.7. </li>
<li> pytz==2018. </li>
<li> scipy==1.1. </li>
<li> six==1.11. </li>
<li> wincertstore==0. </li>

<li> Run Genetic_Algorithm.py file – </li>

## Reference:

[1]. DJ Oamen – Bouncing ball game code python.
https://www.youtube.com/watch?v=9tVCYIcwNjw

[2]. Genetic Algorithm – wiki https://en.wikipedia.org/wiki/Genetic_algorithm

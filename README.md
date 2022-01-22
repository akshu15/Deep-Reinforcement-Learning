# Deep-Reinforcement-Learning

# Description
The goal of the assignment is to learn the trends in stock price and perform a series of trades over a period of time and end with a profit.
In each trade we can either buy/sell/hold. We start with an investment capital of $100,000 and the performance is measured as a percentage of the return on investment. Here we have used Q-Learning algorithm for reinforcement learning to train an agent to learn the trends in stock price and perform a series of trades. The purpose of this assignment is to understand the benefits of using reinforcement learning to solve the real world problem of stock trading.
For this assignment we have used dataset on the historical stock price for Nvidia for the last 5 years.
The dataset has 1258 entries starting 10/27/2016 to 10/26/2021. The features include information such as the price at which the stock opened, the intraday high and low, the price at which the stock closed, the adjusted closing price and the volume of shares traded for the day.

# 1.1 Implementing Q-Learning
Define a Q-Learning table of size states by actions. 
In our case we have 4 states and 3 actions (Buy/Hold/Sell).
Initialize the table to zeros, later we will update it with new values during training.
Now training consists of series of episodes, we have used 1000 episodes.
We first call the reset method of the environment for storing the current state. The function returns an integer in the range of 0 to 3 representing the four possible observations that the agent can receive.
The observation depends upon whether the price increased on average in the number of days the agent considers, and whether the agent already has the stock or not.
Now until each episode gets ended, agent selects a random action or exploits an already computed Q-value. This is done by selecting an arbitrary number between 0 to 1 and comparing it with the epsilon. The epsilon is updated at the end of each episode using the exponential decay formula.
The selected action is then passed to the stock environment using environment’s step method. This method implements what happens when the agent takes the action to Buy/Sell/Hold.

Input parameter:

action: - Integer in the range 0 to 2 inclusive. 0- Buy, 1- Sell, 2- Hold.

Returns:

new state: - observation

reward: - Integer/Float value that’s used to measure the performance of the agent.

done: - Boolean describing whether or not the episode has ended.

info: - A dictionary that can be used to provide additional implementation information.

The Q-Learning table entry is updated using the update rule.
After applying the Q-learning algorithm to solve the stock trading problem we get the following plots.

<img width="650" alt="3_1" src="https://user-images.githubusercontent.com/52970601/150617238-96e7a7e8-2d63-4d44-a22c-284adbd0ed5b.png">

<img width="650" alt="3_3" src="https://user-images.githubusercontent.com/52970601/150617261-cb527652-696b-4388-8299-2b27a7acb3e3.png">

During evaluation we run our trained agent (you will have to set the train parameter to false) and evaluate the agent’s performance, where the agent chooses only greedy actions from the learnt policy.
The plot shows the increase in Agent’s account value over time.

<img width="650" alt="3_2" src="https://user-images.githubusercontent.com/52970601/150617290-aa3661b3-4355-484c-b943-6cda82475ba4.png">

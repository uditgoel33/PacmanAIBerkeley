Pacman: Capture the Flag – Wiki     
Team: Power-Rangerz

**YouTube Link** : https://www.youtube.com/watch?v=QPIAh4Phl0s&feature=youtu.be

**Table of Contest**
1.Introduction
2.Techniques Attempted
     2.1.MDP with Value Iteration
     2.2. Approximate Q-learning
     2.3. Heuristic Search Algorithm A*
3.Capture the Flag Contest
     3.1. Performance table and Graph of our agents in the competitions
4. Final Model
5. Future Improvements


**1.	Introduction**

The Aim of this project is to implement a Pac man Autonomous Agent that can play and compete in a tournament. Our agents where finally developed used A* heuristic graph search techniques and agents were tried to be build using techniques such as MDP with value iteration and Approximate Q Learning. 

**2.Techniques Attempted**
**2.1. MDP With Value Iteration **

We build our agent based on Markov Decision Processes which used to find the optimal policy using value iterations algorithm. To build our model we created a grid of specific size and assigned rewards at specific positions in the grid according to their location and their properties like whether they carrying food or where they carrying capsule etc. 

**2.1.1. Strategies Used ** 

•	To start we created a grid of specific width and length and the transitional probabilities where defined as being 1 if the action is legal and where considered as being 0 if the action of illegal. 
•	We initialised a Q-value with all cells containing values zeroes. 
•	Then we initialised different weights to different cells in the grid like more weights were given to the cell having food pellets and negative weights were given to the cell containing ghosts and the neighbouring cells of the ghosts also got negative rewards. 
•	Then using the value iteration with Bellman equation at each state we found the values and chose the best action based on those values. 
•	When a ghost enters the opponent’s arena then it assigned less rewards to the cell containing ghosts and more rewards for the cells containing food pellets. 
•	Rewards were also given more to the cells that were closer to the home position of the agent and less rewards were given to the cells that were far from the home position. 
•	 If agent captured certain amounts to pellets then the reward assigned on the cells which were closer to the home boundaries of much higher that any other cell which help the agent in navigating home when enough number of food pellets were eaten. 
•	Discount values between 0.6 and 0.9 were tried to find the discount factor giving the optimal policy. 

**2.1.2. Issues with This Strategy **

•	The agent found it hard to navigate in grid which had to food pellets, or capsules or ghosts, that is which had less rewards. So, we had to guide the agent using A* to cells where he can numerous cells with rewards that can help him find a good action.
•	The agent found it hard to figure out alternative paths to goal and stuck to only path that made him get stuck in a loop. 
•	We faced the issue of determine the optimal grid size that can help the agent take the best possible action because choosing a bigger grid size was making the agent take more than one second to select the action and making the grid size smaller was making the agent weak against teams having strong defensive agents.

**2.1.3. Advantages of MDP **

•	It can be used for Q-learning, SARSA or n-step TD Learning

**2.1.4. Disadvantages of MDP**

•	The most difficult part of this approach is assigning the rewards. 

**2.2. Approximate Q-learning:**
 **2.2.1. Strategies Used**
•	The approach was similar to the baseline team’s approach as we tried to get the best action according the set of features and weights. 
•	The model was not able to learn the weights properly. We tried changing the discount factor and the learning rate to observe agent’s performance. 
•	We tried to implement a greedy agent whose goal was to have as many food pellets as it can.
**2.2.2. Issues With this Strategy**
•	Even at the lower learning rates the model was not able to learn the weights properly and the weights usually converged to the weights that were assigned in the beginning. 
•	It performed poorly against team which had a strong defence and the performance of the agent declined in restricted layouts.
•	Low performance of this technique forced us to use some other technique to achieve high performance in the tournament. 
•	The inability of this technique to learn the weights properly was probably due to lack of efficient reward shaping
**2.2.3 Reward shaping**
•	We tried to assign rewards in a similar way as we did in MDP approach. High rewards were given to the agent eating the food and even higher if agent was evading the ghost agent.
**2.2.4. Reward types:**
•	Food pellets were given high rewards when the ghost was not nearby and was given lesser rewards when the ghost was near to the Pacman 
•	Negative rewards were given the cells which lead to the ghost and the cells around the ghost were also assigned some negative rewards
•	High rewards were given to the power capsules 
•	The which were nearer to the home boundary were given higher rewards than the cells which were farther, this helped the agent in navigating home after collecting certain amount of food pellets. 

**2.3. Heuristic Search Algorithm**

We have adopted concepts from Heuristic Search algorithms a agent using A* search.

**2.3.1. Offensive Agent Strategy**

•	The agent takes the data of the opponent’s side and chooses its action using the data gathered. Using the data of the game state if figures out the state of the enemy, whether it is observable or not, how many food pellets are left, how far is the nearest enemy, what is the scared timer of the enemy etc. 
•	The heuristic is simple heuristic which calculates the minimum distance from the current state to the goal state.   
•	The action is chosen by the agent is the first action that is returned to the goal to state. 
•	The states which leads to ghosts have high rewards and high rewards have also been set to states in which the distance between both the agents of the team is less, this is done to ensure some distance between the agents. 
•	If the enemy is nearby and there is a capsule nearby then the goal of the agent shifts to the capsules position and the agent goes in the that direction.
•	If there is no capsule to grab, then the agent again shifts the goal to the home boundary and runs there while avoiding all the ghosts agents. 



**2.3.2. Defensive Agent Strategy**
•	Our defensive agent was also based on the same A* heuristic search with same heuristic and cost function.
•	It changed it goal to the Pacman position when it was observable otherwise the goal of the agent was the boundary line between the two states 
**2.3.3. Issues**
•	The offensive still went to places having only one entry and exit point without any capsule and got stuck. 
•	The agents were not very effective against enemies having strong defence.
•	In order to keep a safe distance with the ghosts, the Pacman sometimes got stuck in the same place. 

**2.3.4. Improvements **

•	In order to improve the performance of our agents we made the defensive agent as being an agent which can turn offensive when there is no invader or if all the enemies are scared.
•	Also, we decided to make the defensive agent offensive when there it is scared 
•	To improve the tracking abilities of our defence agent it changed its goal to the latest food pellet eaten by the opponent.


After implementing these improvements, we figured out that our performance increased, and we decided to keep these agents as our final agents



**4. Final Model**
    4.1 . A* based Offensive and Defensive Agents
•	To improve the performance of our team in the tournament, we came up with a graph search-based algorithm, A*. 
•	We created both the agents using A* algorithm with appropriate heuristics and cost function. 
•	The strategy that we used to create an effective team was that we made both the agents attacking and defensive, that is we made them switchable according to the environment.
•	We made them change the goals according to different situations.
•	We developed a cost function which assigned higher costs to the paths which led to ghosts in the attacking zone and lower costs to paths which where free of ghosts. 
•	We defined different scenarios in which our agent decided to attack or defend


**4. Future Improvements**

•	MDP can lead to much better results if the rewards are assigned correctly. We tried to implement different rewards assigning strategies like a few exponential approaches rather than linear approach but due to shortage of time we were not able to explore all of them. Exponential reward shaping could lead to better results with less ambiguity. 
•	In A* the heuristic is really simple and efficient, if we had more time we would have worked on building a efficient heuristic and also an efficient cost function to help improve the search results. 
•	Less computationally expensive search algorithms can also be used in place of A*. One alternative method is using Monte Carlo Tree Search. 



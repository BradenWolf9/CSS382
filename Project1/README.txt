1. For question 1, I mainly followed the pseudo-code for the graph-search. Later I switched 
   my closed set to a closed list, but I will talk about that in question 5. 

   For the fringe I used a stack. After popping the node from the fringe I also extract the 
   state, action, and cost of the node to variables to be used in the 'for child-node in 
   EXPAND' loop, but I only use the action. In that for loop, after getting the child node, 
   I extract the child state, action, and cost. I then append the child action to the end 
   of the original node action as an array and save that as the child action. Doing this 
   will result in actions being stored as an array, and the final node to the solution 
   having all the actions. In the for loop I then put the child state, new action, and cost 
   back in the child node and push the child node to the fringe.

2. For question 2, with breadth first search I used the same code as DFD, but I used a queue
   as the fringe instead of a stack.

3. For question 3, varying the cost function, I similar code as from the DFS for my uniform 
   cose search, but I used a priority queue instead of a stack. Additionally, when pushing
   onto the fringe, I included the priority which was the total cost of the state. For the 
   first state the total cost was 0. For future states, the total cost was calculated in 
   the 'for child-node in EXPAND' loop. The original node cost was added to the child node 
   cost to create the total cost. This total cost was saved as the child node cost and pushed
   onto the fringe with the priority also being the total cost. 

4. For question 4, I basically copied my code from ucs to A*. However, I added in
   calculating the heuristic for each child, then adding that to the total cost, then that 
   new sum would be pushed in the fringe as the priority.

5. For question 5, I had to make some changes to my existing search algorithms.
   Instead of using a set for closed in each of my search algorithms, I ended
   up using a list. For this problem I stored my state as
   ((x,y),bool array), with the bool array representing the 4 corners, and when I tried to 
   add that to the set I got an unhashable type error. Once pacmand got to a corner, the 
   bool representing that corner got flipped to True.

6. For question 6, I chose my heurisitc to be the max of the manhattan distances from 
   pacmans current location to a corner that had not been visited.

7. For question 7, I used the mazeDistance function to calculate the distance from pacman
   to each food pellet and then used the max distance as the heuristic. Additionally, to 
   reduce run time from about 20 seconds to about 1 second, I saved those calculated 
   distances in the problem.heuristicInfo dictionary. This way if pacmans returns to a 
   position it has already visited, it can use the dictionary to get the distance instead of
   calculating it again through the mazeDistance function.

8. For question 8, I used the euclidean distance to find the closest food to pacman. I then
   called the ucs function to get the path to that food. I ended up implementing isGoalState,
   getSuccessors, and getStartState in the ClosestDotSearchAlgorithm class, only to find out 
   that AnyFoodSeachProblem class was set up for that. 
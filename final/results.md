# The output and correctness of each algorithm:

Traversal: The traversal method that we chose to implement was BFS, which can be found in /code/src/adjacency_list.cc. Our BFS method traverses from the root node to each node in our dataset and thus can be used to inefficiently calculate the shortest path between all nodes and the root node. One claim we wanted to investigate in our project was whether all humans really do have no more than 6 degrees of separation between them. Our BFS method allows us to explore this by calculating the shortest path between the starting node that is passed through and all of the other nodes in the data set. When looking at the output, it is visually evident that the degrees of separation never go above 6. In this method, we also have a print statement that prints if and only iff the degrees of separation go above 6, so that we can run BFS on a node to see if the claim fails. \
\
We tested this method by asserting that the size of the vector that is returned should always equal 4039 since that is the number of nodes that is present in our dataset, and any time we call BFS it should be comparing that starting node to the rest of the data set, thus always returning a vector of size 4039. \
\
The vectors of all the degrees of separation from the tested starting nodes can be found in results/BFS.jpeg.This output from our BFS method displays that the method works by showing that each node is eventually visited.
\
Covered Method: The covered method that we implemented was Prim’s algorithm, which can be found in /code/src/adjacency_list.cc. The purpose of Prim’s algorithm is to find the minimum spanning tree for a weighted undirected graph. All relationships between Facebook friends are equal so they are unweighted, which we solved by assigning all of the edges with an edge weight of 1. \
\
We tested this method by testing one of the helper methods that is called in the function, ‘inMST’. We tested inMST because it ensures that the disjoint set that the algorithm is calculating remains acyclic, and once a cycle is present the code stops running, which is a key part of calculating the minimum spanning tree.We tested this method by testing one of the helper methods that is called in the function, ‘inMST’. We tested inMST because it ensures that the disjoint set that the algorithm is calculating remains acyclic, and once a cycle is present the code stops running, which is a key part of calculating the minimum spanning tree. \
\
Uncovered Method: The uncovered method we chose to implement was a* algorithm, which can be found in /code/src/adjacency_list.cc. A* algorithm is a search algorithm that finds the shortest path between a start node and a destination node. This method is key in investing our claim on degrees of separation because if the claim is true, then any two given nodes that are inputted should result in a shortest path that is less than a length of 6. This method returns the degrees of separation between two inputted nodes, which also helps us explore the connection between two facebook user’s because we can see if they are “friends,” or “friends of friends” and so forth. \
\
We tested this method by asserting that certain nodes had certain degrees of separation that we validated through our inputted csv. For example, if there is a direct edge between node 0 and node 1, we asserted that the degrees of separation between these two nodes were 1. We did this for a few different nodes of varying degrees of separation. \
\
The distances between the tested nodes and our passing test cases from A* can be found in results/A*.png

# The answer to the leading question:

Our leading question is the following: What can we discover about the interconnectedness of humans using a dataset that describes Facebook users and their networks? Specifically, we wanted to investigate the theory of 6 Degrees of Separation, which states that “any person on the planet can be connected to any other person on the planet through a chain of acquaintances that has no more than five intermediaries” (Kirvan, WhatIs.com). We chose data from Facebook to look at these connections between people in order to answer this question, and we did so because Facebook is a common platform that would accurately represent the degrees of separation through “friending.” One algorithm we chose to evaluate our claim was A* algorithm. The reason we chose this is because our method returns the shortest path between a starting node and an ending node, essentially returning the degrees of separation between these two inputted nodes. While we could have used Dijkstra’s algorithm to find the shortest path between a given node and all of the other nodes in the graph, we wanted our algorithm to be more specific so that it only found the shortest path between two user’s, making A* a more appropriate choice. \
\
We also used BFS to explore this claim, by altering our BFS to also update a vector that keeps track of the shortest path between the source node and all other nodes in the graph. This essentially makes our BFS method function like a normal BFS method but also returning the same output as Dijkstra’s which we made just to help us strengthen our proof of the claim. \
\
After running A* on randomly selected nodes in our dataset, we have not been able to find any degrees of separation that are over 6, but this did not fully validate the theory that we were testing, as a select few tests were not comprehensive of the full dataset. We decided to create a method that fully proves our theory by creating a method that calls A* on every node compared to all other nodes in the dataset, and returning “More than 6 degrees of separation” if this was found. When we ran this on our whole dataset we had no output, meaning that the Facebook dataset that we were investigating does in fact satisfy the theory of 6 degrees of separation. \
\
We thought that this idea of degrees of separation was really interesting to investigate, and while using A* algorithm may not have been the best way to effectively prove that our whole dataset follows this theory, it does provide really interesting insights into people’s individual connections. Our algorithm can be used to find if people have any connections between each other, and also to discover how many intermediate connections people have between them.
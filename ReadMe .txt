USING SCILAB:


The visibility graph for a set of obstacles. 

We will be using the various Vision functions present in the NARVAL to generate a visibility graph which is a graph of intervisible locations, typically for a set of points and obstacles in the Euclidean plane.
Visibility graphs may be used to find Euclidean shortest paths among a set of polygonal obstacles in the plane: the shortest path between two obstacles follows straight line segments except at the vertices of the obstacles, where it may turn, so the Euclidean shortest path is the shortest path in a visibility graph that has as its nodes the start and destination points and the vertices of the obstacles. 

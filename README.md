# NODE-DETECTOR-FROM-OBSTACLE-VISUALIZATION-THROUGH-NARVAL=>

Using Scilab , The visibility graph for a set of obstacles.Using the various Vision functions present in the NARVAL to generate a visibility graph which is a graph of intervisible locations.


Visibility graph=>

The visibility graph of a simple polygon has the polygon's vertices as its point locations, and the exterior of the polygon as the only obstacle. Visibility graphs of simple polygons must be Hamiltonian graphs: the boundary of the polygon forms a Hamiltonian cycle in the visibility graph. It is known that not all visibility graphs induce a simple polygon. In fact, visibility graphs of simple polygons do not possess the characteristics of a few special classes of graphs.

Vision Functions (present in NARVAL)=>

They are focusing on computer vision. It is related NL_M because it was originally designed to compute the path of mobile nodes in non-free space where obstacles are present. After the definition of obstacles, the user can determine the path that a node needs to follow in order to move from an original position to a specific destination. Calculations are done in respect with computer vision algorithms (Moravec, Potential Field and Visibility graph). This realistic mobility model is currently under studies and new models will be released in the next update of the NARVAL module.

Introduction:
To performing the visibility graph of different sets of obstacles varying in various factors like 

1)	The number of obstacles
2)	Height and width of the obstacles
3)	Zoom factor of contour performance
4)	Kernel size of  NL_V_Moravec function 
5)	Threshold Values of NL_V_Moravec function
6)	Parameters of NL_V_ContourCornersFilt function


Requirements=>

1) Scilab
2) Sublime Text Editor 

Proposed Architecture=>

Using these vision functions in order to generate the visibility graph of obstacles:

1)  NL_V_ContourCorners — Extract the corners of an obstacle contour.
2)  NL_V_ContourCornersFilt — Extract the corners of an obstacle contour (false detection removal).
3)  NL_V_Convolution2D — Perform the 2D convolution of a kernel on an image.
4)  NL_V_DistanceMapObject — Perform the distance map between an object and its contour.
5)  NL_V_Erosion — Perform the morphological erosion operation on a binary image.
6)  NL_V_MRA — Perform a scale modification on a matrix (Multi Resolution Analysis).
7)  NL_V_Moravec — Perform the Moravec corner detection algorithm on an image.
8)  NL_V_MoravecFilter — Apply a specific threshold on the Moravec corner detection algorithm.
9)  NL_V_PotentialField — Perform the potential field of an obstacle.
10) NL_V_PotentialFieldPath — Perform the path between two pixels in respect with a potential field (obstacles).
11) NL_V_PotentialRectangles — perform the potential matrix of obstacles defined by rectangles.
12) NL_V_RectangleCorners — generate the coordinates of the corners of a rectangle (obstacle).
13) NL_V_RectanglesCorners — generate the coordinates of corners of rectangles (obstacles).
14) NL_V_RectanglesCornersA — Generate the coordinates of the corners of rectangles (obstacles) in respect with a set of defined angles.
15) NL_V_VisibilityGraph — Perform the visibility graph of a set of obstacles.



Abstract=>

Our aim is to perform the visibility graph for a set of obstacles.Using the various Vision functions present in the NARVAL to generate a visibility graph which is a graph of intervisible locations, typically for a set of points and obstacles in the Euclidean plane.
Visibility graphs may be used to find Euclidean shortest paths among a set of polygonal obstacles in the plane: the shortest path between two obstacles follows straight line segments except at the vertices of the obstacles, where it may turn, so the Euclidean shortest path is the shortest path in a visibility graph that has as its nodes the start and destination points and the vertices of the obstacles. 

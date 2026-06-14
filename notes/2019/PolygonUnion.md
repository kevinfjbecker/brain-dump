# Polygon Union

Given two polygons:

POLYGON((1 0, 1 8, 6 4, 1 0))
POLYGON((4 1, 3 5, 4 9, 9 5, 4 1),(4 5, 5 7, 6 7, 4 4, 4 5))
How can I calculate the union (combined polygon)?

Dave's example uses SQL server to produce the union, but I need to accomplish the same in code. I'm looking for a mathematical formula or code example in any language that exposes the actual math. I am attempting to produce maps that combine countries dynamically into regions. I asked a related question here: Grouping geographical shapes

This is a very good question. I implemented the same algorithm on c# some time ago. The Algorithm constructs a common contour of two polygons (i.e. Constructs a union without holes). Here it is.

Goal

Step 1. Create graph that describes the polygons.
Input: first polygon (n points), second polygon (m points). Output: graph. Vertex - polygon point of intersection point.

We should find intersections. Iterate through all polygon sides in both polygons [O(n*m)] and find any intersections.

If an intersection is not found, simply add vertices and connect them to the edge.

If any intersections are found, sort them by length to their start point, add all vertexes (start, end and intersections) and connect them (already in sorted order) to the edge. Graph

Step 2. Check constructed graph
If we did not find any intersection points when graph was built, we have one of the following conditions:

Polygon1 contains polygon2 - return polygon1
Polygon2 contains polygon1 - return polygon2
Polygon1 and polygon2 do not intersect. Return polygon1 AND polygon2.
Step 3. Find left-bottom vertex.
Find the minimum x and y coordinates (minx, miny). Then find the minimum distance between (minx, miny) and the polygon's points. This point will be the left-bottom point.

Left-bottom point

Step 4. Construct common contour.
We start to traverse the graph from the left-bottom point and continue until we get back into it. At the beginning we mark all edges as unvisited. On every iteration you should select the next point and mark it as visited.

To choose the next point, choose an edge with a maximum internal angle in counter-clockwise direction.

I calculate two vectors: vector1 for current edge and vector2 for each next unvisited edge (as presented in the picture).

For vectors I calculate:

Scalar product (dot product). It returns a value related to an angle between vectors.
Vector product (cross product). It returns a new vector. If z-coordinate of this vector is positive, scalar product gives me right angle in counter-clockwise direction. Else (z-coordinate is negative), I calculate get angle between vectors as 360 - angle from scalar product.
As a result I get an edge (and a correspond next vertex) with the maximum angle.

I add to result list each passed vertex. Result list is the union polygon. Vectors

Remarks
This algorithm allows us to merge multiple of polygons - to apply iteratively with polygon's pairs.
If you have a path that consists of many bezier curves and lines, you should flatten this path first.

src: <https://stackoverflow.com/questions/2667748/how-do-i-combine-complex-polygons#>

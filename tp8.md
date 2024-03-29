---
layout: geonum2017
title: "TP8 : Uniform B-splines as Subdivision Surfaces"
date:   2017-03-31
#permalink: /teaching/geo-num-2017/tp8.html
---

## Code
* [TP8 on github](https://github.com/GeoNumTP/GeoNum2017/tree/master/TP8)  
* [general instructions](https://github.com/GeoNumTP/GeoNum2017#géométrie-numérique-spring-2017)  

## Algorithm
Much like in the curve case (recall [Chaikin in TP4](tp4.html) or [Lane-Riesenfeld in TP5](tp5.html)),
a uniform bi-quadratic B-spline surface ($k=2,l=2$) can be evaluated by iterative subdivision
of the initial control net $V^0_{i,\;j}$. Here's the algorithm to perform one step of the subdivision.

At the $k$-th iteration, for each cell of the grid composed of the vertices
$V^k_{i,\;j}$
$V^k_{i+1,\;j}$
$V^k_{i,\;j+1}$
$V^k_{i+1,\;j+1}$
we define a new grid as follows

$$
\begin{array}{ll}
 V^{k+1}_{2i,\;2j}     &= \frac1{16} \left( 9V^k_{i,\;j} + 3V^k_{i+1,\;j} + 3V^k_{i,\;j+1} + 1V^k_{i+1,\;j+1} \right), \\
 V^{k+1}_{2i+1,\;2j}   &= \frac1{16} \left( 3V^k_{i,\;j} + 9V^k_{i+1,\;j} + 1V^k_{i,\;j+1} + 3V^k_{i+1,\;j+1} \right), \\ 
 V^{k+1}_{2i,\;2j+1}   &= \frac1{16} \left( 3V^k_{i,\;j} + 1V^k_{i+1,\;j} + 9V^k_{i,\;j+1} + 3V^k_{i+1,\;j+1} \right), \\ 
 V^{k+1}_{2i+1,\;2j+1} &= \frac1{16} \left( 1V^k_{i,\;j} + 3V^k_{i+1,\;j} + 3V^k_{i,\;j+1} + 9V^k_{i+1,\;j+1} \right). 
\end{array}
$$

**Important**: If the surface is closed (cyclic) in the direction $u$, the subscripts $\scriptstyle i+1$ of $V^k$ are taken modulo the number of vertices in the direction $u$. The same applies for the direction $v$ and the subscripts $\scriptstyle j+1$.

{:.img3grid}
![open 1](/assets/geonum/tp8/open/1.png)
![open 2](/assets/geonum/tp8/open/2.png)
![open 3](/assets/geonum/tp8/open/3.png)

{:.imgCaption}
A subdivision step, open surface.

{:.img3grid}
![closed 1](/assets/geonum/tp8/closed/1.png)
![closed 2](/assets/geonum/tp8/closed/2.png)
![closed 3](/assets/geonum/tp8/closed/3.png)

{:.img3grid}
![closed 4](/assets/geonum/tp8/closed/4.png)
![closed 5](/assets/geonum/tp8/closed/5.png)

{:.imgCaption}
A subdivision step, surface closed in the $u$ direction.

## ToDo

{:.assignements}
1. Implement one step of the above subdivision algorithm for **closed** uniform B-spline surfaces (`torus`).
2. Modify you implementation for surfaces which are **open**: either in one direction (`cylinder`) or in both directions (`grid`, `terrain`).
3. Experiment with parameters in `GenerateRandomTerrain()`.
4. [*bonus*] [Catmull–Clark subdivision scheme](https://en.wikipedia.org/wiki/Catmull%E2%80%93Clark_subdivision_surface) produces bicubic B-spline surfaces.  Although originally devised for quad-meshes with arbitrary topology, it work as well for uniform topologies (the ones we use in this TP). Implement this algorithm and compare the results with biquadratic surfaces. For more details of the algo, see the [wikipedia page](https://en.wikipedia.org/wiki/Catmull%E2%80%93Clark_subdivision_surface) and also [this article](http://www.rorydriscoll.com/2008/08/01/catmull-clark-subdivision-the-basics/).

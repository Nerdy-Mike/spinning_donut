
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## How it works?

For detailed explaination, please visit : <a href="https://www.a1k0n.net/2011/07/20/donut-math.html">Donut Math</a>

Overview Strategy: 
### 1 - How to render 3D object to 2D screen 

<div style="display:flex; justify-content:center">
<img src="https://www.a1k0n.net/img/perspective.png" alt="Render 3D object on 2D screen">
</div>

### 2 - Create a donut, which is a [solid of revolution](https://en.wikipedia.org/wiki/Solid_of_revolution)
<br/>

<div style="display:flex; justify-content:center">
<img src="https://www.a1k0n.net/img/torusxsec.png" alt="Solid of revolution">
</div>
<br/>

<p>\[
(x,y,z) = (R_2,0,0) + (R_1 \cos \theta, R_1 \sin \theta, 0) = (R_2 + R_1 \cos \theta, R_1 \sin \theta, 0)
\]</p>

We have had a circle, next step is to rotate it around y-axis by angle ϕ ( 0 < ϕ < 2π) using [rotation matrix](https://en.wikipedia.org/wiki/Rotation_matrix) 

### 3 - Rotate about x-axis and z-axis
<img src="https://i.ibb.co/VDYQfhB/1.png" alt="1" border="0">
<br>

### 4 - Illumination
We will set the light behind and above viewer: (0,1,-1) - light direction.
To calculate illumination, we need to know the [surface normal](https://en.wikipedia.org/wiki/Normal_(geometry)) of each point. Then we can take the [dot product](https://en.wikipedia.org/wiki/Dot_product) between the point and light direction.

The fomula of surface normal for each point is similar to the above
\begin{aligned}
L &amp;=
\left( \begin{matrix}
N_x, &amp;
N_y, &amp;
N_z \end{matrix} \right)
\cdot
\left( \begin{matrix}
0, &amp;
1, &amp;
-1 \end{matrix} \right)
\\
&amp;= 
\cos \phi \cos \theta \sin B - \cos A \cos \theta \sin \phi - \sin A \sin \theta + 
 \cos B ( \cos A \sin \theta - \cos \theta \sin A \sin \phi)
\end{aligned}
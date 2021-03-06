---
keywords: fastai
title: Matrices Revisited
nb_path: _notebooks/2021-07-11-Matrices revisited.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2021-07-11-Matrices revisited.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Norm">Norm<a class="anchor-link" href="#Norm"> </a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Norm is a function which when applied, gives a measure of distance-ness from the origin, or the size of the <strong>vector</strong>. This function has the following properties</p>
<p>{% raw %}
$$f(x) = 0 \text{ then } x = 0 \tag{1}$$
{% endraw %}</p>
<p>{% raw %}
$$f(x+y) \leq f(x) + f(y) \cdots \text{ Triangle Inequality} \tag{2}$$
{% endraw %}</p>
<p>{% raw %}
$$f(\alpha x) = |\alpha| f(x) \text{  } \forall \alpha \in \mathbb{R} \tag{3}$$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Examples of Norm are,</p>
<p>{% raw %}
$$||x||_p = \left(\sum_i |x_i|^p\right)^\frac{1}{p} \tag{$L^p$ Norm}$$
{% endraw %}</p>
<p>When $p = 2$, we have $L^2$ norm, also known as Euclidean norm. For practical purposes we use squared $L^2$ norm.
{% raw %}
$$||x||_p = \sum_i |x_i|^2$$
{% endraw %}</p>
<p>However, when when we are working with values near $0$, a change of $\epsilon$ will cause the squared $L^2$ norm to change by $\epsilon^2$, which will be very small. Thus we can use $L^1$ norm in those cases.</p>
<p>{% raw %}
$$||x||_1 = \sum_i |x_i| \tag{$L^1$ Norm}$$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Orthogonal-matrices">Orthogonal matrices<a class="anchor-link" href="#Orthogonal-matrices"> </a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Properties of orthogonal matrices</p>
<ul>
<li>They must be square</li>
<li>Rows are mutually orthonormal</li>
<li>Columns are mutually orthonormal</li>
</ul>
<blockquote><p>Two vectors $x$ and $y$ are <strong>orthonormal</strong> if their dot product is 0 and they have unit norm.</p>
</blockquote>
<p>As a result of the definition, the below property follows for any orthogonal matrix $A$,</p>
<p>{% raw %}
$$A^T A = A A^T = I$$
{% endraw %}</p>
<p>{% raw %}
$$A^{-1} = A^T$$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Multiplying-with-orthogonal-matrices-leads-to-rotation">Multiplying with orthogonal matrices leads to rotation<a class="anchor-link" href="#Multiplying-with-orthogonal-matrices-leads-to-rotation"> </a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To prove that multiplying with an orthogonal matrix leads to a rotation, we need to prove two things,</p>
<ul>
<li>The length/norm of the vector is preserved after matrix operation.</li>
<li>The angles between vectors are preserved after matrix operation.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Length-is-preserved">Length is preserved<a class="anchor-link" href="#Length-is-preserved"> </a></h4><p>Let $c$ be an orthogonal matrix, then the squared norm of the transformed vector is as follows,
{% raw %}
$$||c \vec{x}||^2$$
{% endraw %}</p>
<p>{% raw %}
$$= c \vec{x} \cdot c \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= (c \vec{x})^T c \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= \vec{x}^T c^T c \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= \vec{x}^T I \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= \vec{x}^T \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= \vec{x} \cdot \vec{x}$$
{% endraw %}</p>
<p>{% raw %}
$$= || \vec{x} ||^2$$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Angle-between-vectors-is-preserved">Angle between vectors is preserved<a class="anchor-link" href="#Angle-between-vectors-is-preserved"> </a></h4><p>Let $\vec{v}$ and $\vec{w}$ be two vectors and let $\theta$ be the angle between them.</p>
<p>{% raw %}
$$\therefore \text{ } \cos \theta = \frac{\vec{v} \cdot \vec{w}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>Let $\theta_c$ be the angle between the rotated vectors.</p>
<p>{% raw %}
$$\therefore \text{ } \cos \theta_c = \frac{C\vec{v} \cdot C\vec{w}}{||C\vec{v}||\text{ }||C\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ = \frac{(C\vec{w})^T C\vec{v}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ = \frac{\vec{w}^T C^T C\vec{v}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ = \frac{\vec{w}^T I \vec{v}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ = \frac{\vec{w}^T \vec{v}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ = \frac{\vec{v} \cdot \vec{w}}{||\vec{v}||\text{ }||\vec{w}||}$$
{% endraw %}</p>
<p>{% raw %}
$$ \cos \theta_c = \cos \theta $$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Eigen-vectors-and-Eigen-values">Eigen vectors and Eigen values<a class="anchor-link" href="#Eigen-vectors-and-Eigen-values"> </a></h2><p>For a matrix $A$, a vector $x$ and some scalar constant $\lambda$, we can have an equation as below,</p>
<p>{% raw %}
$$A x = \lambda x$$
{% endraw %}</p>
<p>Here, $x$ becomes the eigen vector and $\lambda$ its corresponding eigen value.</p>
<p>To get an intuition for this equation, we can start by thinking of a matrix multiplication on a vector as application of a function that leads to a transformation in the space. This space in which the transformation take place will have few axes (imaging $x$, $y$ and $z$, however more than three are possible). The transformation by the matrix $A$ can be decomposed into sub-transformations along these axes. That scaling factor $\lambda$ is called the eigen value.</p>
<p>Let us assume a vector $\vec{v}$ along the axes $x$ ($x$ from the equation above). Now, the dot product of $\vec{v}$ will cancel out with all the other axes except $x$. Thus the scaling (transformation) will happen only in the direction of $x$ axes.</p>
<blockquote><p>"Cancels out" is a crude term which holds only for matrices whose eigen vectors are orthogonal (see below). Let us assume that the transformation is quantified by an array with each value as a metric of change in the axes other than $x$, then we have chosen the case for other axes as say $[0, 0, 0, 0, 0]$, which could well be $[-1, 2, -3, 4, -2]$ where sum of both the arrays is 0, but the former is easier to visualize.</p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Eigen-vectors-of-a-symmetric-matrix-are-orthogonal">Eigen vectors of a symmetric matrix are orthogonal<a class="anchor-link" href="#Eigen-vectors-of-a-symmetric-matrix-are-orthogonal"> </a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let $A$ be a symmetric matrix with $x$ and $y$ as two of its eigen vectors and $\lambda_1$ and $\lambda_2$ be distinct and corresponding eigen values.</p>
<p>{% raw %}
$$\therefore \text{ } A x = \lambda_1 x  \tag{1}$$
{% endraw %}
Multiplying both sides on left with $y^T$
{% raw %}
$$\therefore \text{ } y^T A x = \lambda_1 y^T x$$
{% endraw %}
Taking transpose on both sides,
{% raw %}
$$\therefore \text{ } \left(y^T A x\right)^T = \lambda_1 \left(y^T x\right)^T$$
{% endraw %}</p>
<p>{% raw %}
$$\therefore \text{ } x^T A^T y = \lambda_1 x^T y$$
{% endraw %}
Since $A$ is symmetric, we have $A = A^T$
{% raw %}
$$\therefore \text{ } x^T A y = \lambda_1 x^T y \tag{2}$$
{% endraw %}</p>
<p>Also,
{% raw %}
$$\therefore \text{ } A y = \lambda_2 y  \tag{3}$$
{% endraw %}
Multiplying both sides on left with $x^T$
{% raw %}
$$\therefore \text{ } x^T A y = \lambda_2 x^T y \tag{4}$$
{% endraw %}
Subtracting $(4)$ from $(2)$ we get,
{% raw %}
$$x^T y \cdot (\lambda_1 - \lambda_2) = 0$$
{% endraw %}
Since $\lambda_1 \neq \lambda_2$ , we have,
{% raw %}
$$x^T y = 0$$
{% endraw %}</p>
<p>This implies that $y \cdot x = 0$ or that $x$ and $y$ are orthogonal vectors.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Eigen-Decomposition">Eigen Decomposition<a class="anchor-link" href="#Eigen-Decomposition"> </a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let $V = [\vec{V_1}, \vec{V_2}, \cdots , \vec{V_n}]$ be the $n$ eigen vectors of a matrix $A$. Also, let $\lambda_1, \lambda_2, \cdots , \lambda_n$ be the $n$ eigenvalues.</p>
<p>{% raw %}
$$V = [\vec{V_1}, \vec{V_2}, \cdots , \vec{V_n}]$$
{% endraw %}</p>
<p>Multiplying  by matrix $A$,
{% raw %}
$$\therefore A V = A [\vec{V_1}, \vec{V_2}, \cdots , \vec{V_n}]$$
{% endraw %}</p>
<p>{% raw %}
$$\therefore A V = [A\vec{V_1}, A\vec{V_2}, \cdots , A\vec{V_n}]$$
{% endraw %}</p>
<p>Using eigenvector's property $A \vec{V_i} = \lambda_i \vec{V_i}$,
{% raw %}
$$\therefore A V = [\lambda_1 V_1, \lambda_2 V_2, \cdots , \lambda_n V_n]$$
{% endraw %}</p>
$$\therefore A V = [V_1, V_2, \cdots , V_n] \cdot 
\begin{bmatrix}
    \lambda_1 &amp; 0 &amp; \cdots &amp; 0 \\
    0 &amp; \lambda_2 &amp; \cdots &amp; 0 \\
    \vdots &amp; \vdots &amp; \cdots &amp; \vdots \\
    0 &amp; 0 &amp; 0 &amp; \lambda_n
\end{bmatrix}
$$<p>{% raw %}
$$\therefore A V = V \text{ } diag(\lambda)$$
{% endraw %}</p>
<p>{% raw %}
$$\therefore A V V^{-1} = V \text{ } diag(\lambda) \text{ } V^{-1}$$
{% endraw %}</p>
<p>{% raw %}
$$\therefore A = V \text{ } diag(\lambda) \text{ } V^{-1}$$
{% endraw %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Eigen-decomposition-of-symmetric-matrices">Eigen decomposition of symmetric matrices<a class="anchor-link" href="#Eigen-decomposition-of-symmetric-matrices"> </a></h3><p>From the discussion above, we know that eigenvectors of symmestric matrices are orthogonal. We also discussed that for an orthogonal matrix $V$, $V V^{T} = I$, that is $V^{-1} = V^{T}$.</p>
<p>Continuing the above equation of eigen decomposition we have,
{% raw %}
$$A = V \text{ } diag(\lambda) \text{ } V^{-1}$$
{% endraw %}</p>
<p>When $A$ is symmetric, its eigenvectors $V$ are orthogonal,
{% raw %}
$$\therefore A = V \text{ } diag(\lambda) \text{ } V^{T}$$
{% endraw %}</p>

</div>
</div>
</div>
</div>
 


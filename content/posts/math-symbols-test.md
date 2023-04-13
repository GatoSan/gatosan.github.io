+++
title = "Math Symbol Support Test"
date = "2023-01-06"
+++

# Inline Math

-   $(a+b)^2$ = $a^2 + 2ab + b^2$
-   A polynomial P of degree d over $\mathbb{F}_p$ is an expression of the form
    $P(s) = a_0 + a_1 . s + a_2 . s^2 + ... + a_d . s^d$ for some
    $a_0,..,a_d \in \mathbb{F}_p$

# Displayed Math

$$
p := (\sum_{k∈I}{c_k.v_k} + \delta_v.t(x))·(\sum_{k∈I}{c_k.w_k} + \delta_w.t(x)) − (\sum_{k∈I}{c_k.y_k} + \delta_y.t(x))
$$

# A more complex example

$$
\sum_{i=1}^{N_K}{\begin{bmatrix}
\left(\frac{\partial_R \mathbf{v}_s}{\partial \dot{\mathbf{s}}} \right)^T &
\left( \frac{\partial_R \mathbf{\omega}_s}{\partial \dot{\mathbf{s}}} \right)^T
\end{bmatrix}_i \begin{bmatrix}
_R\dot{\mathbf{p}} + _R\tilde{\mathbf{\omega}}_{IR}\,_R\mathbf{p}-_R\mathbf{f}^e \\
_R\dot{\mathbf{L}} + _R\tilde{\mathbf{\omega}}_{IR}\,_R\mathbf{L}-_R\mathbf{M}^e 
\end{bmatrix}_i}=0
$$

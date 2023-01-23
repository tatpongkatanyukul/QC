Nielsen and Chuang's Quantum Computation and Quantum Information

See [write math in git](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
* In short, use ```$``` for inline math, ```$$``` for block 
  * or use back-tick math, i.e.,  ```\`math```
  * E.g.,
```
\```math
i \bar{h} \frac{\partial |\psi(t)>}{\partial t} = \hat{H} |\psi(t)>
\```
```
will be rendered as 

```math
i \bar{h} \frac{\partial |\psi(t)>}{\partial t} = \hat{H} |\psi(t)>
```
  
# Chapter 2

## 2.1.6 Adjoints and Hermitian operators

Self-adjoint is Hermitian, i.e., if $A = \ket{v} \bra{v}$ then $A = A^\dagger$.

* It is so: consider $\ket{v} = [v_1, v_2, \ldots, v_k]^T$, so $\bra{v} = [v_1^\ast, v_2^\ast, \ldots, v_k^\ast]$.
  * Therefore, 
  $A = \ket{v} \bra{v}$ =
```math  
\begin{equation}
\begin{pmatrix}
  v_1 v_1^\ast & v_1 v_2^\ast & \cdots & v_1 v_k^\ast \\
  v_2 v_1^\ast & v_2 v_2^\ast & \cdots & v_2 v_k^\ast \\
  \ldots       & \ldots       & \ddots & \ldots \\
  v_k v_1^\ast & v_k v_2^\ast & \cdots & v_k v_k^\ast \\
\end{pmatrix}
\end{equation}
```
which is equal to $(A^T)^\ast$. That is, if $A = \ket{v} \bra{v}$ then $A = A^\dagger$. Q.E.D.


### Exercise 2.16
> Show that any projector $P$ satisfies the equation $P^2 = P$.

Given $P = \sum_i \ket{i} \bra{i}$ (from eq. 2.35) when $\ket{i}$'s are orthonormal bases, thus
$$P^2 = P \cdot P = (\sum_i \ket{i} \bra{i}) \cdot (\sum_j \ket{j} \bra{j})$$.
```math  
\begin{align}
P^2 &= \sum_i \sum_j \ket{i} \braket{i}{j} \bra{j} \\
 &= \sum_i \sum_{j \neq i} \ket{i} \bra{i}\ket{j} \bra{j} + \sum_i \ket{i} \bra{i}\ket{i} \bra{i} \\
 &= \sum_i \sum_{j \neq i} \ket{i} 0 \bra{j} + \sum_i \ket{i} 1 \bra{i} \\
 &= \sum_i \ket{i} \bra{i} = P.\\
\end{align}
```
Q.E.D.

### Exercise 2.17
> Show that a normal matrix is Hermitian if and only if it has real eigenvalues.

Recall all related properties:
* $A$ is a normal matrix if $A A^\dagger = A^\dagger A$.
* $A$ is Hermitian if $A = A^\dagger$.
* Adjoint $A^\dagger = (A^\ast)^T$.
* Eigenvalues
  * Eigenvalues of $A$ are the solutions $\lambda_i$'s of $det | A - \lambda I | = 0$.
  * Any matrix $A = \sum_i \lambda_i \ket{i} \bra{i}$ where $\ket{i}$'s form an orthonormal set of eigenvectors for $A$ with corresponding eigenvalues $\lambda_i$'s.

To clarify, if $A$ is normal, $A$ can be either Hermitian or not.
* If $A$ is Hermitian (Hermitian is always normal: $A = A^\dagger \rightarrow A A^\dagger = A^\dagger A$.

Other handy properties
* $(\ket{w} \bra{v})^\dagger = \ket{w} \bra{v}$. (page 70, Ex. 2.13)
* $(\sum_i a_i A_i)^\dagger = \sum_i a_i^\ast A_i^\dagger$. (page 70, Ex. 2.14, Eq. 2.33)

Given Hermitian, that is
$$A = A^\dagger$

LHS:
$$A = \sum_i \lambda_i \ket{i} \bra{i}$$

RHS:
```math
\begin{align}
A^\dagger &= (\sum_i \lambda_i \ket{i} \bra{i})^\dagger \\
&= \sum_i \lambda_i^\ast (\ket{i} \bra{i})^\dagger \mbox{(from eq. 2.33)} \\
&= \sum_i \lambda_i^\ast \ket{i} \bra{i} \mbox{(from ex. 2.13)} \\
\end{align}
```

To be Hermitian, LHS = RHS, i.e.,

$$A = \sum_i \lambda_i \ket{i} \bra{i} = \sum_i \lambda_i^\ast \ket{i} \bra{i} = A^\dagger$$,
which implies
$$\lambda_i = \lambda_i^\ast$$ for all $i$'s.

Therefore, $\lambda_i$ must be real, so that it is equal to its own conjugate. Q.E.D.

## Paragraph 1, page 71
> ... if $\ket{v_i}$ and $\ket{w_i}$ are any two orthonormal bases, then it is easily checked that the operator $U$ defined by $U \equiv \sum_i \ket{w_i} \bra{v_i}$ is a unitary operator.

Recall
* $U$ is unitary if $U^\dagger U = I$.

Given $U \equiv \sum_i \ket{w_i} \bra{v_i}$,
```math
\begin{align}
U^\dagger U &= (\sum_i \ket{w_i} \bra{v_i})^\dagger (\sum_j \ket{w_j} \bra{v_j}) \\
&= (\sum_i \ket{v_i} \bra{w_i}) \cdot (\sum_j \ket{w_j} \bra{v_j}) \\
&= \sum_i \sum_j \ket{v_i} \bra{w_i}\ket{w_j} \bra{v_j} \\
&= \sum_i \sum_{j \neq i} \ket{v_i} \bra{w_i}\ket{w_j} \bra{v_j} + \sum_i \ket{v_i} \bra{w_i}\ket{w_i} \bra{v_i}\\
&= \sum_i \sum_{j \neq i} \ket{v_i} 0 \bra{v_j} + \sum_i \ket{v_i} 1 \bra{v_i} \;\;\mbox{(orthonormal)}\\
&= \sum_i \ket{v_i} \bra{v_i}\\
\end{align}
```

Since $\ket{v_i}$'s form an orthonormal basis set, $\sum_i \ket{v_i} \bra{v_i} = I$ (from Eq. 2.22). Q.E.D.

### Exercise 2.18
> Show that all eigenvalues of a unitary matrix have modulus 1, that is, can be written in the form $e^{i \theta}$ from some real $\theta$.

Related properties
* unitary property $U^\dagger U = I$.
* Any matrix $A = \sum_i \lambda_i \ket{i} \bra{i}$ where $\ket{i}$'s form an orthonormal set of eigenvectors for $A$ with corresponding eigenvalues $\lambda_i$'s.

Consider $U^\dagger U$.
```math
\begin{align}
U^\dagger U &= (\sum_i \lambda_i \ket{i} \bra{i})^\dagger (\sum_j \lambda_j \ket{j} \bra{j}) \\
&= \sum_i \lambda_i^\ast (\ket{i} \bra{i})^\dagger (\sum_j \lambda_j \ket{j} \bra{j}) \\
&= \sum_i \lambda_i^\ast (\ket{i} \bra{i}) (\sum_j \lambda_j \ket{j} \bra{j}) \\
&= \sum_i \sum_j \lambda_i^\ast  \lambda_j \ket{i} \bra{i} \ket{j} \bra{j} \\
&= \sum_i \sum_{j \neq i} \lambda_i^\ast  \lambda_j \ket{i} \bra{i} \ket{j} \bra{j} + \sum_i \lambda_i^\ast  \lambda_i \ket{i} \bra{i} \ket{i} \bra{i}\\
&= \sum_i \sum_{j \neq i} \lambda_i^\ast  \lambda_j \ket{i} 0 \bra{j} + \sum_i \lambda_i^\ast  \lambda_i \ket{i} 1 \bra{i} \;\;\mbox{(orthonormal)}\\
\end{align}
```




## The postulates of quantum mechanics
* (p 80) **Postulate 1**: Associated to any isolated physical system is a complex vector space with inner product (that is, a Hilbert space) know as the _state space_ of the system. The system is completely described by its _state vector_, which is a unit vector in the system's state space.
* (p 81) **Postulate 2**: The evolution of a _closed_ quantum system is described by a _unitary transformation_. That is, the state $|\psi\rangle$ of the system at time $t_1$ is related to the state $|\psi'\rangle$ of the system at time $t_2$ by a unitary operator $U$ which depends only on the times $t_1$ adn $t_2$, $|\psi'\rangle = U |\psi\rangle$.
  * (p 82) ***Postulate 2'***: The time evolution of the state of a closed quantum system is described by the _Schrodinger equation_, $i \bar{h} \frac{d |\psi\rangle}{d t} = H |\psi\rangle$.
    * Imaginary number $i = \sqrt{-1}$; Planck's constant $\bar{h}$ must be experimentally determined; $H$ is a fixed Hermitian operator known as the _Hamiltonian_ of the closed system.
* (p 84) **Postulate 3**: Quantum measurements are described by a collection $\{M_m\}$ of _measurement operators_. These are operators acting on the state space of the system being measured. the index $m$ referfs to the measurement outcomes that may occur in the experiment. If the state of the quantum system is $|\psi\rangle$ immediately before the measurement then the probability that result $m$ occurs is given by $p(m) = \langle \psi | M_m^\dagger M_m | \psi \rangle$,
and the state of the system after the measurement is
$\frac{M_m | \psi \rangle }{\sqrt{\langle \psi | M_m^\dagger M_m | \psi \rangle}}$.
* (p 94) **Postulate 4**: The state space of a composite physical system is the tensor product of the state spaces of the component physical systems. Moreover, if we have systems numbered 1 through $n$, and system namer $i$ is prepared in the state $| \psi \rangle$, then the joint state of the total system is $| \psi_1 \rangle \otimes | \psi_2 \rangle \otimes \cdots \otimes | \psi_n \rangle$.


## Linear operators and matrices

> "The most convenient way to understand linear operators is in terms of their _matrix representation_.
> In fact, the linear operator and matrix viewpoints turn out to be completely equivalent."

Suppose $A: V \rightarrow W$ is a linear operator between vector spaces $V$ and $W$. Suppose $|v_1 \rangle, \ldots, |v_m \rangle$ is a basis for $V$ and $|w_1 \rangle, \ldots, |w_n \rangle$ is a basis for $W$.
Then for each $j$ in the range $1, \ldots, m$, there exists complex  numbers $A_{ij}$ through $A_{nj}$, such that

$A|v_j \rangle = \sum_i A_{ij} |w_i \rangle$.

Example (Exercise 2.2). Suppose $V$ is a vector space with basis vectors $|0 \rangle$ and $|1 \rangle$,
and $A$ is a linear operator from $V$ to $V$ such that $A |0 \rangle = |1 \rangle$ and $A |1 \rangle = |0 \rangle$.
Give a matrix representation for $A$, with respect to the input basis $|0 \rangle$ , $|1 \rangle$, and the output basis $|0 \rangle$ , $|1 \rangle$. Find input and output bases which give rise to a different matrix representation of $A$.

Soln:

$A | 0 \rangle = A_{11} | 0 \rangle + A_{21} | 1 \rangle = | 1 \rangle$. Thus, $A_{11} = 0$, $A_{21} = 1$.

$A | 1 \rangle = A_{12} | 0 \rangle + A_{22} | 1 \rangle = | 0 \rangle$. Thus, $A_{12} = 1$, $A_{22} = 0$.

That is,
$A = [[0, 1], [1, 0]]$.

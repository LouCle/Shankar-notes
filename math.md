$$
\newcommand{\bra}[1]{\langle #1 \rvert}
\newcommand{\ket}[1]{\rvert #1 \rangle}
\newcommand{\braket}[2]{\langle #1 \rvert #2 \rangle}
\newcommand{\qty}[1]{\begin{bmatrix}#1\end{bmatrix}}
\newcommand{\V}{\mathbb V}
\newcommand{\F}{\mathbb F}
$$

## Mathematical Methods

### Linear Vector Spaces

A linear vector space $\V$ is defined over a field $\mathbb F$ (think of vector spaces as being composite objects of both vectors and a field). If they're defined over $\R$ it's a real vector space, if $\C$, complex. The field consists of scalars, so the vectors themselves are neither complex nor real. A *vector* is an element of $\V$.

They have the following requirements:

- A definite rule representing $\ket V + \ket W$ 
- A definite rule for $a\ket V$ where $a \in \mathbb F$
- Closure under addition, $\ket V + \ket W \in \V$ 
- Distributive scalar multiplication for vectors, $a(\ket V + \ket W) = a\ket V + a\ket W$
- Distributive scalar multiplication for scalars $(a+b)\ket V  = a\ket V + b\ket V$
- Associative scalar multiplication, $a(b\ket V) = ab\ket V$
- Commutative addition, $\ket V + \ket W = \ket W + \ket V$
- Associative addition, $\ket V + (\ket W + \ket Z) = (\ket V + \ket W) + \ket Z$
- Null vector, $\ket V + \ket 0 = \ket V$
- Inverse that can create null vector under addition, $\ket V + \ket{-V} = \ket 0$

Linear independence is the property for a vector to not be written in terms of other vectors in the same set. 

Any $\ket V \in \mathbb F^n$ can be written as a linear combination of $n$ linearly independent vectors $\ket 1 \dots \ket n$. Further, a set of $n$ linear independent vectors in $\F^n$ is called a basis. We get that 
$$
\ket V = \sum_{i=1}^n v_i \ket i
$$
Where $\ket i$ are the basis vectors. $v_i$ are thus the components of the vector $\ket V$. Addition of vectors of the same basis $\ket i$, add their components, i.e.
$$
\ket V + \ket W = \sum^n_{i=1}(v_i+w_i)\ket i
$$
and scalar multiplication is similar
$$
a\ket V = \sum^n_{i=1} av_i\ket i
$$
Since both functions and matrices can be examples of vector spaces, a vector space requires no definition of length or direction for the elements.

Vector spaces can be a space of functions from a set to a field. Let $\mathbb F$ be any field, and let $S$ be a non-empty set. Let $\V$ be the set of all functions from the $S$ into $\mathbb F$. any function $f$ of $\V$ will thus satisfy all the vector space requirements.

##### Exercise 1.1.2: Show that vectors of the form $(a,b,1)$ do not form a vector space

They don't obey closure under addition
$$
(a,b,1) + (c,d,1) \not = (a+c,b+d,1)
$$

##### Exercise 1.1.4

Given
$$
\ket 1 = (1,1,0)\\\ket 2 = (1,0,1)\\\ket 3 = (0,1,1)
$$
We can show that these are linearly independent by attempting to solve the equation for non-zero $a_i$
$$
\sum_{i=1}a_i\ket i=0
$$
from which we get that
$$
a_1+a_2=0 \\a_1+a_3=0 \\a_2+a_3=0
$$
we can now solve $a_1$ and $a_2$ in terms of $a_3$
$$
a_1 = -a_3\\a_2 = -a_3
$$
substituting into $a_1+a_2=0$
$$
-2a_3=0\\a_3 = 0
$$
which finally gives us
$$
a_1=a_2=a_3=0
$$
Thus the vectors are linearly independent, as there is no non-zero solution. 

### Inner Product Space

Recall the arrow vector dot product
$$
\vec A \cdot \vec B = \vec B \cdot \vec A
$$
This obeys linearity, positive semi-definiteness and also symmetry. We can create a generalized scalar product or inner product between any vectors $\ket V$ and $\ket W$, denoted by $\braket{V}{W}$, which "spits out" a scalar. Generally it's defined on $\C$. It obeys the following axioms

- $\braket{V}{W} = \braket{W}{V}^*$ skew-symmetry ($^*$ denotes the complex conjugation)
- $\braket{V}{V}\geq 0 \Leftrightarrow \ket V=~\ket 0$ positive semi-definiteness
- $\braket{V}{(a\ket W +b\ket Z)} = \braket{V}{aW+bZ} = a\braket{V}{W}+b\braket{V}{Z}$ linearity in ket

If a vector space has an inner product, it's called an inner product space. Just to note how we can combine

What if the first factor in the product is a linear superposition, i.e., what is $\braket{aW+bZ}{V}$? - given the first action we get anti-linearity:
$$
\begin{align*}\braket{aW+bZ}{V} &= \braket{V}{aW+bZ}^* \\
&= (a\braket{V}{W}+b\braket{V}{Z})^*\\
&= a^*\braket{V}{W}^*+b^*\braket{V}{Z}^*\\
&= a\braket{W}{V}^*+b\braket{Z}{V}^*
\end{align*}
$$
Were the superposition in the second factor we wouldn't have the conjugates. This is an asymmetry.

Two vectors are orthogonal/perpendicular if their inner product vanishes.

$\sqrt{\braket{V}{V}} = \|V\|$ is the norm/length of a vector. A normalized vector has unit norm.

A set of pairwise orthogonal basis vectors of unit norm are an orthonormal basis.

The inner product is defined verbosely as
$$
\braket{V}{W} = \sum_{i=1}^n\sum_{j=1}^n v_i^*w_j\braket{i}{j}
$$
For an orthonormal basis we get that
$$
\braket{i}{j} = \delta_{ij}
$$
Which means that $v_i^*w_j\not = 0 \Leftrightarrow i=j$ thus collapsing the sum as follows
$$
\begin{align*}
\braket{V}{W} &= \sum_{i=1}^n\sum_{j=1}^n v_i^*w_j \delta_{ij} \\
&= \sum_{i=1}^n v_i^*w_i
\end{align*}
$$
We refer to $\braket{V}{V}$ as the norm squared, as follows
$$
\braket{V}{V} = \sum_{i}^n |v_i|^2 \geq 0
$$
We can write ket vectors in this basis like
$$
\ket X = \qty{x_1\\x_2\\\vdots\\x_n}
$$
The inner product $\braket{V}{W}$ is then the matrix product of the transpose conjugate of $\ket V$ with $\ket W$, i.e. $\mathbf V^\dagger \mathbf W$ which is the following
$$
\braket{V}{W} = \qty{v_1^*&v_2^*&\cdots&v_n^*} \qty{w_1\\w_2\\\vdots\\w_n}
$$

### Dual Spaces and Dirac Notation

Column vectors are manifestations of an abstract vector $\ket V$ in a basis. Each row vector we can associate an abstract vector $\bra W$. Associated with every ket $\ket V$ is a column vector, and taking the transpose conjugate of this, gives us a row vector. The abstract bra associated with this row vector is called $\bra V$. There are *two* vector spaces, the ket space and a dual space of bras, with a ket for every bra and the other way around.

Inner products are defined between bra's and ket's.

There is a basis of vectors $\ket i$ for expanding ket's, and a similar basis $\bra i$ for expanding bra's.

For a basis column/row vector, the $i$'th row or column is a 1 whilst all the others are 0's.

We can describe the associations like
$$
\ket V \leftrightarrow \qty{v_1\\v_2\\\vdots\\v_n}
\leftrightarrow \qty{v_1^*&v_2^*&\cdots&v_n^*}
\leftrightarrow \bra V
$$
We can find the $j$'th component of a vector, recalling
$$
\ket V = \sum_i^n v_i\ket i
$$
which gives us
$$
\begin{align*}
\braket{j}{V} &= \sum_i^n v_i\braket{j}{i} \\
&= v_j
\end{align*}
$$
We can use this result and construct $\ket V$ as
$$
\ket V = \sum_i \ket i \braket{i}{V}
$$
Where $\braket{i}{V}$ gives us the $i$'th component $v_i$ and scalar multiply it with $\ket i$.

**Adjoint** 
The adjoint operation is in this case a transpose conjugate, but the adjoint is a generalized operation. Taking the adjoint of a linear equation relating bra's to ket's replace every ket with its bra (and vice versa), and complex conjugate all coefficients.

We can see this easily given
$$
\ket V = \sum_i \ket i\braket{i}{V}
$$
taking the adjoint gives us
$$
\bra V = \sum_i \braket{V}{i}\bra i
$$
**Gram-Schmidt and dimensionality** 
Given a set linearly independent basis vectors, we can orthonormalize them using the Gram-Schmidt method. 

Let $\ket I, \ket{II},\dots$ be a linearly independent basis. We calculate the first vector of our orthonormalized basis as
$$
\ket 1 = \frac{\ket I}{\|I\|}
$$
this means that
$$
\braket{1}{1} = \frac{\braket{I}{I}}{\|I\|^2} = 1
$$
and we can now orthonormalize our last vector
$$
\ket{2'} = \ket{II}-\ket{1}\braket{1}{II}
$$
from which you can get the basis vector by
$$
\ket 2 =\frac{1}{\|2'\|} \ket{2'}
$$
As for dimensionality,

> The dimensionality of a space equals $n_\perp$, the maximum  number of mutually orthogonal vectors in it.

Any mutually orthogonal set is linearly independent. 

### Subspaces

Given a vector space $\V$, a subset of its elements that form a vector space is called a subspace. A subspace $i$ of $n_i$ dimensionality is denoted $\V^{n_i}_i$.

Given two subspaces, their sum can be found
$$
\mathbb V^{n_i}_i\oplus \mathbb V^{m_j}_j = \mathbb V^{m_k}_k
$$
Where $\V^{m_k}_k$ contains all elements of $\V^{n_i}_i$ and $\V^{m_j}_j$, and all the possible linear combinations of them. 

A subset of a vector space, is a subspace iff for each pair of vectors $a$, $b$ in the subset and each scalar $c$ in the field, the vector $ca+b$ has closure.

Given $\V$ over the field $\F$. Any intersection of any collection of subspaces of $\V$ is also a subspace of $\V$.

### Linear Operators

A linear operator $\Omega$ or linear transformation $T$ is any function from $\V_1$ to $\V_2$ such that
$$
T(cv_1+v_2)=c(Tv_1)+Tv_2
$$
bbAn operator $\Omega$ takes a vector $\ket V \in \V$ and transforms it to another $\ket{V'}$ (and vice versa for bra's). We're interested mainly in operators for which $\Omega \ket V \in \V$.

Linear operators obey the following rules:

- $\Omega a \ket V = a \Omega \ket V$
- $\Omega(\alpha\ket{V_i}+\beta\ket{V_j}) = \alpha \Omega\ket{V_i}+\beta \Omega\ket{V_j}$

And the same rules for bra's, except the order is reversed.

The simplest operator is the identity operator $\hat I$. It works as follows
$$
\forall \ket V,~\hat I \ket V = \ket V
$$
or 
$$
\forall \bra V,~\bra V \hat I = \bra V
$$
We can another interesting operator, namely the rotation operator over $\V^3(R)$. E.g. $\hat R(\frac{1}{2}\pi e_x)$ which rotates a vector about the $e_x$ unit vector by $\frac{1}{2}\pi$. An example
$$
\hat R\left(\frac{1}{2}\pi e_x\right)\ket 2 = \ket 3
$$
This operator is linear. 

The product of two operators means their operation carried out in sequence, i.e.
$$
\Lambda \Omega \ket V = \Lambda (\Omega \ket V) = \Lambda \ket{\Omega V}
$$
We denote the ket vector obtained by the action of $\Omega$ on $\ket V$ as $\ket{\Omega V}$. The order is important.

The commutator defined below is non-zero
$$
\Omega \Lambda - \Lambda \Omega \equiv [\Omega, \Lambda]
$$
as these two operators do not commute. Two useful commutation identities
$$
\begin{align*}
[\Omega, \Lambda \theta] &= \Lambda[\Omega, \theta]+[\Omega,\Lambda]\theta \\[]
[\Lambda\Omega,\theta] &= \Lambda[\Omega,\theta]+[\Lambda,\theta]\Omega
\end{align*}
$$
The inverse of $\Omega$ is $\Omega^{-1}$ and satisfies
$$
\Omega \Omega^{-1} = \Omega^{-1}\Omega = \hat I
$$

### Matrix Elements of Linear Operators

Linear operators can be represented in a basis by a set of $n^2$ numbers, written as a $n\times n$ matrix - these are called the matrix elements in that basis.

If the basis vectors suffer a change
$$
\Omega \ket i = \ket{i'}
$$
then any vector in this space undergoes a change that is readily calculable
$$
\Omega \ket V = \Omega \sum_i v_i\ket i = \sum_iv_i \Omega \ket i = \sum_i v_i \Omega \ket{i'}
$$
When we say $\ket{i'}$ is known, we mean that its components in the original basis are known, 
$$
\braket{j}{i'} = \bra{j} \Omega\ket i \equiv\Omega_{ji}
$$
The $n^2$ number, $\Omega_{ij}$, are the matrix elements of $\Omega$ in this basis. If
$$
\Omega \ket V = \ket {V'}
$$
then we can expand the terms of the transformed $\ket{V'}$ as
$$
v_i' = \sum_j\Omega_{ij}v_j
$$

Just for good measure, we can show this in matrix form as
$$
\qty{v_1'\\v_2'\\\vdots\\v'_n} = \qty{\bra 1 \Omega \ket 1 & \cdots & \bra 1 \Omega \ket n\\\vdots&\ddots \\\bra n \Omega \ket 1 &&\bra n \Omega \ket n}\qty{v_1\\v_2\\\vdots\\v_n}
$$
**Projection Operator** 
Remember that the "outer product" $\ket V \bra W$ produces an $n\times n$ matrix, whilst the inner or dot product $\braket{V}{W}$  produces a scalar. The projection operator is defined as follows
$$
\hat I = \sum_i \ket i \bra i = \sum_i \mathcal P_i
$$
The object $\mathcal P_i = \ket i \bra i$ is the projection operator for the ket $\ket i$. The above equation denotes the identity operator $\hat I$ of $i$ as summation over projection operators for $i$.

The next definition encapsulates the usage of the projection operator, that is
$$
\mathcal P_i \ket V = \ket i \braket{i}{V} = \ket iv_i
$$
It projects any component $v_i$ out as a ket in the direction $i$. $\ket V$ is thus the sum of all of those kets. Notice that it works similarly on bras, just by reversing the terms
$$
\bra V \mathcal P_i = \braket{V}{i}\bra i= v_i^*\bra i
$$
For the following equation
$$
\mathcal P_i \mathcal P_j = \ket i\braket{i}{j} \bra j = \delta_{ij} \mathcal P_j
$$
We note that, has $\mathcal P_j$ already been applied to a $\ket V$, further applications of $\mathcal P$ to $\ket{\mathcal P_j V}$ yields an unchanged $\ket{P_j V}$ (hence the Kronecker delta). We also see that, if $i \not = j$ for $\delta_{ij}\mathcal P_j$, we yield 0 (meaning that if you project a vector onto one basis, projecting it again yields nothing, as there's no information left of the other bases).

Any projection operator has a $1$ at the $i$'th element on the diagonal of the matrix representation. $\sum _i^n \mathcal P_i = \hat I$, whilst if we sum it only over $i$ corresponding to a subspace's basis vectors, we get an operator that projects a vector into the given subspace. For example, projecting an $\R^n$ vector into $\R^{n-1}$
$$
\ket{V'} = \sum_i^{n-1}\mathcal P_i \ket V
$$
**Matrices Corresponding to Products of Operators** 
Matrix for a product of operators
$$
(\Omega \Lambda)_{ij} = \bra i \Omega \Lambda \ket j=\sum_k\Omega_{ik}\Lambda_{kj}
$$
The matrix-form of the operator product is simply the product of the matrix-forms.

**Operator Adjoint**
Given a ket
$$
\Omega \ket V= \ket{\Omega V}
$$
Its corresponding bra is 
$$
\bra{\Omega V} = \bra V \Omega^\dagger
$$
$$\Omega^\dagger$$ is the adjoint of $\Omega$, and is the operator that can act on the bra vector. Its matrix-form is the conjugate transpose of $\Omega$'s matrix-form. We also see that
$$
\Omega^\dagger_{ij} = \Omega^*_{ji}
$$
The adjoint of a product of operators is the product of each individual adjoint in reverse.

**Hermitian, Anti-Hermitian and Unitary operators**
An operator is Hermitian if
$$
\Omega^\dagger = \Omega
$$
An operator is anti-Hermitian if
$$
\Omega^\dagger = -\Omega
$$
An operator can be decomposed into Hermitian and anti-Hermitian parts as
$$
\Omega = \frac{\Omega+\Omega^\dagger}{2} + \frac{\Omega-\Omega^\dagger}{2}
$$
An operator $\hat U$ is unitary if
$$
\hat U\hat U^\dagger = \hat I
$$
This means that the adjoint is the inverse of it (and vice versa). 
$$
\hat U^\dagger \hat U = \hat I
$$
Unitary operators preserve the inner product between the vectors they act on.

**Section not finished**

### Groups

The set of *invertible* linear operators with the operation of composition provides a nice example of a group.

A group consists of the following

1. A set $G$
2. A rule that associates each pair of elements $(x,y)$ in $G$ with $xy$ in $G$ in such a way that
   1. $x(yz) = (xy)z$ for all $x$, $y$ and $z$ in $G$ - associativity.
   2. there is an element $e\in G$ such that $ex=xe=x$ for every $x$ in $G$
   3. to each element $x$ in $G$ there corresponds an element $x^{-1}$ in $G$ such that $xx^{-1}=x^{-1}x=e$

In general, groups requires totality, associativity, identity and invertibility, but not necessarily commutativity. We will briefly look at abelian groups below.

We're already acquainted with the identity operator $\hat I$ that abides by such requirements. Thus the set $\V$ together with $\hat I$ is a group. $n\times n$ invertible matrices together with matrix multiplication are also a group. A group of set $G$ with an operator $(\cdot)$ is non-abelian if
$$
(\exists a,b\in G)\ni a\cdot b \not=b\cdot a
$$
Thus both examples are non-abelian. An example of abelian (commutative) groups would be $\ket V \in \V$ together with the operation of vector addition.

### Isomorphism

Any injective linear transformation $T$ from $\V_1$ onto $\V_2$ is called an isomorphism of $\V_1$ onto $\V_2$. If there exists such isomorphism, we can say that $\V$ is isomorphic to $\V_2$.

$\V_1$ is trivially isomorphic to itself, the identity operator $\hat I$ being an isomorphism of $\V_1$ onto itself. If $\V_1$ is isomorphic to $\V_2$ with $\Omega$, then $\V_2$ is isomorphic onto $\V_1$ with $\Omega^{-1}$, thus we say that $\V_1$ and $\V_2$ are isomorphic.

Isomorphic vector spaces are often regarded as "the same", but the vectors and operations in either vector space may be different.

### Eigenvalues and Eigenkets

Each operator has a vector of its own called an eigenvector, which can be related to the original vector by some scalar. If we have that
$$
\Omega \ket V = \omega\ket V
$$
then $\ket V$ is the eigenvector of $\Omega$, and the eigenvalue is $\omega$. For example, the only eigenvalue for the identity operator is $1$. All vectors are its eigenvectors.

**The Characteristic Equation**
From 1.8.8, we get the characteristic equation
$$
\sum^n_{m=0}c_m\omega^m=0
$$
and the characteristic polynomial
$$
P^n(\omega)=\sum_{m=0}^n c_m\omega^m
$$
The roots of $P^n$ are the eigenvalues. Any operator in $\V^n(C)$ has $n$ eigenvalues. For Hermitian and unitary operators, we can easily find the corresponding eigenvectors if we know the eigenvalues.

### Generalizations to infinite dimensions

Blablabla.

## Review of Classical Mechanics

### Lagrangian Mechanics

Lagrangian formalism of mechanics, the problem of a particle in a potential $V(x)$ is posed in a simple way

>  Given that the particle is at $x_i$ and $x_f$ at times $t_i$ and $t_f$ respectively, what is it that distinguishes the actual trajectory $x_{cl}(t)$ from all other paths?

Lagrangian mechanics attempts to determine in one stroke an entire path for a particle, as opposed to Newtonian mechanics that is concerned with infintesimals.

We can create a few steps for this problem

1. Define a function $\mathscr L$ called the Lagrangian using
   $$
   \mathscr L = T-V
   $$
   Giving us a function $\mathscr L = \mathscr (x,\dot x, t)$

2. For all paths $x(t)$ connecting $(x_i,t_i)$ and $(x_f,t_f)$ calculate the action as
   $$
   S[x(t)] = \int_{t_i}^{t_f} \mathscr L(x,\dot x)~dt
   $$

3. We will then attempt to minimize $S[x(t)]$, because of the principle of least action.

I won't derive the Euler-Lagrange equations here, but we can find a minimized path given
$$
d_t({\partial_{\dot x_i} \mathscr L}) = \partial_{x_i} \mathscr L
$$
Systems often use generalized coordinates $q_i$.

### The Hamiltonian Formalism

In the Lagrangian formalism, the independent variables are generalized coordinates. Momentum is a derived quantity that we define as
$$
p_i = \frac{\partial \mathscr L}{\dot q_i}
$$
The Hamiltonian formalism is similar, but exchanges the role of $\dot q$ and $p$. Instead of $\mathscr L(q,\dot q)$ we yield $\mathcal H(q,p)$ which generates the equations of motion and $\dot q$ thus becomes the derived quantity as
$$
\dot q_i = \frac{\partial \mathcal H}{\partial p_i}
$$
We can effect such a change with the Legendre Transform. Simply, given
$$
u(x) = d_xf
$$
We can define a function
$$
g(u) = x(u)u-f(x(u))
$$
thus giving us
$$
d_ug = d_ux\cdot u+x(u)-d_xf\cdot d_u x=x(u)
$$
We can generalize this given $f=f(x_1,x_2,\dots,x_n)$ as
$$
g(u_1,\dots,u_j,x_{j+1},\dots,x_n) = \sum^j_{j=1}\partial_{x_i}fx_i-f(x_1,\dots,x_n)
$$
We see that
$$
\partial_{u_i}g = x_i
$$
which will become useful in a second.

The Lagrangian formalism describes the state of a system as a path in $n$-dimensional configuration space. Converesely, the Hamiltonian mechanics describes the state as a point in $2n$-dimensional phase space with the coordinates $q_1,\dots,q_n,p_1,\dots,p_n$. For a given $\mathcal H$, only one path passes through a given point in phase space.

With all this in mind, we can apply the Legendre transform to the Lagrangian to obtain the "corresponding" Hamiltonian
$$
\mathcal H(q,p) = \sum_i q_ip_i-\mathscr L(q_i,\dot q_i)
$$
Hamilton's canonical equations are
$$
\frac{\partial \mathcal H}{p_i} = \dot q_i
$$
and
$$
-\frac{\partial \mathcal H}{\partial q_i} = \dot p_i
$$
A relation we will use later is that given
$$
T = \frac{1}{2}m\dot x^2,~V=V(x)
$$
We get the canonical momentum
$$
p = \partial_{\dot x} \mathscr L = m\dot x
$$
Which we can invert to $x_i(p)$ (instead of $p(x_i)$) as
$$
\dot x = \frac{p}{m}
$$
Which yields
$$
\mathcal H(x,p) = \frac{p^2}{2m}+V(x)
$$

### Cyclic Coordinates, Poisson Brackets and Canonical Transformation


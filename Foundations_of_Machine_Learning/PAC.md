# The PAC Learning Framework
**sample complexity**: the number of points needed to achieve an approximate solution to the class of learnable concepts.   

finite hypothesis set  
**consistent case**: the hypothesis set used contains the concept to learn 

## The PAC Learning Model
### Notations
- $\mathcal{X}$: input space, the set of all possible examples or instances  
- $\mathcal{Y}$: target space, the set of all possible labels or target values, $\{0, 1\}$ in this introductory chapter.
- $\mathcal{C}$: concept class(a set of classes), a concept can be a mapping from $\mathcal{X}$ to $\mathcal{Y}$.
- $H$: hypothesis set

#### Assumptions

- Examples are independently and indetically distributed (i.i.d.) according to some fixed but unknown $D$.

#### Generalization Error
$R(h) = Pr_{x\sim D}[h(x) \neq c(x)] = E_{x\sim D}[1_{h(x)\neq c(x)}]$
The generalization error of a hypothesis is not directly accessible since both the distribution $D$ and the target $c$ are unknown. However, the learner can measure the **empirical error** of a hypothesis on the labeled sample $S$.  

#### Empirical Error
$\hat{R}(h) = \frac{1}{m}\sum_{i = 1}^{m}1_{h(x_i)\neq c(x_i)}$
Thus, the empirical error of $h \in H$ is its average error on the sample $S$.  

#### Relations between generalization error and empirical error
Note that for a fixed hypothesis $h \in H$, the expectation of the empirical error based on an i.i.d sample $S$ is equal to the generalization error.
$E[\hat{R}(h)] = R(h)$

### PAC Learning 
#### Notations of Cost
- $O(n)$: an upper bound on the computational representation of any element $x \in \mathcal{X}$. 
- size($c$): the maximal cost of the computational representation of $c \in C$. 
#### Definitions
A concept class $C$ is PAC-learnable, if there exists an algorithm $\mathcal{A}$ and a polynomial function $poly(\cdot, \cdot, \cdot, \cdot)$  such that for any $\epsilon > 0$ and $\delta > 0$, for all distribution $D$ on $\mathcal{X}$ and for any target concept $c \in C$, the following holds for any sample size $m \geq poly(\frac{1}{\epsilon}, \frac{1}{\delta}, n, size(c))$:  
$$Pr_{S\sim D^m}[R(h_S) \leq \epsilon] \geq 1 - \delta$$
If $\mathcal{A}$ further runs in $poly(\frac{1}{\epsilon}, \frac{1}{\delta}, n, size(c))$, then $C$ is said to be **efficiently PAC-learnable**. The algorithm $\mathcal{A}$ exists, it is called a **PAC-learning algorithm** for $C$.


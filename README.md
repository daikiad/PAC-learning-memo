# PAC-learning-memo

## Notations
error $\epsilon \in (0,1)$

confidence $\delta\in(0,1)$

sample complexity $m_H : (0,1)^2 \rightarrow \mathbb{N}$

PAC learningの定義では無数の $m_H$が考えられる場合がある。

ここでは簡便のため、sample complexity $m_H$と言った場合は、無数の候補の中で最小のもの $m_H(\epsilon, \delta) = \min(m_{H,\text{candadate}}(\epsilon, \delta))$を指す。

learning algorithm $A$

domain set $Z$

$\mathcal{D}\subset Z$


*general loss function*  $l: \mathcal{H}\times Z \rightarrow \mathbb R_{+} $
に対して
*risk function* $L_\mathcal{D}$と *empirical risk* $L_S$ を以下のように定義する

$$
L_\mathcal{D}\centercolon= \underset{z\sim\mathcal{D}}{E}[l(h, z)]
$$

$$
L_S(h) \centercolon=\frac{1}{m} \sum_{i=1}^m (l(h, z_i))
$$

# 第三章 A Formal Learning Model

## Definition 3.4 (Agnostic PAC learnability for general loss functions)

A hypothesis class $\mathcal{H}$ is agnostic PAC learnable 
w.r.t. a set $Z$ and a loss function $l : H \times Z \rightarrow \mathbb{R}_{+}$ if

$$
\left(\exists m_H (0,1)^2\rightarrow \mathbb{N}\right)
\left(\exists \text{ learning algorithm }A\right)\text{ s.t. }\\
\left[
(\forall\epsilon,\delta)
(\forall\mathcal{D})
(\forall m \ge m_H(\epsilon, \delta))
\left(\mathbb{P}_{S\sim \mathcal{D}^m}[L_\mathcal{D}(A(S))\le \min_{h'\in\mathcal{H}} L_\mathcal{D}(h')+\epsilon]\ge 1-\delta\right)
\right]
$$

where the training set $S$ is created by drawing i.i.d. samples from $\mathcal{D}$

# 第四章 Learning via Uniform Convergence
## 定義4.1 ($\epsilon$-representative sample)
A training set $S$ is called $\epsilon$-representative (w.r.t. $Z$, $\mathcal{H}$, $l$, and $\mathcal{D}$)if

$$
\forall h\in\mathcal{H}, |L_S(h)-L_\mathcal{D}(h)|\le \epsilon
$$


## 補題4.2(Lemma 4.2)
training set $S$が $\epsilon/2$-representative (w.r.t. $Z$, $\mathcal{H}$, $l$, and $\mathcal{D}$)のとき、全ての
$\text{ERM}\_\mathcal{H}(S)$
、つまり全ての $h_S\in \text{argmin}\_{h\in\mathcal{H}} L_S(h)$
は次を満たす。

$$
L_\mathcal{D}(h_S) \le \min_{h\in\mathcal{H}}L_\mathcal{D}(h)+\epsilon
$$

## Definition 4.3 Uniform Convergence

A hypothesis class $\mathcal{H}$ has the **uniform convergence property** (w.r.t. $Z$ and $l$ ) if

$$
\exists m_{H}^{UC} \text{ s.t.}\\
\left[(\forall \epsilon)(\forall\delta)(\forall \mathcal{D}\text{ over } Z)
[\mathbb{P}_{S\sim \mathcal{D^m}}[\text{S is epsilon representative}]\ge 1-\delta]\right]
$$

where S is a sample of $m\ge m_\mathcal{H}^{UC}(\epsilon, \delta)$ examples drawn i.i.d. according to $\mathcal{D}$

## 系4.4 (Corollary 4.4)

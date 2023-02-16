# PAC-learning-memo
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

where the training set $S$ is created by drawing i.i.d. samples from $\mathcal{D}$ and $L_\mathcal{D}(h):= \underset{z\sim \mathcal{D}}{\mathbb{E}}\left[l(h, z)\right]$

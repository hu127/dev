# Least-squares estimation of transformation parameters between two point patterns

## 适用场景
现在有两组点云 $\{x_i\},\{y_i\}$ , 其中 $i=1,2,\cdots,n$ , 点云为$m$维,现在我们需要找到两组点云之间的相似变幻(R:rotation, t:translation, c: scaling). \
并且这个相似变幻可以给出两组点云之间的最小均方误差(mean squared error) $e^2(R,t,c)$.
$$e^2(R,t,c)=\frac{1}{n}\sum_{i=1}^{n}\|y_i-(cRx_i+t)\|^2$$

## 需要的 Lemma
现有 $A$ 和 $B$ 两个 $m\times n$的矩阵， $R$ 是一个 $m\times m$的旋转矩阵, $UDV^T$ 是 $AB^T$ 的SVD结果($UU^T=VV^T+I$, $D=\text{diag}(d_i),d_1\geq d_2\geq \cdots \geq d_m \geq 0$). \
关于 $R$ 的方程 $\|A-RB\|^2$ 的最小值为

$$
\min _R\|A-R B\|^2=\|A\|^2+\|B\|^2-2 \operatorname{tr}(D S)
$$
其中
$$
S= \begin{cases}I & \text { if } \operatorname{det}\left(A B^T\right) \geq 0 \\ \operatorname{diag}(1,1, \cdots, 1,-1) & \text { if } \operatorname{det}\left(A B^T\right)<0 .\end{cases}
$$
When $\operatorname{rank}\left(A B^T\right) \geq m-1$, the optimum rotation matrix $R$ which achieves the above minimum value is uniquely determined.
$$
R=U S V^T
$$
where $S$ in (4) must be chosen as
$$
S= \begin{cases}I & \text { if } \operatorname{det}(U) \operatorname{det}(V)=1 \\ \operatorname{diag}(1,1, \cdots, 1,-1) & \text { if } \operatorname{det}(L) \operatorname{det}(V)=-1\end{cases}
$$
when $\operatorname{det}\left(A B^T\right)=0\left(\operatorname{rank}\left(A B^T\right)=m-1\right)$.
Proof of Lemma: Define an objective function $F$ as
$$
F=\|A-R B\|^2+\operatorname{tr}\left(L\left(R^T R-I\right)\right)+g\{\operatorname{det}(R)-1\}
$$


# Harmonic Oscillator With Damping: Solving ODEs

Consider a system:

$$
\begin{aligned}
-kx-cv=ma \\ 
-kdx-c\frac{dx}{dt}=m\frac{d^2x}{dt^2} \\
m\frac{d^2x}{dt^2}+c\frac{dx}{dt}+kx=0 \\ 
\end{aligned}
$$

Note that $-cv$ is the damping term!

This is your average linear, second-order homogenous ordinary differential equation. First, guess $x=e^rt$, which leads us to solving the auxiliary equation;

$$
\begin{aligned}
Ar^2+Br+C=0 \\
mr^2+cr+k=0 \\
r=\frac{-c \pm \sqrt{c^2 - 4mk}}{2m} \\
\end{aligned}
$$

This gives us

$$
\begin{aligned}
x(t)=\exp(\frac{-c + \sqrt{c^2 - 4mk}}{2m})t,\hspace{0.2cm} \exp(\frac{-c + \sqrt{c^2 + 4mk}}{2m})t
\end{aligned}
$$

So, the general solution is 
$$
x(t)=C_{1}\exp(\frac{-c + \sqrt{c^2 - 4mk}}{2m})t+C_{2}\exp(\frac{-c + \sqrt{c^2 + 4mk}}{2m})t
$$

Let's examine different possibilities for the discriminant $c^2-4mk$.

$$
\begin{aligned}
c^2-4mk<0 	\Rightarrow c^2<4mk \cdots 1\\
c^2-4mk=0 	\Rightarrow c^2=4mk \cdots 2\\ 
c^2-4mk>0 	\Rightarrow c^2>4mk \cdots 1\\ 
\end{aligned}
$$

For our convenience, let $d=\sqrt{|c^2 - 4mk|}$.

**Possibility $1$**

$$
\begin{aligned}
r=\frac{-c \pm id}{2m}\\
\newline
\Rightarrow x(t)=\exp(\frac{-c}{2m}t \pm i\frac{d}{2m}t) \\ 
= \exp(\frac{-c}{2m}t)\exp(\pm i\frac{d}{2m}t) \\ 
= \exp(\frac{-c}{2m}t)(\cos(\frac{d}{2m}t) \pm i\sin(\frac{d}{2m}t)) \\
\Rightarrow x(t) = C_{1}e^{\frac{-c}{2m}t}\cos(\frac{d}{2m}t) + C_{1}e^{\frac{-c}{2m}t}\sin(\frac{d}{2m}t)
\end{aligned}
$$

**Possibility $2$**

$$
\begin{aligned}
r=\frac{-c}{2m}
\newline
\Rightarrow x(t)=\exp(\frac{-c}{2m}t)
\end{aligned}
$$

But we need one more root, so we multiply by $t$.

$$
\begin{aligned}
x(t) = t\exp(\frac{-c}{2m}t)
\end{aligned}
$$

Just to make sure, let's check that this is a solution.

$$
\begin{aligned}
m\frac{d^2x}{dt^2}+c\frac{dx}{dt}+kx=0 \\
m(\frac{-c}{2m}\exp(\frac{-c}{2m}t)-\frac{-c}{2m}\exp(\frac{-c}{2m}t)+(\frac{-c}{2m})^2t\exp(\frac{-c}{2m}t))\\
+c(\exp(\frac{-c}{2m}t)-\frac{c}{2m}t\exp(\frac{-c}{2m}t))+\\
k(t\exp(\frac{-c}{2m}t)) = 0 \\
(-\frac{c^2}{4m}+k)t\exp(-\frac{c}{2m}t) = 0
\end{aligned}
$$

Recalling that $c^2=4mk$ for this scenario,

$$
\begin{aligned}
(-\frac{c^2}{4m}+k)t\exp(-\frac{c}{2m}t) = 0
\end{aligned}
$$

Is successfully satisfied. Moreover, note that the Wronskian is also non-zero, which would show that it's linearly independent to the first solution.

So, the general solution is:

$$
\begin{aligned}
x(t) = C_{1}\exp(-\frac{c}{2m}t)+C_{2}t\exp(-\frac{c}{2m}t)
\end{aligned}
$$

**Possibility $3$**

$$
\begin{aligned}
r = \frac{-c \pm d}{2m}
\newline
\Rightarrow x(t) = C_{1}\exp(-\frac{c+d}{2m}t)+C_{2}\exp(-\frac{c-d}{2m}t)
\end{aligned}
$$

We have our three scenarios! Now let's see how they look experimentally with Python!
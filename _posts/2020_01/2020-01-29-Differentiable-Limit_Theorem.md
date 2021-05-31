---
layout: post
---
Consider a sequence of functions

$$f_1 , f_2 , \dots f_n$$

and suppose that they converge to a function, say $$\lim_{n\to \infty} f_n = f$$.

If each of these functions is differentiable, then we get a sequence of derivatives

$$f'_1 , f'_2 , \dots f'_n$$

suppose also that these functions converge to a function, say $$\lim_{n\to \infty} f'_n = g$$.

Given this information, the central question of this post arises:

  Is the derivative of the limit ($$f'$$) equal to the limit of the derivatives ($$g$$)?

This is the question answered by the differentiable limit theorem (Theorem 6.3.1 in Understanding Analysis by Stephen Abbott)

So, to start with: the answer is no in general. Consider the sequence of functions $$h_n(x) = x^{1+ \frac{1}{1-2n}}$$ on the interval $$[-1,1]$$. Each $$h_n$$ is differentiable: it's derivative is $$h'_n (x) = (1+ \frac{1}{1-2n})x^{\frac{1}{1-2n}}$$. [is there a case where $$g$$ exists and yet $$f' \neq g$$?]

However, the derivative of the limit and the limit of the derivatives will coincide when we add a few additional assumptions. Here is the statement of the theorem:

Suppose $$f_n \to f$$ pointwise on an interval $$[a,b]$$, suppose also that $$\forall n\in \mathbb{N}$$, $$f_n$$ is differentiable.

If the sequence of derivatives $$(f'_n)_n$$ converges $$\textit{uniformly}$$ to a function $$g$$, then $$f = \lim_{n\to \infty} f_n$$ is differentiable and $$f'(x) = g(x)$$ for all $$x\in [a,b]$$.

$$\textbf{Proof:}$$
We want to show that for a fixed $$c\in [a,b]$$, the limit $$\lim_{x\to c} \frac{f(x) - f(c)}{x-c}$$ exists and equals $$g(c)$$. The existence will follow from the fact that $$g(c)$$ gives a real value. So, given $$\epsilon > 0$$, we need to find some $$\delta > 0$$ such that, whenever $$|x-c| < \delta$$, we have
\begin{equation}
| \frac{f(x)-f(c)}{x-c}-g(c)| < \epsilon
\end{equation}

Observe that
\begin{align}
| \frac{f(x)-f(c)}{x-c}-g(c)| &= | \frac{f(x)-f(c)}{x-c} - \frac{f_n(x)-f_n(c)}{x-c} + \frac{f_n(x)-f_n(c)}{x-c} - f_n'(c)+f_n'-g(c)|\newline
 &\leq | \frac{f(x)-f(c)}{x-c} - \frac{f_n(x)-f_n(c)}{x-c}| + |\frac{f_n(x)-f_n(c)}{x-c} - f_n'(c)|+ |f_n'-g(c)|
\end{align}

Now we want to use our assumptions about $f_n$, $f$, and $g$ to make each of these values small.

First, since $$(f')_n$$ converges to $$g$$, there exists some $$N_1 \in \mathbb{N}$$ such that $$\forall m \geq N_1$$ we have $$\mid f'_m (c) - g(c)\mid < \frac{\epsilon}{3}$$. So we can make the third value sufficiently small by letting $$m \geq N_1$$

Next, since $$(f_n)_n$$ converges uniformly, by the Cauchy Criterion we know that there exists some $$N_2\in \mathbb{N}$$ such that for ANY $$x\in [a,b]$$, $$n,m\geq N_2 \Rightarrow \mid f'_n(x) - f'_m(x) \mid$$.

Now, set $$N = \max\{N_1 , N_2\}$$. Since $$f_N$$ is differentiable on $$[a,b]$$, we have, for any $$c\in [a,b]$$,

$$\lim_{x\to c} \frac{f_N(x) - f_N(c)}{x-c} = f'_N (c)$$

i.e., there exists some $$\delta > 0$$ such that

$$\mid x-c \mid < \delta \Rightarrow \mid \frac{f_N(x) - f_N(c)}{x-c} - f_N'(c) \mid < \frac{\epsilon}{3}$$

So we can make the second value in our inequality sufficiently small so long as $$\mid x - c < \delta$$ (IMPORTANT NOTE HERE: This is the $$\delta$$ which we are ultimately looking for.)

Now, fix $$x\in (c-\delta , c+\delta)$$ and consider $$h(x) = f_m(x) - f_N (x)$$ (where $m\geq N_2$$)

By the Mean Value Theorem, there exists an $$\alpha \in [c,x]$$ such that $$h'(\alpha) = \frac{h(x)-h(c)}{x-c}$$ (note that we assume WLOG that $$x > c$$. Also, we know that $$h'$$ exists on $$[c,x]$$ because both $$f_m$$ and $$f_N$$ are differentiable on $$[c,x]$$.)

Translating this from $$h$$ back in terms of $$f_m$$ and $$f_N$$, we see that we have

$$f_m' (\alpha) - f_N'(\alpha) = \frac{f_m(x) - f_N(x) - f_m(c) + f_N(c)}{x-c}$$

and since $$m,N\geq N_2$$, we know that $$ \mid f_m' (\alpha) - f_N'(\alpha) \mid < \frac{\epsilon}{3}$$, so

$$\mid \frac{f_m(x)-f_m(c)}{x-c} - \frac{f_N(x)-f_N(c)}{x-c} \mid < \frac{\epsilon}{3}$$

Now, taking the limit of this as $$m\to \infty$$, we get

$$ \mid \frac{f_m(x)-f_m(c)}{x-c} - \frac{f_N(x)-f_N(c)}{x-c} \mid \leq \frac{\epsilon}{3}$$

(where we can a possible equality since we have taken the limit)

Thus we can make the first value of our inequality as small as we wish.

Therefore

$$\mid \frac{f(x)-f(c)}{x-c}-g(c) \mid < \frac{\epsilon}{3} + \frac{\epsilon}{3} + \frac{\epsilon}{3} = \epsilon$$

and we conclude that the derivative of the limit is equal to the limit of the derivatives.

Q.E.D.

So why am I writing about this theorem? Because the proof method is illustrative of many difficult concepts in analysis; it requires not only knowledge of the definitions of derivatives, continuity, pointwise and uniform convergence, and the mean value theorem, but it also requires that you know how to utilize these ideas in nontrivial ways (beyond simply applying the definitions in specific contexts).

This proof has been covered in great detail in this third week of my real analysis II class and contains many ideas which will be manditory knowledge for taking the analysis prelim -- if not on the exam itself.

This blog is meant to be a place where I post mathematical ideas which I find interesting and, as the title of the blog may indicate, I consider myself more of an algebraist. So why is my first real post about an analysis proof?

Honestly, because I have been struggling with analysis this quarter. I thought that after last quarter I had a good grasp on the basic concepts, but starting over again in this second quarter of analysis, I found that I was frequently getting lost. This caused me to doubt my ability in analysis -- convincing myself that I did not have any intuition for the subject and that I would never be able to enjoy it in the way that I enjoy algebra.

Though these thoughts are still nagging at me a bit, this theorem and proof have been the first

I had studied the proof before class (worried that similar material might be on the quiz) and so when we went over it in class I was able to follow every minute step and understand it even better -- which, because of all the material required to understand the steps of the proof, meant that I understood more of analysis than I had thought.

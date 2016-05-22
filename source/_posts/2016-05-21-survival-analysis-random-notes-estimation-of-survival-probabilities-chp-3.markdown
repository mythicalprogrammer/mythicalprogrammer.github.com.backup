---
layout: post
title: "Survival Analysis: Estimation of Survival Probabilities chp 3.2.1 & 3.2.2"
date: 2016-05-21 14:19:21 -0700
comments: true
categories: 
- Statistic
- Survival Analysis
- Notes
---

### definitions

Failure and censored times where $$ N $$  is the number of subject:

$$
 \{t_1,t_2,\ldots, t_j, \ldots,t_N  \} 
$$

Distinct ordered failure time observed among $$ N $$ patients where $$ j $$ is the $$j$$th ordered time; not the $$j$$th subject:

$$
 t_{(1)} < t_{(2)} < ... < t_{( j )},  J \leq N  \\
$$

\# of failures; $$d_j \geq 1$$:

$$ 
 d_j (j = 1, \ldots, J) 
$$ 

\# of patients "at risk" -> # of subjects actually observed when failures occur:

$$ 
 n_j 
$$ 

### Survival Probabilities 

<b><i>Sample</i></b> conditional probability of surviving beyond time $$t_{(j)}$$ is: 

$$ 
\begin{align}
 \mbox{} \hat{p_j} & = \dfrac{n_j - d_j}{n_j} \\ 
 \mbox{} & = \dfrac{n_j}{n_j} - \dfrac{d_j}{n_j} \\
 \mbox{} & = 1 - \dfrac{d_j}{n_j} \\
 \mbox{} & = 1 - \hat{q_j} \\
\end{align}
$$

So... $$ n_j - d_j $$ is the patients that is alive at the $$j$$th time subtracted by the number of patients that "failed". 

"failed" can be relapses in cancer or death of patient. (*Yeah I know it's morbid.* But this books is about survival analysis in medical field.)

Dividing it over $$ n_j $$ gives us the probability of survival rate for that day, using those particular patients who survived at that day (in context $$j$$th day). It doesn't take into account of any previous days.

To expand, say on the $$j$$th day there is 112 patients but the previous day there were 113. This probability does not take previous day in account. 

Say we have a drug test for cancer and at the start of the experiment there is 127 patients. Over the course of the experiment people die off in different days. This probability does not take into account the original 127 patient. It only takes into account how many people were alive and died at that particular $$j$$th day.

We need to address this somehow. 

Note: $$ \hat{q_j} $$ is the estimated conditoinal probability of failure at $$t_{(j)}$$. 

The proportion of $$P(t)$$ in the <b><i>population</i></b> surviving at $$t$$ is:

$$ 
\begin{align}
\mbox{} \hat{P} & = \prod_{j|t_{j} \leq t} \hat{p_j} \\
\mbox{} & = \prod_{j|t_{j} \leq t} 1 - \hat{q_j} \\
\mbox{} & = \prod_{j|t_{j} \leq t} 1 - \dfrac{d_j}{n_j} \\
\end{align}

$$



<table class="pure-table">
<thead>
<tr>
<th>Treatment</th>
<th>Time to relapse (week)</th>
<th>Num of censored data</th>
<th>Num of failures</th>
<th>Num of patients at risk</th>
<th>Conditional probability of remision</th>
<th>Cumulative probability of remission</th>
</tr>
<tr>
<th></th>
<th>$$t_{(j)}$$</th>
<th></th>
<th>$$d_j$$</th>
<th>$$n_j$$</th>
<th>$$\hat{p_j} = \dfrac{n_j - d_j}{n_j}$$</th>
<th>$$\hat{P} = \prod_{j|t_{j} \leq t} \hat{p_j}$$</th>
</tr>
</thead>
<tr>
<td>Placebo</td>
</tr>
<tr>
<td></td>
<td>1</td>
<td></td>
<td>2</td>
<td>21</td>
<td>$$\dfrac{19}{21} = 0.90476$$</td>
<td>$$0.90476$$</td>
</tr>
<tr>
<td></td>
<td>2</td>
<td></td>
<td>2</td>
<td>19</td>
<td>$$\dfrac{17}{19} = 0.89474$$</td>
<td>$$0.9048 \times 0.8947 = 0.8095$$</td>
</tr>
<tr>
<td></td>
<td>3</td>
<td></td>
<td>1</td>
<td>17</td>
<td>$$\dfrac{16}{17} = 0.94118$$</td>
<td>$$ 0.8095 \times 0.9412 = 0.7619$$</td>
</tr>
<tr>
<td>$$\ldots$$</td>
</tr>
<tr>
<td>6-MP</td>
</tr>
<tr>
<td></td>
<td>6</td>
<td>1</td>
<td>3</td>
<td>21</td>
<td>$$\dfrac{18}{21} = 0.85714$$</td>
<td>$$ 0.8571 $$</td>
</tr>
<tr>
<td></td>
<td>7</td>
<td></td>
<td>1</td>
<td>17</td>
<td>$$\dfrac{16}{ (21-3-1)=17} $$ $$= 0.94118$$</td>
<td>$$ 0.8571 \times 0.9412 = 0.8067 $$</td>
</tr>
</table>


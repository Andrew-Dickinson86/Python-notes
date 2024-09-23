## <center>Basic Statistics<center>

### Useful Links

[Python Quick Reference](https://www.python.org/ftp/python/doc/1.1/quick-ref.1.1.html)

[Python3 cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)

[Python.org](https://www.python.org/)

[Python Standard Library](https://docs.python.org/3/library/index.html)

[Python Functions](https://docs.python.org/3/library/functions)

---

|<td colspan=3> <center><bold><h3>**Table of contents**<center>|||
|---|:---|:---:|
|**01.**|[**Basic Statistics**](#Basic-Statistics;)|statistical types of data<br>types of probability distribution<br>expected value<br>mode, variance, median<br>pearson correlation coefficient (PCC)|

**Statistical types of data**:  

Three main types:
- $x$ is an **ordinal** variable if $x\in\mathbb{N}$ (**Natural numbers** - whole, positive, **typically does not include 0**);  
$\;\;\;\;$e.g:  
    * Our age  
    * Amazon star reviews  
    * Likert scale (strongly agree [5], agree [4], neutral [3], disgree [2], strongly disagree [1])  
- $x$ is a **numerical** variable if $x\in\mathbb{R}$ (**Real numbers** - all rational and irrational numbers;  
- $x$ is an **categorical (or nominal)** variable if $x\in C$, where $C$ is a **finite set** of element (and typically there's **no order between the elements** of $C$)  
$\;\;\;\;$e.g:  
    * Yes/No,  
    * The categories of films/books  

**Types of probability distribution**:  

There are **two main types**:  
* **Discrete**; good for **categorical / ordinal** data  
* **Continuous**; good for **numerical** data  

**Discrete probability distributions** include:  

* Bernoulli Distribution  
* Uniform Distribution  
* Poisson Distribution  

**Continuous probability distributions** include:  

* Continuous Uniform Distribution  
* Gaussian Distribution  

**Bernoulli Distribution**:  

See NumPy section for creating random distributions in Python  

Any kind of events with **two possible outcomes (binary events**), e.g. flipping a fair coin  
The **probability mass function (PMF) `f`** over possible outcomes **k** is:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/614e0c64d59f0ff2e926deafcb2de6e502394fac)  
**k** = success - outcome you want to keep track of (1 = success)  
**p** = probability of success (probability of failiure is 1-p)  
Every Bernoulli trial must be an **independant event**  


<img src="img/bernoulli_distribution.png" alt="Bernoulli Distribution" width="75%" height="auto" class="blog-image">

**Uniform Distribution**:  

See NumPy section for creating random distributions in Python  

Good to formalise **events with equal probability**  
e.g. drawing a heart, diamond, club, or spade from a deck of cards,  
$\;\;\;\;$ or rolling a number on a dice  
Has **one parameter n (the number of events)** where each event has the **same probability**  
from the set of realisation {a-b}, (otherwise probability is zero)  
**probability mass function (PMF) `f`**:  
![](https://www.math.net/mj/Zih4KSA9IFxmcmFjMW4gXCAsIFwgXHRleHR7eCA9IDEsIDIsIDMsIC4uLiwgbn0=_100.svg)  
**n** = number of events  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1f/Uniform_discrete_pmf_svg.svg/488px-Uniform_discrete_pmf_svg.svg.png)

**Poisson Distribution**:  

See NumPy section for creating random distributions in Python  

Good to formalise **events occurring in a fixed interval of time (or space), or other specified interval types such as distance, area or volume**  
e.g. Number of patients visiting the GP between 10-11am  
$\;\;\;\;$or Number of rainy days in Edinburgh in a year  
**probability mass function (PMF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c429d187b5d4ef8ddea32a2d224f423cf9fe5b0)  
Valid **only for values on the x-axis** 

e is Euler's number (e = 2.71828...)  
k is the number of occurrences  
k! is the factorial of x  
λ (sometimes written μ) is a potitive number equal to the expected value (EV) of X when that is also equal to its variance   
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2debd3f9adf97c8af4919aa69ed4a7121b47a737)

![](https://wsproject.org/images/poisson3.gif)

**Continuous probability distributions** include:  

* Continuous Uniform Distribution  
* Gaussian Distribution  

**Continuous Uniform Distribution**:  

The distribution describes an experiment where there is an **arbitrary outcome that lies between certain bounds**  
The **bounds are** defined by the parameters, **a and b**, which are the **minimum and maximum values**  
**probability density function (PDF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b701524dbfea89ed90316dbc48c5b62954d7411c)  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Uniform_Distribution_PDF_SVG.svg/375px-Uniform_Distribution_PDF_SVG.svg.png)  

**Gaussian Distribution**:  

See NumPy section for creating random distributions in Python  

For a **real-valued** (Rational and irrational numbers) random variable 
Informally called a bell curve, but there are other types of bell shaped distributions  
**probability density function (PDF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/00cb9b2c9b866378626bcfa45c86a6de2f2b2e40)  

**μ** (Mu) is the **mean** or expectation of the distribution (and also its median and mode)  
**σ** (Sigma) is the **standard deviation**  

When **μ=0 and σ=1**, this is called **Normal Distribution (Z)**  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Normal_Distribution_PDF.svg/330px-Normal_Distribution_PDF.svg.png)  
Red curve is the **Standard normal distribution**  

**Normal distribution:**  
![](https://i.insider.com/546e68776bb3f74f68b7d0ba?width=769&format=jpeg)  

**Expected value**:  

The return you can expect for some kind of action  
Generalised as the weighted average  
The **basic expected value** formula:  
The probability of an event multiplied by the amount of times the event happens  
$ E(X) = P(x) * n $  

The formula changes slightly according to what kinds of events are happening.
For **discrete binomial events** (2 outcomes):  
$ E(X) = P(x) * X $   

For **discrete multiple events** (multiple probabilities):  
$ E(X) = \sum X * P(X) $  

**P(x)** = probability of success  
**X** = number of trials  

For a **continuous random variable**:  
![](https://study.com/cimages/multimages/16/visual4-1.png)  

The curve is esscentially broken up into smaller and smaller intervals and the weighted average is calculated similar to discrete distribution  4

**Mode**:  

Mode is the value with the highest probability (this will be in the center of a symetric distribution)  

Single mode = **Unimodel**  
Two or more modes = **Multimodel**  

**Variance**:  

Quantifies the spread around the mean  
Defined as the mean of the squared difference between the mean and the data  
For **Discrete** random variable:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2577f2b00102ca127d8867a756b85e17d97eab5f)  
**μ** = expected value  

For **Continuous** random variable:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/15af4223be86b41d179dfd36b2ecbc27fd2d467a)  
**f(x)** = PDF  

**Medium**:  

The **middle value** in a sorted, ascending or descending, list of values  
![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Finding_the_median.png/330px-Finding_the_median.png)  

![](https://ubalt.pressbooks.pub/app/uploads/sites/11/2020/12/ch29a-redone.png)  

**Pearson correlation coefficient (PCC)**:  

A measure of **linear correlation** between two sets of data  
It is the ratio between the covariance of two variables and the product of their standard deviations; thus it is essentially a normalized measurement of the covariance, such that the result always has a value between −1 and 1  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b9c2079a3ffc1aacd36201ea0a3fb2460dc226f)  
Where:
**n** = sample size  
**x<sub>i</sub>, y<sub>i</sub>** = individual sample points indexed with *i*  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5792e9289b8786ab64a5ef4e0cd083f9c151062e) = (the sample mean); and analogously for ȳ  

Does not exactly mean that one event causes the other (but we can have an idea)  
Values closer to $\pm$1 = high correlation  
Values closer to 0 = low correlation  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Correlation_coefficient.png/600px-Correlation_coefficient.png)

[<p style="text-align: right;">**⬆ Top of Page ⬆**</p>](#Basic-Statistics)

---

---
title: "Plotting and Distributions"
date: 2023-03-16T23:40:01-04:00
draft: False
---

<center>
&#x200B;
<img src="/images/outreach/plotting.png" alt="A Futuristic Classroom" style="width:700px;"/>
</center>

<!-- add a line drop -->
<center>
&#x200B;
</center>

We will spend a moment to study different ways of visually describing data using plots. Here we will develope some Python programming techniques to create some data to be used for plotting. In specific, we will look at several types of plots and then decide what types of features each plot has and how it could be helpful when describing data.

### Making random data for plotting
We first begin by making come random data which we could use for plotting later. There are different types of data to create. For instance, we will make data from several types of __distributions__. A [distribution](https://www.ibm.com/docs/en/SSEP7J_11.1.0/com.ibm.swg.ba.cognos.ug_ca_dshb.doc/statisticaldistribution.html) type provides a statistical vocabulary which describes which values are common, and which are uncommon for a field of numbers.

---


## Normal Distribution

``` python
x_axis = np.arange(-20, 20, 0.01)
  
# Calculating mean and standard deviation
from numpy import random

mean = statistics.mean(x_axis)
sd = statistics.stdev(x_axis)
norm.pdf(x_axis, mean, sd)

x = random.normal(size=(2, 3))
print(x)
```

### Line

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
import statistics
  
# Plot between -10 and 10 with .001 steps.
x_axis = np.arange(-20, 20, 0.01)
  
# Calculating mean and standard deviation
mean = statistics.mean(x_axis)
sd = statistics.stdev(x_axis)
age = norm.pdf(x_axis, mean, sd)

# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Normal Distribution')

plt.plot(x_axis, age )
plt.show()
```

### Histogram

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
import statistics
  
# Plot between -10 and 10 with .001 steps.
x_axis = np.arange(-10, 10, 0.01)
ages = random.normal(size=(2000,1))

# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Normal Distribution')

plt.plot(x_axis, ages)
plt.show()
```


## Binomial Distribution

``` python
from numpy import random
x = random.binomial(n=10, p=0.5, size=10)
print(x)
```


### Histogram (Bar Chart)

``` python
from numpy import random
import matplotlib.pyplot as plt

# frequencies
ages = list(random.binomial(n=10, p=0.5, size=1000))
print(f"The data in the variable ages : {ages}, {type(ages)}")  
 
# setting the ranges and no. of intervals
range = (0, 10)
bins = 50

# plotting a histogram
plt.hist(ages, bins, range, color = 'blue', histtype = 'bar', rwidth = 0.8)
  
# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Binomial Distribution')
  
# function to show the plot
plt.show()
```

---

## Poisson Distribution

``` python
from numpy import random
x = random.poisson(lam=2, size=10)
print(x)
```


### Histogram

``` python
from numpy import random
import matplotlib.pyplot as plt

# frequencies
ages = random.uniform(size=(2, 10)) #size(y_max, x_iterations)
print(f"The data in the variable ages : {ages}, {type(ages)}")  
 
# setting the ranges and no. of intervals
range = (0, 20)
bins = 1

# plotting a histogram
plt.hist(ages, bins, range,  histtype = 'bar', rwidth = 1)
  
# x-axis label
plt.xlabel('age')

# frequency label
plt.ylabel('No. of people')

# plot title
plt.title('A Uniform Distribution')
  
# function to show the plot
plt.show()
```

---

## Uniform Distribution

``` python
import numpy as np
x = np.random.uniform(0.01, 0.99, 1000) 
print(x)
```

### Line Plot

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
import statistics
  
# Plot between -10 and 10 with .001 steps.
x_axis = np.arange(-10, 10, 0.01)
ages = random.uniform(size=(2000,1))

# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Uniform Distribution')

plt.plot(x_axis, ages)
plt.show()
```

### Histogram Plot

``` python
import numpy as np 
import matplotlib.pyplot as plt 
 
values = np.random.uniform(0.01, 0.99, 1000) 
count, bins, ignored = plt.hist(values, 20, density=True)
plt.plot(bins, np.ones_like(bins),color='r')

# add title
plt.title('Uniform Distribution')

# label the axes
plt.ylabel('Density')
plt.xlabel('Values')

# function to show the plot
plt.show()
```

### Normal Inverse Gaussian continuous random variable Distribution

``` python
from scipy.stats import norminvgauss

a, b = 1.25, 0.5
r = norminvgauss.rvs(a, b, size=10)
print(r)
```

### Line Plot

``` python
import numpy as np
from scipy.stats import norminvgauss
import matplotlib.pyplot as plt
fig, ax = plt.subplots(1, 1)

a, b = 1.25, 0.5
mean, var, skew, kurt = norminvgauss.stats(a, b, moments='mvsk')

x = np.linspace(norminvgauss.ppf(0.01, a, b),
                norminvgauss.ppf(0.99, a, b), 100)
ax.plot(x, norminvgauss.pdf(x, a, b),
       'r-', lw=5, alpha=0.6, label='norminvgauss pdf')

rv = norminvgauss(a, b)
ax.plot(x, rv.pdf(x), 'k-', lw=2, label='frozen pdf')

vals = norminvgauss.ppf([0.001, 0.5, 0.999], a, b)
np.allclose([0.001, 0.5, 0.999], norminvgauss.cdf(vals, a, b))

r = norminvgauss.rvs(a, b, size=1000)

ax.hist(r, density=True, bins='auto', histtype='stepfilled', alpha=0.2)
ax.set_xlim([x[0], x[-1]])
ax.legend(loc='best', frameon=False)
plt.show()
```

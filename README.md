import numpy as np
import matplotlib.pyplot as plt

def f(x):    #標準正規分布
    k=1/np.sqrt(6.28)
    n=np.exp(x**2)
    m=np.sqrt(n)
    l=1/m
    return l*k

def pi(x): #混合正規分布
    return 0.25*f(x)+0.75*f(x-6)


lli=[]
li=[]
x0=6#step1
t=0


while t <11000:
    u=np.random.rand() #step2
    a=np.random.rand()
    e=(a-0.5)*0.2# e~U(-a,a) a=0.1
    y=x0+e
    if u < min(1,pi(y)/pi(x0)) :
        x0=y
    else :
        x0=x0     #ここまでstep3
    t=t+1 #step4
    li.append(x0)
    lli.append(t)
plt.plot(lli,li)

plt.show()
plt.plot(x,pi(x))
plt.hist(li,width=0.5,bins=10,normed=True,alpha=0.5)
# plt.plot(x,pi(x))

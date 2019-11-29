Summary of Astra Exploiting Predictability to Optimize Deep Learning
========================================================================================
&ensp;&ensp;&ensp;&ensp;With the rapid development of DNNs (Deep Neural Networks), the software accelerators can hardly catch up with the hardware accelerators and
the need of engineering programs. Meanwhile, there are some models that can not be optimized by the current accelerators (*e.g.* cuDNN). To meet
the need of software accelerators, the authors invented a system called Astra, which can automatically optimize not only the popular models
with the comparable efforts to other accelerators, but also the models that does not fit those accelerators. **To achieve this, Astra uses multi-
version compilation, that is, run more than one version of code to test which one is the best version, and given the state space, it uses three
key techniques to keep the state space under control, guaranteeing the efficiency and are space acceptable.**

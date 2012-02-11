Iteration
=========

Using SAGE for Iteration 
------------------------

This booklet tells you how to use the free and Open-Source `SAGE mathematics software <http://www.sagemath.org/>`_
for studying iteration sequences.

To use SAGE, you first need to start the SAGE program on your computer.
You should have already installed SAGE on your computer (if not, for instructions on how to
install SAGE, see `the SAGE Installation Guide <http://www.sagemath.org/doc/installation/>`_).

This booklet assumes that the reader has some basic knowledge of iteration, 
and the principal focus of the booklet is not to explain iteration, 
but rather how to study iteration sequences using SAGE.

If you are new to iteration, and want to learn more about any of the concepts presented here, 
I would highly recommend the Open University book “Iteration” (product code MS221 chapter B1), available second-hand from from the 
`Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

Plotting iteration sequences of real functions
----------------------------------------------

We can calculate the first 10 terms of the iteration sequence x_{n+1} = x_{n}*(1 - x_{n}) (n = 0, 1, 2,...),
with initial term x_{0} = 0.5, by typing:

.. highlight:: R 

::

    > f(x) = x*(1-x)       
    > p = 0.5; print(0,p)
    > for i in range(1,10):
         newp = f(p)
         print(i,newp)
         p = newp
      (1, 0.250000000000000)
      (2, 0.187500000000000)
      (3, 0.152343750000000)
      (4, 0.129135131835938)
      (5, 0.112459249561653)
      (6, 0.0998121667496825)
      (7, 0.0898496981184161)
      (8, 0.0817767298664456)
      (9, 0.0750892963187959)

To make a plot of successive points in the iteration sequence above, we can type:

::

    > f(x) = x*(1-x)  
    > p = 0.5; mypoints = []; var('mypoint')
    > mypoint = vector([p,0]); mypoints.append(mypoint)
    > for i in range(1,10):
         newp = f(p)
         mypoint = vector([p,newp])
         mypoints.append(mypoint)
         mypoint = vector([newp,newp])
         mypoints.append(mypoint)
         p = newp
    > points(mypoints, rgbcolor=(0.2,0.6, 0.1), pointsize=30) + line(mypoints)
    
|image0|

Another example is the iteration sequence x_{n+1} = cos(x_{n}) (for n = 0, 1, 2, ...), where x_{0} = 0:

To make a plot of successive points in the iteration sequence above, we can type:

::

    > f(x) = cos(x)
    > p = 0.0; mypoints = []; var('mypoint')
    > mypoint = vector([p,0]); mypoints.append(mypoint)
    > for i in range(1,10):
         newp = f(p)
         mypoint = vector([p,newp])
         mypoints.append(mypoint)
         mypoint = vector([newp,newp])
         mypoints.append(mypoint)
         p = newp
    > points(mypoints, rgbcolor=(0.2,0.6, 0.1), pointsize=30) + line(mypoints)

|image1|

Finding fixed points of iteration sequences of real functions
-------------------------------------------------------------

A fixed point of an iteration sequence is a point for which x_{n+1} = x_{n}.

The fixed point equation of the iteration sequence x_{n+1} = x_{n}*(1 - x_{n}) is x = x*(1-x). To find the fixed point, we can solve
for x in SAGE by typing:

::

    > solve( x*(1-x) == x, x) 
      [x == 0] 

This tells us that the fixed point of iteration sequence x_{n+1} = x_{n}*(1 - x_{n}) is x=0. In this case, it happens that this is an attracting 
fixed point, and the sequence converges to the fixed point x=0 at the limit as n goes to Infinity.

Similarly, the fixed point equation of the iteration sequence x_{n+1} = 0.5*(x_{n} + (3/x_{n})) is x = 0.5*(x + (3/x)). To find the fixed point, we can solve
for x in SAGE by typing:

::

    > solve( 0.5*(x + (3/x)) == x, x) 
      [x == -sqrt(3), x == sqrt(3)]

This tells us that the fixed points are x=-sqrt(3) and x=sqrt(3). It happens that x=sqrt(3) is an attracting fixed point, and the 
sequence converges to sqrt(3) in the limit as n goes to Infinity.

Sometimes, SAGE does not give us a solution to the fixed point equation. For example, for the iteration sequence x_{n+1} = cos(x_{n})
(for n = 0, 1, 2, ...), the fixed point equation is x = cos(x). If we try to solve this in SAGE, we don't get a useful answer:

::

    > solve (cos(x) == x, x)
      [x == cos(x)]

In this case, we need to use the findroot() to solve the equation numerically. For example, to find
a solution to the equation x = cos(x) in the range 0 to pi/2, we type:

::

    > find_root(cos(x) == x,0,pi/2)
      0.73908513321516067

This tells us that a fixed point of the iteration sequence is approximately x=0.739. It happens that x=0.739 is an attracting fixed point,
and this iteration sequence will converge to x=0.73908513321516067 in the limit as n goes to Infinity. 
      
Similarly, the fixed point equation of the iteration sequence x_{n+1} = x_{n}*x_{n} - 2.4 (where n = 0, 1, 2...) is x = x*x - 2.4.
To find the fixed points we solve the fixed point equation:

::

    > solve( (x*x) - 2.4 == x, x)
      [x == -1/10*sqrt(265) + 1/2, x == 1/10*sqrt(265) + 1/2]

That is, the fixed points are x=-1/10*sqrt(265) + 1/2 and x=1/10*sqrt(265) + 1/2. In this case, the fixed points happen to be repelling
fixed points, and the iteration sequence tends to Infinity as n goes to Infinity.

Links and Further Reading
-------------------------

Some links are included here for further reading.

For background reading on iteration, I would recommend the Open University book “Iteration” (product code MS221 chapter B1), available second-hand from from the 
`Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

For an in-depth introduction to SAGE, see the `SAGE documentation website <http://www.sagemath.org/help.html#SageStandardDoc>`_.

Acknowledgements
----------------

Thank you to Noel O'Boyle for helping in using Sphinx, `http://sphinx.pocoo.org <http://sphinx.pocoo.org>`_, to create
this document, and github, `https://github.com/ <https://github.com/>`_, to store different versions of the document
as I was writing it, and readthedocs, `http://readthedocs.org/ <http://readthedocs.org/>`_, to build and distribute
this document.

Many of the examples in this document have been inspired by examples in the excellent Open University
book “Iteration” (product code MS221 chapter B1), available second-hand from from the 
`Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

Contact
-------

I will be grateful if you will send me (`Avril Coghlan <http://www.ucc.ie/microbio/avrilcoghlan/>`_) corrections or suggestions for improvements to
my email address a.coghlan@ucc.ie 

License
-------

The content in this book is licensed under a `Creative Commons Attribution 3.0 License
<http://creativecommons.org/licenses/by/3.0/>`_.

.. |image0| image:: ../_static/image0.png
.. |image1| image:: ../_static/image1.png
.. |image2| image:: ../_static/image1.png
            :width: 900



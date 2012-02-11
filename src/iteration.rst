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

Iteating real functions 
-----------------------

We can calculate the first 10 terms of the iteration sequence x_{n+1} = x_{n}*(1 - x_{n}) (n = 0, 1, 2,...),
with initial term x_{0} = 0.5, by typing:

.. highlight:: r

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

Links and Further Reading
-------------------------

Some links are included here for further reading.

For background reading on DNA sequence statistics, it is
recommended to read Chapter 1 of
*Introduction to Computational Genomics: a case studies approach*
by Cristianini and Hahn (Cambridge University Press;
`www.computational-genomics.net/book/ <http://www.computational-genomics.net/book/>`_).

For more in-depth information and more examples on using the SeqinR
package for sequence analysis, look at the SeqinR documentation,
`http://pbil.univ-lyon1.fr/software/seqinr/doc.php?lang=eng <http://pbil.univ-lyon1.fr/software/seqinr/doc.php?lang=eng>`_.

There is also a very nice chapter on "Analyzing Sequences", which
includes examples of using SeqinR for sequence analysis, in the
book *Applied statistics for bioinformatics using R* by Krijnen
(available online at
`cran.r-project.org/doc/contrib/Krijnen-IntroBioInfStatistics.pdf <http://cran.r-project.org/doc/contrib/Krijnen-IntroBioInfStatistics.pdf>`_).

For a more in-depth introduction to R, a good online tutorial is
available on the "Kickstarting R" website,
`cran.r-project.org/doc/contrib/Lemon-kickstart <http://cran.r-project.org/doc/contrib/Lemon-kickstart/>`_.

There is another nice (slightly more in-depth) tutorial to R
available on the "Introduction to R" website,
`cran.r-project.org/doc/manuals/R-intro.html <http://cran.r-project.org/doc/manuals/R-intro.html>`_.

Acknowledgements
----------------

Thank you to Noel O'Boyle for helping in using Sphinx, `http://sphinx.pocoo.org <http://sphinx.pocoo.org>`_, to create
this document, and github, `https://github.com/ <https://github.com/>`_, to store different versions of the document
as I was writing it, and readthedocs, `http://readthedocs.org/ <http://readthedocs.org/>`_, to build and distribute
this document.

Many of the ideas for the examples and exercises for this chapter
were inspired by the Matlab case studies on
*Haemophilus influenzae*
(`www.computational-genomics.net/case\_studies/haemophilus\_demo.html <http://www.computational-genomics.net/case_studies/haemophilus_demo.html>`_)
and Bacteriophage lambda
(`http://www.computational-genomics.net/case\_studies/lambdaphage\_demo.html <http://www.computational-genomics.net/case_studies/lambdaphage_demo.html>`_)
from the website that accompanies the book
*Introduction to Computational Genomics: a case studies approach*
by Cristianini and Hahn (Cambridge University Press;
`www.computational-genomics.net/book/ <http://www.computational-genomics.net/book/>`_).

Thank you to Jean Lobry and Simon Penel for helpful advice on using
the SeqinR package.

Contact
-------

I will be grateful if you will send me (`Avril Coghlan <http://www.ucc.ie/microbio/avrilcoghlan/>`_) corrections or suggestions for improvements to
my email address a.coghlan@ucc.ie 

License
-------

The content in this book is licensed under a `Creative Commons Attribution 3.0 License
<http://creativecommons.org/licenses/by/3.0/>`_.

.. |image0| image:: ../_static/P1_image0.png
.. |image1| image:: ../_static/P1_image1.png
            :width: 900



Get Started
=================

Installation
------------

We recommend using SafePilot via Docker.
Please refer to `Docker Documentation <https://docs.docker.com/>`_ for more information.
After activating docker on your computer, get the docker image using the following command:

.. code:: bash

   docker pull wxu3/safepilot


(Optional) 
If you prefer to manually configure the environment, we recommend setting it up within a virtual environment.
Please refer to `Anaconda Documentation <https://docs.anaconda.com/free/anaconda/install/index.html/>`_ for more information. After activating your virtual environment, install the required packages according to `dependencies.txt <https://en.wikipedia.org/wiki/Linear_temporal_logic/>`_.

After configuring the environment, use the following command to install SafePilot:

.. code:: bash

   git clone https://github.com/WeizheSyr/SafePilot.git


After installing SafePilot, you can use the following command to run ``hello_safepilot.py`` to verify if the environment is configured properly.

.. code:: bash

   python hello_safepilot.py


.. Important::

   SafePilot requires linux and does not support Apple M-Series CPUs.
   

Basic Concepts
--------------
First-order logic (FOL)
~~~~~~~~~~~~~~~~~~~~~~~~~~~
First-Order Logic (FOL), also known as Predicate Logic, is a formal system used in mathematics, philosophy, linguistics, and computer science to express statements about objects and their relationships. FOL extends propositional logic by including quantifiers (like "for all" (∀) and "there exists" (∃)) and predicates, which can express properties of objects and relations between them.
For more information, please refer to `First-order logic wiki <https://en.wikipedia.org/wiki/First-order_logic/>`_.


Linear temporal logic (LTL)
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Linear Temporal Logic (LTL) is a type of formalism used to describe sequences of events in a temporal (time-based) context. LTL is commonly used in the verification of systems, such as software or hardware, where the order of events matters. LTL includes temporal operators like "G" (Globally, meaning "always"), "F" (Finally, meaning "eventually"), "X" (Next, meaning "in the next state"), and "U" (Until). 
For more information, please refer to `Linear temporal logic wiki <https://en.wikipedia.org/wiki/Linear_temporal_logic/>`_.


Z3
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Z3 is a theorem prover from Microsoft Research. We utilize the Z3 Python API to verify whether the output of the LLM satisfies the FOL constraints. Please refer to `Z3 <https://github.com/Z3Prover/z3/>`_ for more information.


Spot
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Spot is a C++17 library for LTL, ω-automata manipulation and model checking. We utilize the Spot Python API to verify whether the output of the LLM satisfies the LTL constraints. Please refer to `Spot <https://spot.lre.epita.fr/index.html/>`_ for more information.


Q&A
~~~~~~~~~~~~~~~
1. TypeError: 'max_iters' is an invalid keyword argument for this function

Line 149 in src/cpsim/controllers/LP_cvxpy.py
"max_iter" to "max_iters" or "max_iters" to "max_iter"



2. NameError: name 'imath' is not defined

go to "anaconda3/envs/demo3/lib/python3.8/site-packages/cpsim/models/nonlinear/vessel.py" in your anaconda's path
add "from interval import imath, interval" in line 8.


Get Started
=================

Installation
------------

We recommend using SafePilot via Docker.
Please refer to `Docker Documentation <https://docs.docker.com/>`_ for more information.
After activating docker on your computer, install SafePilot using the following command:

.. code:: bash

   docker pull safepilot


(Optional) 
If you prefer to manually configure the environment, we recommend setting it up within a virtual environment.
Please refer to `Anaconda Documentation <https://docs.anaconda.com/free/anaconda/install/index.html/>`_ for more information. After activating your virtual environment, install the required packages using the following command:
 install CPSim with the following command:

.. code:: bash

    pip install cpsim[interval]



Minimum Simulation
------------------
After installing CPSim, you can write the following code to simulate the behaviours of a continuous stirred tank reactor.

.. literalinclude:: ../../src/examples/1_CSTR_simulation.py
    :language: python
    :name: 1_CSTR_simulation.py
    :caption: Minimum simulation example
    :emphasize-lines: 13,15,16
    :linenos:

First, we import a built-in nonlinear CSTR model at Line 3.
Then, we configure some simulation parameters, such as sampling time :math:`dt`, at Lines 6-9.
At Line 10, we create a simulation object with the model and the parameters.

The main control loop is at Lines 12-16.
In each iteration of the loop, it updates the reference state, and evolves the system a sampling time advance.

After simulation, the reference state, output, system state, and control input are stored in the simulation object.
Here, we plot the reference state and the output at Lines 26-28.

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


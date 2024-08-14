Block World Problem
~~~~~~~~~~~~~~~~~~~~

In this problem, we require the LLM to generate a plan to control a robotic arm to stack blocks on a plane as specified.


We read the prompt from ``first_prompt_formula.txt`` and instruct the LLM to generate FOL specifications in the format required by the Z3 Python API.

After manually checking the correctness of the generated specification, we proceed to request the LLM to generate a plan using prompt from ``first_prompt_plan.txt``.

The specific problem is as follows.

.. code:: json

    (define (problem BW-rand-6)
    (:domain blocksworld-4ops)
    (:objects b1 b2 b3 b4 b5 b6 )
    (:init
    (arm-empty)
    (on b1 b6)
    (on b2 b3)
    (on-table b3)
    (on b4 b1)
    (on-table b5)
    (on-table b6)
    (clear b2)
    (clear b4)
    (clear b5)
    )
    (:goal
    (and
    (on b1 b2)
    (on b5 b3)
    (on b6 b4))
    )
    )


The figure below shows the initial state and the goal state of the problem.

.. image:: images/5_example/block.png
   :width: 650 px
   :align: center
   :alt: Block World Problem


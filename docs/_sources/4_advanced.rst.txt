Custom Components
=================

Target new problems
-------------------
We can define a new controller by inheriting the ``Controller`` class.
1. Create a new Python file to invoke the various components, define parameters for calling the LLM, and specify prompts for the interactions.

2. Create new files to store the initial prompt for querying the formula specification and the initial prompt for querying the motion plan results.

3. Customize FOL verifier if your constraints are expressed in FOL.
Functions to be customized in ``Fol_verifier`` class.

.. code:: python

    # Return problem from raw_problem
    # Customize according to each specific tasks
    def get_problem(self):
        pass
    
    # Return plan list from raw_plan
    # Customize according to each specific tasks
    def get_plan(self):
        pass
    
    # Set states from plan
    # Customize according to each specific tasks
    def set_states(self):
        pass
    
    # Set the initial state
    # Customize according to each specific tasks
    # Return the initial state
    def set_initial_state(self, s):
        pass
    
    # Set the goal state
    # Customize according to each specific tasks
    # Return the goal state
    def is_goal_state(self, s):
        pass
    
    # Populate self.steps based on the obtained plan, 
    # with each entry comprising (action, *args, s_prev, s_next), 
    # representing the action, action objects, previous state, and next state, respectively.
    def set_states(self):
        pass
    
    # Generate reasoning according to wrong_steps
    def reasoning(self, wrong_steps):
        pass

4. Customize LTL verifier if your constraints are expressed in LTL.
Functions to be customized in ``LTL_verifier`` class.

.. code:: python

    # Return atomic proposition list from problem
    # Customize according to each specific tasks
    def get_aps(self, problem_path):
        pass
    
    # Return plan list from raw_plan
    # Customize according to each specific tasks
    def get_plan(self):
        pass

    # Return !formula
    def get_aformula(self):
        aparsed_formula = spot.formula.Not(self.formula)
        # aformula = spot.translate(self.formula, dict=self.d)
        aformula = spot.translate(aparsed_formula, dict=self.d)
        return aformula
    
    # Return state list
    # Customize according to each specific tasks
    def get_states(self, bdd_ithvar_list):
        pass

    # Generate reason according to the wrong steps
    # Customize according to each specific tasks
    def reasoning(self, wrong_steps):
        pass

For complete examples, please refer to the source code of the examples.

* Invoke components, such as `auto.py <https://github.com/WeizheSyr/SafePilot/blob/main/src/examples/case1/auto.py>`_.
* First prompt for getting logic specification, such as `first_prompt_formula.txt <https://github.com/WeizheSyr/SafePilot/blob/main/src/examples/case1/first_prompt_formula.txt>`_.
* First prompt for getting plan, such as `first_prompt_plan.txt <https://github.com/WeizheSyr/SafePilot/blob/main/src/examples/case1/first_prompt_plan.txt>`_.
* FOL verifier, such as `case1/verifier.py <https://github.com/WeizheSyr/SafePilot/blob/main/src/examples/case1/verifier.py>`_.
* LTL verifier, such as `case2/verifier.py <https://github.com/WeizheSyr/SafePilot/blob/main/src/examples/case2/verifier.py>`_.

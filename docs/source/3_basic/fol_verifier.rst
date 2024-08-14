FOL Verifier
~~~~~~~~~~~~~~~~~~~~
This component is implemented by the Fol_verifier class, responsible for verifying whether the output of the LLM satisfies the FOL constraints. This component, based on the Z3 Python API, implements the template for the entire verification process and the core verification functions. 

Users need to extract and populate each step's state, as well as the initial and goal states, from the problem and plan provided in natural language. By calling the verification() function, the component returns the verification results and identifies the specific step that violates the specification. Then generate reasoning based on user requirements.

Custom functions required:
~~~~~~~~~~~~~~~~~~~~

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
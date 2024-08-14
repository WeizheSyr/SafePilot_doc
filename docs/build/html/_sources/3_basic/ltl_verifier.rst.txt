LTL Verifier
~~~~~~~~~~~~~~~~~~~~
This component is implemented by the LTL_verifier class, responsible for verifying whether the output of the LLM satisfies the LTL constraints. This component, based on the Spot Python API, implements the template for the entire verification process and the core verification functions. 

Users need to extract and populate each step's state and transitions, from the problem and plan provided in natural language. By calling the verification() function, the component returns the verification results and identifies the specific step that violates the specification. Then generate reasoning based on user requirements.

Custom functions required:
~~~~~~~~~~~~~~~~~~~~

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
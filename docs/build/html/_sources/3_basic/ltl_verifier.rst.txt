LTL Verifier
~~~~~~~~~~~~~~~~~~~~
This component is implemented by the LTL_verifier class, responsible for verifying whether the output of the LLM satisfies the LTL constraints. This component, based on the Spot Python API, implements the template for the entire verification process and the core verification functions. 

Users need to extract and populate each step's state and transitions, from the problem and plan provided in natural language. By calling the verification() function, the component returns the verification results and identifies the specific step that violates the specification. Then generate reasoning based on user requirements.


.. Important::

   Some functions require customization and will be detailed in the Custom Component section.

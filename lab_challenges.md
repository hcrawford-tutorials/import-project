# Import is Important Tutorial
## Lab: Animal Classification System

## Challenges and Extensions

### Challenge 1: The `__all__` Variable
Research the special `__all__` variable in Python packages.

**Experiment:**
1. Research what `__all__` does in a Python module
2. Implement `__all__` in one of your package's `__init__.py` files
3. Test what happens when you use `from package import *`
4. Compare the behavior with and without `__all__` defined

**Questions:**
- What gets imported when you use `*` if `__all__` is defined?
- What gets imported if `__all__` is not defined?
- Why might `__all__` be useful in a large codebase?
- When might you want to exclude certain items from `*` imports?

### Challenge 2: Multi-Level Attribute Hierarchy
Currently, you have shared attributes at the classification level (fish, mammals, etc.). What about attributes that apply to all cold-blooded or all warm-blooded animals?

**Challenge:**
1. Create shared attributes at the temperature-regulation level (cold-blooded, warm-blooded)
2. Make these higher-level attributes accessible to all animals in those categories
3. Handle potential naming conflicts between different levels

**Questions:**
- If multiple levels define the same attribute name, which one takes precedence?
- How can you design your hierarchy to avoid conflicts?
- Can an animal access attributes from multiple levels of the hierarchy?

### Challenge 3: Circular Import Prevention
**Experiment:**
1. Try to create two modules that import from each other
2. Observe and document what happens
3. Research strategies to prevent or resolve circular imports
4. Implement a solution

**Questions:**
- When do circular imports become a problem?
- What error messages do you see?
- What are some architectural patterns to avoid circular dependencies?

### Challenge 4: Dynamic Module Access
Write code that can dynamically load modules based on string names.

**Goal:** Create a function that takes a classification name as a string and returns the appropriate module, so you can write code like:

```python
fish = get_classification("fish")
print(fish.has_scales)
```

**Hints:**
- Research the `importlib` module
- Consider how to construct import paths programmatically
- Think about error handling for invalid classification names

---
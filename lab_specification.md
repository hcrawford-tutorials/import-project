# Import is Important Tutorial
## Lab: Animal Classification System

### Learning Objectives
By the end of this lab, you will be able to:
- Create a multi-level package structure using directories and `__init__.py` files
- Understand the difference between modules (`.py` files) and packages (directories with `__init__.py`)
- Use relative imports to share code between modules in the same package
- Control namespace visibility using `__init__.py` files
- Import modules and attributes using various import syntaxes
- Understand how Python's import system affects attribute access

### Overview
In this lab, you'll create a package structure that models the biological classification of vertebrate animals. You'll organize animals into a hierarchy that mirrors taxonomic relationships, and learn how Python's import system allows you to access attributes and modules at different levels of the hierarchy.

### Background: Animal Classification
Vertebrates are animals with backbones. They can be classified into two main categories based on body temperature regulation:

**Warm-Blooded Vertebrates:**
- Birds (e.g., parrot, robin)
- Mammals (e.g., lion, seal)

**Cold-Blooded Vertebrates:**
- Fish (e.g., shark, pufferfish)
- Amphibians (e.g., frog, salamander)
- Reptiles (e.g., lizard, snake)

### Lab Structure

You'll create a package hierarchy that mirrors the biological classification of vertebrates. The structure, as shown in the following diagram, organizes vertebrates by their characteristics (warm-blooded vs. cold-blooded) and then by their specific classification (fish, mammals, birds, etc.).

![Vertebrates Classification](.devcontainer/vertebrates.png)

**Your Goal:** Design and implement a package structure where:
- Each level of classification is represented by a package (directory with `__init__.py`)
- Individual animals are modules (`.py` files)
- Shared characteristics for each classification are stored in a way that all animals in that group can access them
- You can import animals and their attributes at different levels of the hierarchy

You'll also create a `main.py` file at the root of your workspace to test your package structure.

---

## Part 1: Understanding Packages vs. Modules

### Task 1.1: Create the Basic Structure
1. Design a directory hierarchy that represents the animal classification system
1. Create the necessary directories and files to make your hierarchy into valid Python packages

**Hints:**
- Think about how to represent the hierarchical relationship: animals → vertebrates → temperature regulation → specific classification → individual animals
- What file is needed in each directory to make it a regular package?
- Would a namespace package work better? Why or why not?

### Task 1.2: Create Your First Module
Let's start with a simple example: create a module for the shark.

1. Decide where the shark module should live in your hierarchy
2. Create the module file and add attributes that describe a shark (e.g., species name, size)
3. Add a print statement to the module so you can observe when it gets imported
4. Create `main.py` and experiment with importing your shark module
5. Try to access the shark's attributes from `main.py`

**Exploration Questions:**
- When does the print statement execute?
- What's the full path needed to access attributes?
- What happens if you import the same module twice?
   - Consider examining the output of `sys.modules` and `locals().keys()`

---

## Part 2: Sharing Attributes Within a Package

Each classification level should have attributes that apply to all animals in that category. For example, all fish share certain characteristics, while all mammals share different characteristics.

### Task 2.1: Create Shared Attributes
Use the classification diagram above to see some characteristics that all fish share. Create a way to store these shared attributes so that individual fish modules can access them.

**Challenge:** Where should you put these shared attributes? How should you name the file or module?

### Task 2.2: Import Attributes into a Module
Now make your shark module able to access the shared fish attributes. Experiment with different import approaches:

**Approach 1:** Import the entire attributes module
- Try importing the attributes as a module object
- Access attributes through that module object
- Question: Can you access attributes directly on the shark, or do you need to go through the attributes module?

**Approach 2:** Import specific attributes
- Import individual attributes from the shared module
- Try accessing these attributes directly
- Question: What's the difference in how you access these attributes compared to Approach 1?

**Approach 3:** Import everything at once
- Import all attributes from a module at once
- Question: What are the trade-offs of this approach?

**Exploration Questions:**
- What does the dot (`.`) mean in import statements?
- What's the difference between relative and absolute imports?
- Which approach makes the most sense for your use case and why?

---

## Part 3: Package-Level Imports with `__init__.py`

Right now, to access specific animals, you might need to import the full path. Let's explore how `__init__.py` can control what's accessible when you import a package.

### Task 3.1: Make Modules Accessible at Package Level
**Goal:** Be able to import the fish package and access individual fish (like shark) through it, without having to import the full path to each fish.

**Experiment:**
1. Try importing just the fish package and accessing the shark module through it
2. If this doesn't work initially, research how `__init__.py` can help
3. Modify the appropriate `__init__.py` file to make individual fish modules accessible

**Exploration Questions:**
- What happens when you import a package?
- What role does `__init__.py` play in controlling access?
- Can you still use the long import path if you want to?

### Task 3.2: Make Attributes Accessible at Package Level
**Goal:** Be able to access shared fish attributes (like `has_scales`) directly from the fish package, not just from individual fish modules.

**Experiment:**
1. Try accessing a shared attribute directly from the fish package
2. If it doesn't work, figure out what you need to add to `__init__.py`
3. Make it so attributes are accessible at multiple levels (both from the package and from individual modules)

**Exploration Questions:**
- At how many different levels can you now access `has_scales`?
- Draw or describe the namespace hierarchy
- What are the benefits and drawbacks of making attributes available at multiple levels?

---

## Part 4: Complete the Classification System

### Task 4.1: Implement All Animal Modules
Expand your package to include all the animals from the vertebrates classification system diagram above. Each animal should:
1. Be represented as its own module
2. Have access to its classification's shared attributes
3. Have at least two unique attributes specific to that animal species

### Task 4.2: Define Shared Attributes for Each Classification
For each of the five classifications, use the classification diagram determine the attributes that are shared by all animals in that group, and create a way to store and share those attributes.

### Task 4.3: Make Everything Accessible
For each classification package, configure the package initialization so that:
1. All individual animal modules can be accessed through the package
2. All shared attributes can be accessed at the package level
3. The import paths are as convenient as possible for users of your package

**Challenge:** Can you make it so someone can write `import animals.fish as fish` and then access both `fish.shark.species_name` and `fish.has_scales`?

---

## Part 5: Testing Your Package Structure

### Task 5.1: Create a Comprehensive Test Script
Create a `main.py` file that demonstrates you can:

1. **Import entire classifications** and access their shared attributes
2. **Access individual animals** through their classification packages
3. **Compare different classifications** by showing attributes from different groups
4. **Show the full hierarchy** by accessing attributes at multiple levels (package level and module level)

Your test script should clearly demonstrate that:
- Shared attributes are accessible at the classification level
- Individual animals can be accessed through their packages
- Each animal has both shared attributes and unique attributes
- The hierarchy works for both warm-blooded and cold-blooded vertebrates

### Task 5.2: Experiment with Different Import Styles
Python offers multiple ways to import modules and attributes. Experiment with different import styles to understand their trade-offs:

**Experiment with:**
1. Importing the full path to a module
2. Importing with an alias
3. Importing a package and accessing modules through it
4. Using `from ... import ...` syntax
5. Importing specific attributes directly

**For each style, consider:**
- Readability: How clear is it where the attribute comes from?
- Convenience: How much typing is required?
- Namespace pollution: What names are added to your current namespace?
- Flexibility: How easy is it to access multiple items?

---

## Part 6: Challenges and Extensions

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

## Part 7: Reflection Questions

After completing the lab, reflect on these questions:

1. **Namespace Management:**
   - How does Python's import system help organize large codebases?
   - What are the trade-offs between deep package hierarchies vs. flat structures?

2. **Import Strategies:**
   - When would you use `from .attributes import *` vs. explicit imports?
   - How do you balance convenience vs. clarity in import statements?

3. **Package Design:**
   - How does `__init__.py` give you control over your package's public API?
   - Why might you want to hide certain modules or attributes from package-level access?

4. **Real-World Applications:**
   - How is this package structure similar to organizing a large web application?
   - Can you think of other domains (besides biology) where this hierarchical structure would be useful?

---

## Deliverables

When you complete this lab, you should have:

1. **A complete package structure** that:
   - Organizes animals hierarchically by classification
   - Uses `__init__.py` files to make directories into packages
   - Allows imports at different levels of the hierarchy

2. **At least 10 animal modules** (2 per classification):
   - Fish, Amphibians, Reptiles, Birds, Mammals
   - Each with unique attributes appropriate to that species

3. **Shared attributes for each classification** that:
   - Are accessible to all animals in that classification
   - Can be accessed at the package level
   - Reflect the biological characteristics of that group

4. **A working main.py** that demonstrates:
   - Importing packages with aliases
   - Accessing shared attributes at the package level
   - Accessing individual animals and their attributes
   - Multiple import styles and their trade-offs

5. **Understanding of key concepts** including:
   - The difference between modules and packages
   - How `__init__.py` controls namespace visibility
   - When to use relative vs. absolute imports
   - Trade-offs between different import styles

---

## Common Pitfalls and Tips

### Pitfall 1: Forgetting `__init__.py`
**Problem:** Import fails with "No module named 'animals'"
**Solution:** Ensure every directory in the package hierarchy has an `__init__.py` file

### Pitfall 2: Incorrect Relative Imports
**Problem:** `ImportError: attempted relative import with no known parent package`
**Solution:**
- Relative imports (`.` syntax) only work within packages
- Always run your code from outside the package directory
- Use `python main.py`, not `python animals/vertebrates/...`

### Pitfall 3: Accessing Unimported Modules
**Problem:** `AttributeError: module 'animals.vertebrates.cold-blooded.fish' has no attribute 'shark'`
**Solution:** Make sure `__init__.py` imports the shark module: `from . import shark`

### Pitfall 4: Confusing Module and Attribute Names
**Problem:** Unclear whether `fish.environment` refers to an attribute or a module
**Solution:** Use clear naming conventions (e.g., modules are nouns, attributes might be `has_` or `is_` prefixed)
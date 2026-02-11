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

### Setup Instructions

1. Follow these [setup instructions](./setup.md), then return here to get started
1. Navigate to the new `animal-classification` directory in your terminal
1. You'll build your entire package structure from scratch in this directory

### Overview
In this lab, you'll create a package structure that models the biological classification of vertebrate animals. You'll organize animals into a hierarchy that mirrors taxonomic relationships, and learn how Python's import system allows you to access attributes and modules at different levels of the hierarchy.

### Lab Structure

You'll create a package hierarchy that mirrors the biological classification of vertebrates, which are animals with backbones. The structure, as shown in the following diagram, organizes vertebrates by their characteristics (warm-blooded vs. cold-blooded) and then by their specific classification (fish, mammals, birds, etc.).

![Vertebrates Classification Diagram](.devcontainer/vertebrates.png)

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
1. Create only the package structure - you'll create the modules in later tasks

**Hints:**
- Think about how to represent the hierarchical relationship: animals → vertebrates → temperature regulation → specific classification → individual animals
- What file is needed in each directory to make it a regular package?
- Would a namespace package work better? Why or why not?

##### Success
You'll know you succeeded when:
1. You can import your package hierarchy without errors
1. Running `python3.14 -c "import vertebrates"` completes without error

### Task 1.2: Create Your First Module
Let's start with a simple example: create a module for the shark.

1. Decide where the shark module should live in your hierarchy
1. Create the module file and add attributes that describe a shark (e.g., the attributes from the diagram). The attributes can be represented with any names and data types you choose.
1. Add a `print` statement to the shark module to observe when it gets imported. This is usually the first line in the file so it runs before any `import` statements.
1. Import the shark module in `main.py` and add print statements to display shark attributes

##### Success
You'll know you succeeded when:
1. Running `main.py` prints the shark's attributes without errors.

##### Reflection
- Are you accessing the attributes with the fully qualified import (e.g., `vertebrates.cold_blooded.fish.shark.has_fins`)? If so, how can you change the `import` statement so you can refer just to the attribute (e.g., `has_fins`)? How would the `import` statement change if you wanted to refer to them with the animal name (e.g., `shark.fins`)?
- When does each `print` statement execute? Was this what you expected? Why or why not?
- What's the full path needed to access attributes?
- What happens if you import the same module twice?
   - Consider examining the output of `sys.modules` and `locals().keys()`
- What exception do you get if you try to import an attribute that doesn't exist?

---

## Part 2: Sharing Attributes Within a Package

Each classification level has attributes that apply to all animals in that category. For example, all fish share certain characteristics, while all mammals share different characteristics.

### Task 2.1: Create Shared Attributes
Use the classification diagram above to see some characteristics that all fish share. Create a way to store these shared attributes so that individual fish modules can access them.

**Challenge:** Where should you put these shared attributes? How should you name the file or module?

### Task 2.2: Import Attributes into a Module
Now make your shark module able to access the shared fish attributes. Experiment with different import approaches:

**Approach 1:** Import the entire attributes module into the `shark` module
- Try importing the attributes as a module object in your shark module
- In `main.py`, import the shark module and update the `print` statements to print out the attributes
- Question: Can you access attributes directly on the shark, or do you need to go through the attributes module?

**Approach 2:** Import specific attributes into the `shark` module
- Import individual attributes from the shared module into the `shark` module
- In `main.py`, try accessing these attributes directly from the shark module first using an absolute import statement, then with a relative import statement.
- Question: What's the difference in how you access these attributes compared to Approach 1?
- Question: Do you prefer the absolute or the relative import? Why?

**Approach 3:** Import everything at once
- Import all attributes from the attributes module into the shark module without specifying them individually
- Question: What are the trade-offs of this approach?

##### Success
You'll know you succeeded when:
1. You've tried each of the three approaches listed above and understand the differences between each approach.

##### Reflection
- What does the dot (`.`) mean in import statements?
- What's the difference between relative and absolute imports?
- Which approach makes the most sense for your use case and why?

---

## Part 3: Package-Level Imports with `__init__.py`

Right now, to access specific animals, you might need to import the full path. Let's explore how `__init__.py` can control what's accessible when you import a package.

### Task 3.1: Make Modules Accessible at Package Level
**Goal:** Be able to import the fish package into `main.py` and access individual fish (like shark) through it, without having to import the full path to each fish.

**Experiment:**
1. Try importing just the `fish` package into `main.py` and access the `shark` module through it. Try both absolute and relative imports. 
2. If this doesn't work initially, research how `__init__.py` can help
3. Modify the appropriate `__init__.py` file to make individual fish modules accessible

##### Reflection
- What happens when you import a package?
- What role does `__init__.py` play in controlling access?

### Task 3.2: Make Attributes Accessible at Package Level
**Goal:** Be able to access shared fish attributes (like `has_scales`) directly from the fish package, not just from individual fish modules.

**Experiment:**
1. In `main.py`, try accessing a shared attribute directly from the `fish` package without going through `shark`
2. If it doesn't work, figure out what you need to add to `__init__.py`
3. Make it so attributes are accessible at multiple levels (both from the package and from individual modules)

##### Reflection
- At how many different levels can you now access `has_scales`?
- Draw or describe the namespace hierarchy
- What are the benefits and drawbacks of making attributes available at multiple levels?

---

## Part 4: Complete the Classification System

### Task 4.1: Implement All Animal Modules
Expand your package to include **two animals each** from **at least three** of the five classifications the vertebrates classification system diagram above, for a total of **six animal modules**. Each animal should:
1. Be represented as its own module
1. Have access to its classification's shared attributes
1. Have the three unique attributes specific to that animal species from the classification diagram
1. Uses a variety of different import methods, including the following:
   * absolute imports
   * relative imports
   * the `from <module> import ..." structure
   * adding imports to `__init__.py`
   * modularizing code where it's beneficial and importing into the original files

**Stretch Goal:**
Complete all modules for all 10 animals in the vertebrates classification system.

##### Success
You'll know you succeeded when:
1. You have 6 - 10 animal modules (2 per classification)
2. Each animal module can be imported without errors
3. Each animal has access to its classification's shared attributes without copying them into each animal's module

### Task 4.2: Define Shared Attributes for Each Classification
For **at least three** of the five classifications, use the classification diagram to determine the attributes that are shared by all animals in that group, and create a way to store and share those attributes.

**Stretch Goal:**
Complete attributes for all 10 animals in the vertebrates classification system.

##### Success
You'll know you succeeded when:
1. You have three to five shared attribute modules/files (one per classification)
2. Attributes from the diagram are stored appropriately
3. Individual animal modules can successfully access shared attributes

### Task 4.3: Make Everything Accessible
For each classification package, configure the package initialization so that:
1. All individual animal modules can be accessed through the package
1. All shared attributes can be accessed at the package level
1. The import paths are as readable and clear as possible for users of your package

##### Success
You'll know you succeeded when:
1. You can import a classification and access individual animals through it
2. Shared attributes are accessible at the package level
3. The challenge examples `fish.shark.has_scales` and `fish.has_scales` both work

**Challenge:** Can you make it so someone can write `import vertebrates.cold_blooded.fish as fish` and then access both `fish.shark.has_scales` and `fish.has_scales`?

---

## **Stretch Goal** Part 5: Testing Your Package Structure

### Task 5.1: Create a Comprehensive Test Script
Expand your `main.py` file that you created in Task 1.2 to demonstrate that you can:

1. **Import entire classifications** and access their shared attributes
1. **Access individual animals** through their classification packages
1. **Compare different classifications** by showing attributes from different groups
1. **Show the full hierarchy** by accessing attributes at multiple levels (package level and module level)

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

#### Deliverable (Optional)
Create a file called `import_experiments.py` that demonstrates each import style with comments explaining the trade-offs you observed.

---

## Part 6: Reflection

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

---

## Deliverables

When you complete this lab, you should have:

1. **A complete package structure** that:
   - Organizes animals hierarchically by classification
   - Uses `__init__.py` files to make directories into packages
   - Allows imports at different levels of the hierarchy

2. **6-10 animal modules** (2 per classification):
   - Fish, Amphibians, Reptiles, Birds, Mammals
   - Each with unique attributes appropriate to that species

3. **Shared attributes for each classification** that:
   - Are accessible to all animals in that classification
   - Can be accessed at the package level
   - Reflect the biological characteristics of that group

4. **Stretch Goal: A working main.py** that demonstrates:
   - Importing packages with aliases
   - Accessing shared attributes at the package level
   - Accessing individual animals and their attributes
   - Multiple import styles and their trade-offs

5. **Understanding of key concepts** including:
   - The difference between modules and packages
   - How `__init__.py` controls namespace visibility
   - When to use relative vs. absolute imports
   - Trade-offs between different import styles

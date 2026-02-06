# Knowledge Representation System

A Python implementation demonstrating **knowledge representation and reasoning** using facts, rules, and forward chaining inference.

## Overview

This project implements a simple but powerful knowledge base system that:
- **Stores facts** as semantic triples: (subject, relation, object)
- **Defines rules** that derive new knowledge from existing facts
- **Performs inference** using forward chaining to discover all derivable facts
- **Queries knowledge** using pattern matching on facts

## Core Concepts

### Facts
Facts represent basic statements about the world encoded as triples:
```python
("john", "parent_of", "mary")    # John is a parent of Mary
("mary", "child_of", "john")     # Mary is a child of John
```

### Rules
Rules are inference mechanisms that generate new facts from existing ones. The system applies rules repeatedly until no new facts can be derived:
```python
Rule("parent -> child", parent_implies_child)      # If X parent_of Y, then Y child_of X
Rule("parent -> ancestor", parent_implies_ancestor)  # If X parent_of Y, then X ancestor_of Y
Rule("ancestor transitive", ancestor_transitive)   # Transitivity: X ancestor Z if X ancestor Y and Y ancestor Z
```

### Forward Chaining
The inference engine applies all rules to the current fact set, collects newly derived facts, and repeats until reaching a fixed point (no new facts are discovered).

## Architecture

### KnowledgeBase Class
```python
class KnowledgeBase:
    def add_fact(self, fact: Fact)              # Add a base fact
    def add_rule(self, rule: Rule)              # Add an inference rule
    def infer(self)                             # Run forward chaining inference
    def query(self, subject=None, relation=None, obj=None)  # Query with pattern matching
```

## Example: Family Relationships

The implementation demonstrates a family tree with relationships:

**Base Facts:**
- John is parent of Mary
- Mary is parent of Ali
- Ali is parent of Zara

**Inferred Facts:**
- Mary is child of John (from parent→child rule)
- Ali is child of Mary
- Zara is child of Ali
- John is ancestor of Mary (from parent→ancestor rule)
- John is ancestor of Ali (from transitivity)
- John is ancestor of Zara

## Usage

```python
# Create knowledge base
kb = KnowledgeBase()

# Add facts
kb.add_fact(("john", "parent_of", "mary"))
kb.add_fact(("mary", "parent_of", "ali"))

# Add rules
kb.add_rule(Rule("parent -> child", parent_implies_child))
kb.add_rule(Rule("ancestor transitive", ancestor_transitive))

# Run inference
kb.infer()

# Query results
ancestors = kb.query(relation="ancestor_of", obj="zara")
print(ancestors)  # All people who are ancestors of zara
```

## Key Features

- ✅ **Set-based fact storage** - Automatically handles duplicates
- ✅ **Rule composition** - Easily define new inference rules
- ✅ **Complete inference** - Derives all possible facts
- ✅ **Pattern queries** - Flexible querying on any combination of triple components
- ✅ **Type-safe** - Uses Python dataclasses and type hints

## Files

- [knowledge_representation.ipynb](knowledge_representation.ipynb) - Interactive notebook with examples
- [README.md](README.md) - This documentation

## Applications

This knowledge representation approach is useful for:
- Semantic web and ontology reasoning
- Expert systems and rule-based inference
- Graph databases and knowledge graphs
- Logic programming systems
- Constraint satisfaction problems

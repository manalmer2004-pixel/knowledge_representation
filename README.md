# Knowledge Representation System

A Python implementation demonstrating **knowledge representation and reasoning** using facts, rules, and forward chaining inference.

## Overview

This project implements a simple but powerful knowledge base system that:
- **Stores facts** as semantic triples: (subject, relation, object)
- **Defines rules** that derive new knowledge from existing facts
- **Performs inference** using forward chaining to discover all derivable facts
- **Queries knowledge** using pattern matching on facts


### Forward Chaining
The inference engine applies all rules to the current fact set, collects newly derived facts, and repeats until reaching a fixed point (no new facts are discovered).



## Key Features

- **Set-based fact storage** - Automatically handles duplicates
- **Rule composition** - Easily define new inference rules
- **Complete inference** - Derives all possible facts
- **Pattern queries** - Flexible querying on any combination of triple components
- **Type-safe** - Uses Python dataclasses and type hints

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

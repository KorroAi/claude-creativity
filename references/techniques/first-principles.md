# First Principles Thinking

## When to Use
Technical problems, architecture decisions, systems design. Anytime you're looking at a solution built on layers of assumptions.

## The Method
1. Identify the current solution or assumption chain.
2. Strip it down: "What is this actually doing, at the most fundamental level?"
3. Rebuild from the ground up. Ignore all existing implementations.
4. Only add back constraints that are physically or logically necessary — not just conventional.

## Example
Problem: "We need a faster database."
First principles: What is a database actually doing? Storing data and retrieving it by key. Do we need all the SQL layer? Do we even need a traditional DB? Could it be a flat file with an index? Could it be in-memory with periodic snapshots? Redis, SQLite, flat files — all valid once you strip the assumption "we need what we already have."

## Why It Works
Breaks the anchoring effect — existing solutions blind you to simpler alternatives.

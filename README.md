# PyTable

PyTable is a lightweight, dictionary‑based table structure designed to store and manage rows of data in a simple, predictable way. It acts as the internal storage layer for tools like PyData, providing a clean interface for adding, replacing, and removing entries without unnecessary complexity.

## Overview

PyTable maintains a list of rows, where each row is typically a Python dictionary. The first row is stored as the base row (bRow), and all additional rows are appended to the internal list col.

This makes PyTable ideal for:

- Lightweight data storage

- CLI tools

- Debugging utilities

- Text‑based engines

- Any system that needs simple, structured row management

Its design is intentionally minimal — no indexing logic, no formatting, no schema enforcement — just clean, direct data manipulation.

## Why PyTable?

Many applications need a simple way to store structured data without pulling in a full database or over‑engineering a custom solution. PyTable solves this by offering:

- A predictable list‑based storage model

- Simple CRUD‑style operations

- Zero dependencies

- A clean API that other tools (like PyData) can build on

Instead of juggling lists, dictionaries, and manual indexing, PyTable centralizes row management into a single, reusable component.

## Core Features

### Base Row Initialization

The first value passed to PyTable becomes the base row:
```python
self.bRow = value
self.col = [self.bRow]
```

This ensures every table starts with at least one entry.

### AddItem
Append a new row to the table:

```python
def AddItem(self, val):
    self.col.append(val)
```

### ReplaceItem
Replace an existing row by index:
```python
def ReplaceItem(self, i, val):
    self.col[i] = val
```

### RemoveItem
Clear a row by index:
```python
def RemoveItem(self, i):
    self.col[i] = {}
```
This keeps the table structure intact while marking the row as empty.

## Example

```python
from PyTable import PyTable

table = PyTable({"Name": "Potion", "Heals": 25})

table.AddItem({"Name": "Elixir", "Heals": 100})
table.ReplaceItem(0, {"Name": "Hi‑Potion", "Heals": 50})
table.RemoveItem(1)

print(table.col)
```

### Output:

```python
[
    {"Name": "Hi‑Potion", "Heals": 50},
    {}
]
```

## Class Structure

```python
class PyTable:
    def __init__(self, value):
        self.bRow = value
        self.col = [self.bRow]

    def AddItem(self, val):
        self.col.append(val)

    def ReplaceItem(self, i, val):
        self.col[i] = val

    def RemoveItem(self, i):
        self.col[i] = {}
```

(Full implementation included in repository.)

## Summary

PyTable is a minimal, dependency‑free data container designed for simple row‑based storage. It provides the foundation for tools like PyData, offering predictable behavior and a clean API for managing structured data.

Requires: Python 3.x

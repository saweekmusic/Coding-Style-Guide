# SAWEEK's Personal Python Coding Style Guide

Welcome to my personal Python style guide — a set of consistent rules and best practices tailored for me, designed to keep my code clean, readable, and ADHD-friendly.  
This guide is a living document: I’ll update it as I learn and grow. It combines ideas from established conventions (like Google’s style), but mostly it reflects what helps *me* write better code, faster.

---

## 1. Naming Conventions

- **Variables & functions:** `camelCase`  
  ```python
  userName = "Asher"
  
  def calculateTotal(price, taxRate):
      return price + (price * taxRate)
  ```
- **Constants:** `ALL_CAPS`  
  ```python
  MAX_USERS = 100
  ```
- **Classes:** `PascalCase`  
  ```python
  class UserProfile:
      def __init__(self, name):
          self.name = name
  ```

---

## 2. Indentation & Spacing

- Use **4 spaces** per indentation level (no tabs).  
  ```python
  def exampleFunction():
      if True:
          print("Indented by 4 spaces")
  ```
- **Blank lines:**  
  - 2 blank lines before class definitions  
  - 1 blank line between functions  
- Leave enough space so the code visually “breathes.”  

  ```python

  class UserProfile:
      def __init__(self, name):
          self.name = name

      def greetUser(self):
          print(f"Hello, {self.name}!")

  def calculateTax(amount):
      return amount * 0.1
  ```

---

## 3. Function & Class Definitions

- Always use `def` to define functions.  
  ```python
  def getUserAge():
      return 25
  ```
- Docstrings are mandatory for every function and class, following Google style, including `Args`, `Returns`, and `Raises` sections.  

  ```python
  def divideNumbers(a: float, b: float) -> float:
      """Divides a by b.

      Args:
          a (float): Numerator.
          b (float): Denominator.

      Returns:
          float: The division result.

      Raises:
          ValueError: If b is zero.
      """
      if b == 0:
          raise ValueError("Denominator cannot be zero.")
      return a / b
  ```

---

## 4. Imports & Constants

- Organize imports in this order with a blank line between each group:  
  1. Standard library  
  2. Third-party libraries  
  3. Local application imports  

  ```python
  import os
  import sys

  import requests

  from myproject.utils import helperFunction
  ```
- Store constants in a dedicated file for better organization.  

  ```python
  # constants.py
  MAX_CONNECTIONS = 10
  TIMEOUT_SECONDS = 5
  ```

---

## 5. Error Handling

- Catch exceptions **only when necessary**.  
- Always **log** or **raise** exceptions — never use empty `except` blocks or just `pass`.  

  ```python
  try:
      result = divideNumbers(10, 0)
  except ValueError as e:
      print(f"Error occurred: {e}")
      raise
  ```

---

## 6. Type Hints & String Formatting

- Use **type hints everywhere** to clarify code intent.  
  ```python
  def greetUser(name: str) -> str:
      return f"Hello, {name}!"
  ```
- Use **f-strings** exclusively for string formatting.  
  ```python
  age = 30
  print(f"I am {age} years old.")
  ```

---

## 7. Project Structure

- Use structured folders (`src/`, `tests/`, `configs/`, etc.) **only for bigger projects**.  
- For small projects, freestyle is fine.

  ```
  my_project/
  ├── src/
  │   └── main.py
  ├── tests/
  │   └── test_main.py
  └── configs/
      └── settings.yaml
  ```

---

## 8. Comments & Readability (ADHD-friendly)

- **Inline comments:** Use sparingly, only when a line needs clarification, separated by two spaces.  
  ```python
  total = price * quantity  # total cost calculation
  ```
- **Above-line comments:** Always add one blank line before a comment block and none after.  
  ```python

  # Calculate total price with tax
  def calculateTotal(price, taxRate):
      return price + (price * taxRate)
  ```
- **Section headers:** Use visual dividers (e.g., `# ==== Section ====`) to separate large code blocks for easy scanning.  

  ```python
  # ==== User Management Functions ====

  def createUser():
      pass

  def deleteUser():
      pass
  ```
- Avoid stacking multiple single-line comments without blank lines; prefer docstrings for longer explanations.  
- Use VS Code extensions like *Better Comments* to highlight important notes (`TODO`, `FIXME`, `NOTE`).  

**Method comments vs docstrings:**  
- Use a short comment *above* the method if you want a quick mental group or summary.  
- Always write a full docstring for the method describing args, returns, and raises.  

  ```python
  # Handle new user creation and default values
  def createUser(userId: int) -> dict:
      """
      Creates a new user in the system.

      Args:
          userId (int): The user’s ID.

      Returns:
          dict: The new user's profile data.

      Raises:
          ValueError: If the ID already exists.
      """
      pass
  ```

**Balanced comment approach:**  
- Comment to explain the *why* or tricky parts, not the *what*.  
- Write pseudocode-style comments only for complex blocks, not every line.  
- Let clear naming and decomposition reduce the need for excessive commenting.  

Example:

```python
# Loop through first 10 numbers and print double their value
for i in range(10):
    val = i * 2
    print(val)
```

---

## 9. Miscellaneous

- When unsure about blank lines between functions/classes, prioritize readability and breathing space.  
- Use comments as “mini road signs” to guide your future self.  
- This guide is a flexible tool to keep your code consistent and your brain happy!

---
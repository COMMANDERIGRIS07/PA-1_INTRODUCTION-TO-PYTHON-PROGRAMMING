
## Edited by: BASAL, EARL DAVID M.
## Section: 2ECE-B

## ===================PROGRAMMING ASSIGNMENT #1===================

## A. WORD ROTATION PROBLEM

A Python application that demonstrates string manipulation by performing a left-circular shift on an input string. It moves the leading character to the end of the word while preserving the order of all remaining characters.

## Code Explanation

```python
def rotate_word(txt):
    if not txt:
        return txt
    return txt[1:] + txt[0]
```

### 1. Guard Clause (`if not txt:`)
* **Purpose:** Handles edge cases involving empty strings (`""`).
* **Logic:** Evaluates to `True` if `txt` is empty or `None`. It returns the input as-is to prevent index errors and redundant computations.

### 2. String Slicing & Concatenation (`txt[1:] + txt[0]`)
* **`txt[1:]`:** Uses Python slicing to extract a substring starting from index 1 through the end of the string (dropping the first character).
* **`txt[0]`:** Retrieves the single character at index 0.
* **`+` Operator:** Creates a new string by joining the sliced tail with the original head at the end. Strings in Python are immutable, so this operation creates a new object rather than modifying the original in place.

### 3. Main Execution Block
* **`input("Enter a word: ")`:** Captures string input from standard input (stdin).
* **`rotate_word(user_txt)`:** Passes the user's input into the function and assigns the returned value to `result`.
* **`print(...)`:** Displays the mutated string to standard output (stdout).

---

## Execution Examples

| Input (`user_txt`) | Substring (`txt[1:]`) | First Char (`txt[0]`) | Output (`result`) |
| :--- | :--- | :--- | :--- |
| `"hello"` | `"ello"` | `"h"` | `"elloh"` |
| `"Python"` | `"ython"` | `"P"` | `"ythonP"` |
| `"A"` | `""` | `"A"` | `"A"` |
| `""` *(empty)* | N/A | N/A | `""` |


## B. USERNAME BUILDER PROBLEM

### 1. Function Overview
- **Function Name:** `make_username(first_name, last_name)`
- **Purpose:** Generates a standardized, clean username by combining a user's first and last names separated by a period (`.`).

### 2. Code Implementation
```python
def make_username(first_name, last_name):
    # Step 1 & 2: Lowercase and strip spaces from first name
    clean_first = first_name.lower().replace(" ", "")

    # Step 1 & 3: Lowercase and strip spaces from last name
    clean_last = last_name.lower().replace(" ", "")

    # Step 4: Join processed names with a single period
    return f"{clean_first}.{clean_last}"


# Interactive Input Section
first_name_input = input("Enter first name: ")
last_name_input = input("Enter last name: ")

# Execute function and output result
username = make_username(first_name_input, last_name_input)
print("Generated Username:", username)
```

### 3. Detailed Explanation for Professor
- **`.lower()` Method:** Converts all characters in both `first_name` and `last_name` to lowercase to meet standard username format requirements.
- **`.replace(" ", "")` Method:** Replaces all spaces (including leading, trailing, or middle spaces in multi-word names like "Mary Jane") with an empty string, completely purging whitespace without requiring iteration or regular expressions.
- **Formatted String (f-string):** Constructs the final output string in the format `clean_first.clean_last`.

### 4. Sample Test Cases
| Input First Name | Input Last Name | Function Call | Expected Output |
| :--- | :--- | :--- | :--- |
| `"John"` | `"Doe"` | `make_username("John", "Doe")` | `'john.doe'` |
| `"Mary Jane"` | `"Smith "` | `make_username("Mary Jane", "Smith ")` | `'maryjane.smith'` |
| `"  ALAN "` | `" TURING "` | `make_username("  ALAN ", " TURING ")` | `'alan.turing'` |

---

## C. BOOKEND SWAP PROBLEM

### 1. Function Overview
- **Function Name:** `swap_bookends(items)`
- **Purpose:** Swaps the first and last elements (the "bookends") of a given list while maintaining the exact order of all intermediate elements.

### 2. Code Implementation
```python
def swap_bookends(items):
    # Extended sequence unpacking (Requirement)
    first, *middle, last = items

    # Construct and return a NEW list with swapped endpoints
    return [last, *middle, first]


# Interactive Input Section
user_input = input(
    "Enter list items separated by spaces (minimum 2 items): "
)
items_input = user_input.split()

# Execute function and output result
result = swap_bookends(items_input)
print("Resulting List:", result)
```

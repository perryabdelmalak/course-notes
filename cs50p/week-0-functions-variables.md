# CS50P Week 0: Functions, Variables

Course: Harvard CS50's Introduction to Programming with Python

## Functions

A function is an action. You call it by name and give it arguments in parentheses.

```python
print("hello, world")
```

- `print` is the function, `"hello, world"` is the argument
- Arguments are the inputs a function works with
- Some functions have **side effects** (`print` shows text on screen) and some **return a value** (`input` gives text back)

## print

```python
print("hello")
print("hello", "world")          # hello world (space between)
print("hello", "world", sep="-") # hello-world
print("no newline", end="")      # stay on same line
```

- Named arguments like `sep` and `end` change the behavior
- To print a quote inside a string, use the other kind of quote or escape it: `"She said \"hi\""`

## input and variables

```python
name = input("What's your name? ")
print("hello, " + name)
```

- `input` shows a prompt, waits for the user, and **returns** what they typed
- `=` is **assignment**: the right side is evaluated, then stored in the name on the left
- A variable is a name for a value stored in memory
- Naming: lowercase with underscores (`first_name`), meaningful names
- `input` always returns a **string**, even if the user types a number

## Strings (str)

```python
name = "  perry abdelmalak  "
name.strip()        # remove spaces at both ends
name.capitalize()   # first letter upper
name.title()        # Each Word Capitalized
name.upper()        # ALL CAPS
name.lower()        # all lower
```

- Strings are **immutable**: methods return a new string, they don't change the old one, so assign the result: `name = name.strip()`
- Methods are functions that belong to a value, called with a dot
- Chain them: `input("Name: ").strip().title()`
- `split` breaks a string into a list: `"Ada Lovelace".split(" ")` gives `["Ada", "Lovelace"]`
- `+` joins strings, `*` repeats them: `"ha" * 3` is `"hahaha"`

## f-strings

```python
name = "Perry"
print(f"hello, {name}")
```

- Put `f` before the quote, put variables or expressions in `{}`
- Cleaner than joining with `+` or using commas
- Formatting inside braces: `f"{price:.2f}"` gives 2 decimals, `f"{big:,}"` gives commas

## int, float and conversion

- `int` is a whole number, `float` is a decimal number
- `input` gives a string, so convert before doing math:

```python
x = int(input("x: "))
y = int(input("y: "))
print(x + y)
```

- Without `int(...)`, `"1" + "2"` is `"12"` (joined text), not `3`
- Use `float(...)` for decimals
- `int("abc")` or `int("1.5")` raises a `ValueError`

## Arithmetic operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `+` | add | `5 + 2` is `7` |
| `-` | subtract | `5 - 2` is `3` |
| `*` | multiply | `5 * 2` is `10` |
| `/` | divide (always a float) | `5 / 2` is `2.5` |
| `//` | floor division | `5 // 2` is `2` |
| `%` | remainder (modulo) | `5 % 2` is `1` |
| `**` | power | `5 ** 2` is `25` |

Useful helpers:

```python
round(2.567, 2)   # 2.57
abs(-3)           # 3
max(1, 5, 3)      # 5
```

- `x += 1` is shorthand for `x = x + 1`
- `%` is handy for even/odd checks: `n % 2 == 0`
- Floats can be slightly off: `0.1 + 0.2` is `0.30000000000000004`

## Defining your own functions

```python
def hello(to="world"):
    print("hello,", to)

hello()          # hello, world
hello("Perry")   # hello, Perry
```

- `def name(parameters):` then an **indented** body
- A parameter is the variable in the definition, an argument is the value you pass in
- Default values (`to="world"`) make a parameter optional
- Define a function **before** you call it

### return

```python
def square(n):
    return n * n

print(square(3))  # 9
```

- `return` sends a value back to the caller and ends the function
- A function without `return` gives back `None`
- Printing and returning are different: `print` shows something, `return` hands it back so other code can use it

## The main() convention

```python
def main():
    name = input("What's your name? ")
    hello(name)

def hello(to="world"):
    print("hello,", to)

main()
```

- Put the program's main steps in `main()` and call it at the bottom
- This lets you define helper functions in any order, as long as `main()` runs after they are all defined
- Later weeks add `if __name__ == "__main__":` around the call

## Comments

```python
# This is a comment
x = 5  # explain why, not what
```

- Comments are ignored by Python and written for humans
- Good comments explain **why**; clear names explain **what**
- Use them to leave a `# TODO` for yourself

## Common beginner pitfalls

- Forgetting `int()` after `input()`, so `"2" + "3"` gives `"23"`
- Using `=` when you mean `==` (assignment vs comparison)
- Forgetting that `.strip()`, `.title()` etc. return a new string and don't change the original
- Mismatched quotes or a missing closing parenthesis
- Wrong indentation inside a function (Python needs it)
- Calling a function before it is defined
- Forgetting the parentheses: `main` does nothing, `main()` runs it
- Mixing up `print` (shows) and `return` (gives back)
- Misspelling a variable name, which causes a `NameError`

## Quick recap

- Functions take arguments and may return values
- `input` returns a string, convert with `int()` or `float()` for math
- Use f-strings for clean output
- Define functions with `def`, use `return` to give back values
- Wrap the program in `main()` and call it once at the end

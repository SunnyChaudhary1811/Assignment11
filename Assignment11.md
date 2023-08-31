# Assignment-11

Q1:-

The else block in a try-except statement is executed if no exceptions occur in the corresponding try block. It's useful for separating code that handles exceptions from code that executes when the try block runs successfully. For example, it can be used to execute specific actions when a file is successfully opened, separate from exception handling.


```python
try:
    file = open("data.txt", "r")
except FileNotFoundError:
    print("File not found.")
else:
    data = file.read()
    file.close()
    print("Data read successfully:", data)

```

    File not found.
    

Q2:-


Yes, a try-except block can be nested inside another. This is known as nested exception handling. It allows for handling different levels of exceptions more specifically. For example, you can handle errors related to input validation at an outer level and errors related to specific calculations at an inner level. This approach provides more detailed error handling in different parts of your code.


```python
try:
    num1 = int(input("Enter a number: "))
    try:
        num2 = int(input("Enter another number: "))
        result = num1 / num2
        print("Result:", result)
    except ZeroDivisionError:
        print("Cannot divide by zero.")
    except ValueError:
        print("Invalid input. Please enter a valid integer.")
except ValueError:
    print("Invalid input. Please enter a valid integer.")

```

    Enter a number: 78
    Enter another number: 108
    Result: 0.7222222222222222
    

Q3:-

Define a class that inherits from Exception or its subclass.
Add an __init__ method to set the error message.


```python
class MyCustomError(Exception):
    def __init__(self, message):
        self.message = message

try:
    age = int(input("Enter your age: "))
    if age < 0:
        raise MyCustomError("Age cannot be negative.")
    print("Your age:", age)
except MyCustomError as e:
    print("Custom Error:", e)
except ValueError:
    print("Invalid input. Please enter a valid integer.")

```

    Enter your age: 45
    Your age: 45
    

Q4:-

SyntaxError: Code syntax is incorrect.

TypeError: Incompatible data types.

ValueError: Inappropriate value for a function.

IndexError: Index is out of range.

KeyError: Dictionary key doesn't exist.

FileNotFoundError: File cannot be found.

ZeroDivisionError: Division or modulo by zero.

AssertionError: Assertion statement fails.

ImportError: Module cannot be imported.

MemoryError: Out of memory.

IOError: Input/output operation fails.

NameError: Name is not found.

AttributeError: Attribute reference fails.

Q5:-

Logging in Python involves recording events during program execution. It's vital in software development for:

Debugging: Identify and fix issues.

Monitoring: Track performance and health.

Auditing: Record user actions and system events.

Collaboration: Aid teamwork and communication.

Optimization: Find and fix performance bottlenecks.

Documentation: Capture program behavior.

Testing: Ensure consistent behavior over time.

The logging module offers tools to create structured logs, aiding debugging, maintenance, and collaboration.

Q6:-

Log levels in Python indicate message severity:

DEBUG: Detailed debugging info.

INFO: General operational info.

WARNING: Potential issues or unexpected behavior.

ERROR: Errors that don't stop the program.

CRITICAL: Critical errors causing program halt.

Examples:


DEBUG: Tracing variable values in a bug.

INFO: Server start/stop events.

WARNING: Low disk space warning.

ERROR: Invalid user input.

CRITICAL: External service outage.

Q7:-


Log formatters in Python customize how log messages are structured. To create a custom format:

Create a Formatter object.

Set a format string with placeholders.

Attach formatter to a handler (console, file, etc.).

Connect the handler to a logger.


```python
#EXAMPLE
import logging

# Create a logger
logger = logging.getLogger("my_logger")
logger.setLevel(logging.DEBUG)

# Create a formatter
formatter = logging.Formatter(
    fmt="%(asctime)s - %(name)s - %(levelname)s - %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S"
)

# Create a console handler and attach the formatter
console_handler = logging.StreamHandler()
console_handler.setFormatter(formatter)

# Attach the handler to the logger
logger.addHandler(console_handler)

# Log messages
logger.debug("This is a debug message")
logger.info("This is an info message")

```

    2023-08-31 11:42:21 - my_logger - DEBUG - This is a debug message
    2023-08-31 11:42:21 - my_logger - INFO - This is an info message
    

Q8:-


```python
#Create a shared logger in a main script or config module:
import logging

logger = logging.getLogger("my_app")
logger.setLevel(logging.DEBUG)

#Configure handlers and formatters:
formatter = logging.Formatter("%(asctime)s - %(name)s - %(levelname)s - %(message)s")
console_handler = logging.StreamHandler()
console_handler.setFormatter(formatter)
logger.addHandler(console_handler)

#In other modules/classes, import the logger and use it:
# In other modules or classes
import logging

logger = logging.getLogger("my_app.some_module")
logger.debug("Debug message from another module.")



```

    2023-08-31 11:53:53,820 - my_app.some_module - DEBUG - Debug message from another module.
    

Q9:-

Logging vs. Print Statements:

Purpose:

Logging: Structured recording of events for monitoring, debugging, and maintenance.

Print Statements: Quick output for debugging and immediate feedback during development.

Flexibility:


Logging: Customizable message format, various output destinations.

Print Statements: Limited formatting, output to console.

Severity Levels:


Logging: Supports severity levels for categorization and prioritization.

Print Statements: No built-in categorization.

Real-world Usage:

Logging: Production applications, long-term maintenance, monitoring.

Print Statements: Quick debugging in development, simple scripts.

Q10:-


```python
import logging

# Create and configure logger
logger = logging.getLogger("my_logger")
logger.setLevel(logging.INFO)

# Create a file handler
file_handler = logging.FileHandler("app.log")
file_handler.setLevel(logging.INFO)

# Create a formatter
formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(message)s")
file_handler.setFormatter(formatter)

# Attach handler to logger
logger.addHandler(file_handler)

# Log the message
logger.info("Hello, World!")

```

    2023-08-31 11:56:37 - my_logger - INFO - Hello, World!
    

Q11:-


```python
import logging
import traceback
import datetime

# Configure logging
logging.basicConfig(level=logging.ERROR,
                    format="%(asctime)s - %(levelname)s - %(message)s",
                    handlers=[logging.FileHandler("errors.log"), logging.StreamHandler()])

def main():
    try:
        # Your code that might raise an exception
        result = 10 / 0  # This will raise a ZeroDivisionError
    except Exception as e:
        # Log the exception
        error_msg = f"Exception: {type(e).__name__}, Timestamp: {datetime.datetime.now()}"
        logging.error(error_msg)
        traceback.print_exc()  # Print the traceback to the console

if __name__ == "__main__":
    main()

```

    2023-08-31 11:57:25,540 - ERROR - Exception: ZeroDivisionError, Timestamp: 2023-08-31 11:57:25.540428
    Traceback (most recent call last):
      File "C:\Users\sunny\AppData\Local\Temp\ipykernel_36040\746259093.py", line 13, in main
        result = 10 / 0  # This will raise a ZeroDivisionError
    ZeroDivisionError: division by zero
    


```python

```

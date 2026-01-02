# PromptableTraceback


## Overview

PromptableTraceback is a lightweight Python debugging library designed to optimise AI-assisted coding.

**Why use it?** When code fails, you typically spend a couple minutes gathering relevant lines of code, checking variable states, and copying the traceback into an LLM to help you debug. This library automates that process by capturing the "state of the world" at the exact moment of failure and formatting it into a clean, LLM-ready report.


## Installation

Install PromptableTraceback via `pip` from [PyPI](https://pypi.org/project/promptable-traceback/):

```bash
pip install promptable-traceback
```

**Requirements:** 
- Python 3.7+
- Works across Windows, MacOS, and Linux


## Example Usage

**Targeted monitoring:** Use the `@promptable_traceback.catch` decorator to capture errors that occur within a specific function.
```py
import promptable_traceback

@promptable_traceback.catch()  # Initialise locally.
def my_func(var1):
    var1 = int(var1)  # Trigger an error.

my_func("frfr")
```

**Universal monitoring:** Use `promptable_traceback.hook` to capture any unhandled errors across your entire application.
```py
import promptable_traceback

promptable_traceback.hook()  # Initialise globally.

def my_func(var1):
    var1 = int(var1)  # Trigger an error.

my_func("frfr")
```


## API Reference

The following parameters are available for targeted and universal monitoring.

- **`context_window` (int):** The number of lines captured above and below the line of code which errored. Set to 25 by default. Note: This is capped by the boundaries of the function when using the decorator, or the boundaries of the file when using the hook.
- **`mask_secrets` (bool):** When set to True, variables containing sensitive data will have their values redacted. Set to True by default.


## Suggestions & Feedback

I am always looking for ways to make this tool more useful for different development workflows.

If you have ideas for:
- **Alternative invocation:** Different ways to trigger the library into specific frameworks.
- **Tailored reporting:** Ideas for specific report formats that work better for certain LLMs or specialised debugging scenarios.
- **Feature requests:** Anything else that would make your debugging life easier.

Please feel free to open an issue or reach out!

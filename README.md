# Tool


Tools in LangChain connect Python functions with schemas to define their **name**, **description**, and **arguments**, allowing chat models to call these functions.

---

#### **Key Concepts:**
1. **Tools** encapsulate functions and schemas for easy use in chat models.
2. Use the `@tool` decorator to define tools quickly.
3. Tools support:
   - Automatic schema generation.
   - Artifacts like images or dataframes.
   - Injected arguments (hidden from models).

---

#### **Tool Schema:**
1. **Attributes:**
   - `name`: Name of the tool.
   - `description`: What the tool does.
   - `args`: JSON schema of function arguments.
2. **Methods:**
   - `invoke`: Synchronous execution.
   - `ainvoke`: Asynchronous execution.

---

#### **Creating a Tool:**
```python
from langchain_core.tools import tool

@tool
def multiply(a: int, b: int) -> int:
    """Multiply two numbers."""
    return a * b
```

---

#### **Using a Tool:**
```python
result = multiply.invoke({"a": 2, "b": 3})  # Output: 6
print(multiply.name)  # multiply
print(multiply.description)  # Multiply two numbers.
print(multiply.args)
```

---

#### **Advanced Configuration:**
- Modify schemas (e.g., name, description).
- Handle artifacts for outputs like images or dataframes.
```python
@tool(response_format="content_and_artifact")
def process_data(...) -> Tuple[str, Any]:
    """Processes data and returns results."""
    return "Processed successfully", artifact
```

---

For detailed examples, refer to the **LangChain documentation** on [custom tools](https://docs.langchain.com).

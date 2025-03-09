# Document Writer: AST vs Tree-Sitter

This repository contains two implementations for generating documentation from Python source code:

1. **Document Writer AST**: Uses Python's built-in `ast` module to parse the abstract syntax tree.
2. **Document Writer Tree**: Uses Tree-Sitter to parse the syntax tree.

Each implementation extracts function details and generates documentation using the Groq AI model.

---

## Document Writer AST

### Overview

The **AST-based document writer** relies on Python's built-in `ast` module to analyze Python scripts. It extracts the following elements:

- Function names and arguments
- Class names
- Imported modules
- Existing docstrings (if any)

After extracting the necessary information, it sends a request to Groq AI to generate detailed documentation, including usage examples. The results are stored in a Markdown file named **`output.md`**.

### Features

✅ Uses Python's built-in `ast` module (no extra dependencies required)\
✅ Extracts function names, parameters, imports, and classes\
✅ Reads existing docstrings and enhances them\
✅ Outputs generated documentation to `output.md`

### Limitations

❌ Cannot analyze complex syntax patterns or decorators effectively\
❌ Might miss certain function arguments, especially in lambda functions\
❌ Limited handling of nested functions and methods

---

## Document Writer Tree

### Overview

The **Tree-Sitter-based document writer** utilizes the `tree-sitter` library to parse Python code structurally. Unlike AST, Tree-Sitter provides a more flexible and robust parsing mechanism, making it better suited for analyzing modern Python syntax.

### Features

✅ Uses Tree-Sitter for a more precise syntax tree\
✅ Extracts function names and their parameters more accurately\
✅ Works well with nested functions, decorators, and lambda expressions\
✅ Outputs generated documentation to `outputs.md`

### Limitations

❌ Requires external dependencies (`tree-sitter` and `tree-sitter-languages`)\
❌ Does not extract class names or import statements\
❌ Does not check existing docstrings before generating new ones

---

## Comparison: AST vs Tree-Sitter

| Feature                 | AST-Based Approach | Tree-Sitter Approach     |
| ----------------------- | ------------------ | ------------------------ |
| **Dependencies**        | Built-in (`ast`)   | External (`tree-sitter`) |
| **Function Parsing**    | Basic              | Advanced                 |
| **Class Parsing**       | ✅ Yes              | ❌ No                     |
| **Import Extraction**   | ✅ Yes              | ❌ No                     |
| **Nested Functions**    | ❌ Limited          | ✅ Better Handling        |
| **Decorator Handling**  | ❌ Limited          | ✅ Better Handling        |
| **Existing Docstrings** | ✅ Uses them        | ❌ Ignores them           |
| **Output File**         | `output.md`        | `outputs.md`             |

### Conclusion

- If you want a lightweight, built-in solution that extracts **imports, classes, and function details**, use **Document Writer AST**.
- If you need a more **precise function analysis**, especially for **nested functions and modern Python syntax**, use **Document Writer Tree**.

Both methods have their strengths and trade-offs. Choose based on your specific use case!

---

## Setup & Usage

1. Clone this repository:

   ```sh
   git clone https://github.com/yourusername/document-writer.git
   cd document-writer
   ```

2. Install dependencies (for Tree-Sitter only):

   ```sh
   pip install tree-sitter tree-sitter-languages langchain-groq
   ```

3. Run the AST-based parser:

   ```sh
   python document_writer_ast.py
   ```

4. Run the Tree-Sitter-based parser:

   ```sh
   python document_writer_tree.py
   ```

5. Check the generated files:

   - `output.md` (from AST-based parser)
   - `outputs.md` (from Tree-Sitter-based parser)

---

## License

This project is open-source and available under the MIT License.

Author-Kush

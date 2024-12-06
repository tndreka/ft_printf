# ft_printf

## Custom Implementation of the Standard `printf` Function

### Overview

`ft_printf` is a custom implementation of the standard `printf` function from the C standard library. It allows formatted output of various data types - integers, strings, and characters - to the standard output, `stdout`. It takes a format string and a variable number of arguments, which allows it to be quite flexible and adapt to different types of formatted output. In this way, you will understand better how variadic functions and format specifiers work in C by implementing `ft_printf`.

---

## Key Concepts

### 1. **Variadic Functions**
`ft_printf` is a **variadic function**, meaning it can accept a variable number of arguments. In C, this is possible by using the `<stdarg.h>` library that offers macros (`va_start`, `va_arg`, `va_end`) to manage the variable arguments.

- **`va_start`**: Initializes the variable argument list.
- **`va_arg`**: Retrieves the next argument from the list.
- **`va_end`**: Ends the processing of variable arguments.

This enables `ft_printf` to be very flexible, handling any number and type of arguments passed in the function call.

### 2. **Format Specifiers**
The core functionality of `ft_printf` is based on **format specifiers**. These are placeholders in the format string (e.g., `%d`, `%s`, `%c`) that define how the corresponding arguments should be formatted and displayed.

Common format specifiers include:
- `%d`: Integer (decimal)
- `%i`: Integer (decimal, same as `%d`)
- `%u`: Unsigned integer
- `%s`: String
- `%c`: Character
- `%x`: Unsigned hexadecimal (lowercase)
- `%X`: Unsigned hexadecimal (uppercase)
- `%p`: Pointer

Each specifier relates to a specific function or method in `ft_printf` that handles the printing of that particular type of data.

### 3. **Handling Different Data Types**
To support various data types, `ft_printf` has to process several types of conversions:
- **Integers:** Signed and unsigned integers are printed with specifiers such as `%d`, `%i`, and `%u`. Functions like `ft_print_digit` and `ft_print_unsigned` handle integer formatting.
- **Strings and Characters:** Formatting string (`%s`) and character (`%c`) is implemented through helper functions, such as `ft_print_string` and `ft_print_char`.
- **Pointers:** The `%p` specifier prints the memory address (pointer) of an object in hexadecimal, implemented with `ft_print_pointer`.
- **Hexadecimal:** The `%x` and `%X` specifiers print an unsigned integer in hexadecimal format, with `%x` using lowercase letters and `%X` using uppercase.

### 4. **Number Formatting**
For numeric format specifiers (`%d`, `%i`, `%u`, `%x`, `%X`), the logic of `ft_printf` generally consists of converting a number to a string in some base (decimal, hexadecimal). This is usually left to a secondary function that takes the number and its base, converts it into a string representation, then prints it.

---

## How It Works

1. **Initialization:** The function begins by parsing the format string for format specifiers.
2. **Processing Arguments:** For each format specifier, `ft_printf` uses the corresponding function to format the argument and output it.
3. **Output:** The formatted results are printed to the standard output using system calls like `write` via `ft_putchar` or `ft_putstr`.

---

## Example Usage

```c
ft_printf("Hello, world! This is an integer: %d\n", 123);
ft_printf("An unsigned integer: %u\n", 123);
ft_printf("Another integer: %i\n", -456);
ft_printf("A string: %s\n", "Test string");
ft_printf("Character: %c\n", 'X');
ft_printf("Hexadecimal (lowercase): %x\n", 255);
ft_printf("Hexadecimal (uppercase): %X\n", 255);

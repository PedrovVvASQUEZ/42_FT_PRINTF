# ft_printf

A simplified reimplementation of the C standard library's `printf` function. This 42 school project explores parsing a format string, retrieving variadic arguments, and printing values with `write`.

## Features

`ft_printf` writes to standard output and returns the number of characters printed. The following conversions are supported:

| Conversion | Output |
| --- | --- |
| `%c` | A character |
| `%s` | A string (`(null)` if the pointer is `NULL`) |
| `%p` | A hexadecimal address prefixed with `0x` (`(nil)` for a null pointer) |
| `%d`, `%i` | A signed decimal integer |
| `%u` | An unsigned decimal integer |
| `%x` | A lowercase hexadecimal integer |
| `%X` | An uppercase hexadecimal integer |
| `%%` | The `%` character |

Format flags, field width, and precision are not implemented. For an unsupported conversion specifier, the specifier character is printed as-is.

## Build

From the project directory:

```sh
cd ft_printf
make
```

This builds the static library `libftprintf.a`. Available Makefile targets are `make`, `make clean`, `make fclean`, and `make re`. The project is compiled with `gcc` using `-Wall -Wextra -Werror`.

## Usage

Include the header and link the library when compiling your program:

```c
#include "ft_printf.h"

int main(void)
{
	int count;

	count = ft_printf("Hello %s, score: %d%%\n", "42", 100);
	return (count < 0);
}
```

From the repository root, assuming your source file is named `main.c`:

```sh
gcc -Wall -Wextra -Werror -Ift_printf main.c ft_printf/libftprintf.a -o demo
./demo
```

## Project structure

- `ft_printf/ft_printf.c` — parses the format string, reads variadic arguments, and dispatches conversions.
- `ft_printf/ft_utils.c` — prints characters, strings, and signed numbers in a given base.
- `ft_printf/ft_putunbr.c` — converts and prints unsigned integers.
- `ft_printf/ft_putptr.c` — prints pointers in hexadecimal.
- `ft_printf/ft_printf.h` — function declarations and required includes.
- `ft_printf/Makefile` — builds the static library.

# get_next_line

## Overview

**get_next_line** is a function that reads from a file descriptor and returns a line terminated by a newline character, developed as part of the 42 curriculum. This project focuses on file I/O, memory management, and handling edge cases in C, providing a robust utility that can be used in various applications where line-by-line reading is required.

## Table of Contents

- [Getting Started](#getting-started)
- [Function Prototype](#function-prototype)
- [Usage](#usage)
- [Makefile](#makefile)
- [Contributing](#contributing)
- [License](#license)

## Getting Started

### Prerequisites

To compile and use `get_next_line`, you need:
- A Unix-like operating system (Linux, macOS, etc.)
- `gcc` or another C compiler
- `make`

### Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/Mohamadaliibrahim/get_next_line
cd get_next_line
```

### Building the Library

To compile the library, simply run:

```bash
make
```

This will generate the `libgnl.a` static library file, which you can link against in your projects.

## Function Prototype

```c
char *get_next_line(int fd);
```

- **Parameters:**
  - `fd`: The file descriptor to read from.

- **Return Value:**
  - The function returns a line from the file descriptor, including the newline character if there is one. If the end of the file is reached, `get_next_line` returns `NULL`.

## Usage

To use `get_next_line` in your project, include the library header:

```c
#include "get_next_line.h"
```

Example usage:

```c
int fd = open("example.txt", O_RDONLY);
if (fd < 0)
    return 1;

char *line;
while ((line = get_next_line(fd)) != NULL)
{
    printf("%s", line);
    free(line);
}

close(fd);
```

Compile your project by linking the `libgnl.a` file:

```bash
gcc -Wall -Wextra -Werror -o my_program my_program.c -L. -lgnl
```

### Customization

You can adjust the buffer size used by `get_next_line` by modifying the `BUFFER_SIZE` macro in the header or by defining it during compilation:

```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 -o my_program my_program.c -L. -lgnl
```

## Makefile

The `Makefile` includes the following rules:

- `make` or `make all`: Compiles the library.
- `make clean`: Removes object files.
- `make fclean`: Removes object files and the compiled library.
- `make re`: Cleans and recompiles the library.

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please fork the repository and create a new branch for your feature or bug fix. Submit a pull request once your changes are ready.

1. Fork the project.
2. Create your feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a pull request.

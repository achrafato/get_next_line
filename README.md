# get_next_line - Line Reading Function

A function that reads a line from a file descriptor, part of the 42 curriculum.

## 📋 Overview

`get_next_line` is a function that returns a line read from a file descriptor, with the following features:
- Reads from multiple file descriptors simultaneously (bonus version)
- Handles both files and standard input
- Memory efficient with customizable buffer size

## 📁 Files Structure

### Mandatory Part
- `get_next_line.c` - Main function implementation
- `get_next_line.h` - Header file with prototypes
- `get_next_line_utils.c` - Helper functions

### Bonus Part
- `get_next_line_bonus.c` - Multiple fd implementation
- `get_next_line_bonus.h` - Bonus header file
- `get_next_line_utils_bonus.c` - Bonus helper functions

## 🔧 Function Prototype

```c
char *get_next_line(int fd);
```

## 🛠️ Usage

1. Include in your project:
```c
#include "get_next_line.h"
```

2. Example usage:
```c
int main(void)
{
    int fd = open("example.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}
```

## ⚙️ Compilation

Compile with specific buffer size:
```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 <files>.c
```

## 📝 Features

- Returns NULL if there's nothing to read or an error occurred
- Returns a string including the terminating \n character (except for the last line)
- Can handle multiple file descriptors simultaneously (bonus version)
- Memory leak free
- Static variable management
- Customizable buffer size during compilation

## ⚠️ Behavior

- Returns the read line on success
- Returns NULL on error or when nothing else to read
- Undefined behavior if:
  - fd is negative
  - BUFFER_SIZE is negative
  - Reading fails
  - File is empty

## 📜 License

This project is part of the 42 curriculum and is provided as-is.

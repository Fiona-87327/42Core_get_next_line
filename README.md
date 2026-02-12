# get_next_line - 42 Core Curriculum

## 📝 Overview
The **get_next_line** project is a fundamental part of the 42 school curriculum. The goal is to write a function that returns a line read from a file descriptor. Whether it's a file, standard input, or even a network connection, this function allows you to read content line by line.

This project introduces the concept of **static variables** in C and deepens the understanding of memory management and file manipulation.

---

## 🛠️ Features
- **Line-by-line reading:** Each call to `get_next_line` returns the next line of the given file descriptor.
- **Dynamic Buffer:** The reading buffer size can be modified at compile time using the `-D BUFFER_SIZE=n` flag.
- **Bonus Support:** 
  - Uses only one static variable.
  - Supports multiple file descriptors simultaneously (e.g., reading from `fd 3`, then `fd 4`, then back to `fd 3` without losing the reading thread).

---

## 📂 Project Structure
- `get_next_line.c`: Main logic of the function.
- `get_next_line_utils.c`: Helper functions required for string manipulation.
- `get_next_line.h`: Header file containing prototypes and macros.
- `*_bonus.c/h`: Bonus version files supporting multiple file descriptors.

---

## 🚀 Usage

### Function Prototype
```c
char *get_next_line(int fd);
```

### Parameters
- `fd`: The file descriptor to read from.

### Return Value
- **Read line:** Correct behavior.
- **NULL:** Nothing else to read or an error occurred.

### Compilation
To use this function in your project, include the source files during compilation. You can define the `BUFFER_SIZE` (default is 42 if not specified):

```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o gnl
```

---

## 💻 Example
```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd = open("test.txt", O_RDONLY);
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

---

# File-Handling-in-C



# Assignment 09: File Handling in C

## Problem Statement
Write a C program to copy the contents of one file to another using file handling.

## Objective
To study file handling in C and implement file reading and writing operations.

## Theory

### 1. What is a file and what is the purpose of file handling in C?
A file is a collection of data stored permanently on a storage device. File handling in C allows a program to create, open, read, write, append, and close files. Unlike variables, which usually store data temporarily in memory, files preserve information even after the program terminates.

### 2. Explain `fopen()` and `fclose()` with an example.
- `fopen()` opens a file in a specified mode and returns a file pointer.
- `fclose()` closes an opened file and releases associated resources.

**Syntax:**
```c
FILE *fp;
fp = fopen("input.txt", "r");
fclose(fp);
```

The file should be checked for successful opening before performing operations on it.

## Algorithm
1. Start the program.
2. Declare file pointers for the source and destination files.
3. Open the source file in read mode.
4. Check whether the source file opened successfully.
5. Open the destination file in write mode.
6. Read characters from the source file one by one.
7. Write each character into the destination file.
8. Close both files.
9. Display a success message.
10. Stop the program.

## C Program
```c
#include <stdio.h>

int main()
{
    FILE *source, *destination;
    int ch;

    source = fopen("input.txt", "r");

    if (source == NULL)
    {
        printf("Error opening source file.\n");
        return 1;
    }

    destination = fopen("output.txt", "w");

    if (destination == NULL)
    {
        printf("Error opening destination file.\n");
        fclose(source);
        return 1;
    }

    while ((ch = fgetc(source)) != EOF)
    {
        fputc(ch, destination);
    }

    fclose(source);
    fclose(destination);

    printf("File copied successfully.\n");

    return 0;
}
```

## Sample Input
Create a file named `input.txt` in the same directory as the program with the following contents:

```text
Hello World!
This is a file handling program in C.
```

## Sample Output
```text
File copied successfully.
```

The `output.txt` file will contain:

```text
Hello World!
This is a file handling program in C.
```

## Platform
Linux

## FAQ's

### 1. What is a `FILE *` pointer?
A `FILE *` pointer is used to refer to a file opened by a C program. It stores the information required by the C standard library to perform file operations.

### 2. Explain the functioning of `fprintf()` and `fscanf()`.
- `fprintf()` writes formatted data to a file.
- `fscanf()` reads formatted data from a file.

Example:
```c
fprintf(fp, "%d", number);
fscanf(fp, "%d", &number);
```

### 3. Explain different file opening modes.
- `"r"` – Opens an existing file for reading.
- `"w"` – Opens a file for writing; creates it if necessary and truncates it if it already exists.
- `"a"` – Opens a file for appending data at the end.
- `"r+"` – Opens an existing file for both reading and writing.
- `"w+"` – Opens a file for reading and writing, creating or truncating it.
- `"a+"` – Opens a file for reading and appending.

## Conclusion
Thus, reading the contents of one file and writing them into another file was implemented successfully using file handling functions in C.


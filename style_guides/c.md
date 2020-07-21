# C Style Guidelines
## Files
1. filenames are in snake_case
2. for general files, include the following standard header
```c
/** @file filename.c

    A brief description of the file

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et
    dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
    ommodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat
    ulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim
    id est laborum.

    @author DeveloperName
    @date 2020
    @copyright 2020 Audio Logic Inc

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
    INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
    PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE
    FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
    ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

    DeveloperName
    Audio Logic Inc
    985 Technology Blvd
    Bozeman, MT 59718
    openspeech@flatearthinc.com
*/
```
3. for kernel drivers, include the following standard header
```c
// SPDX-License-Identifier: GPL-2.0+
/** @file filename.c

    A brief description of the file

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et
    dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
    commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat
    nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim
    id est laborum.

    @author DeveloperName
    @date 2020
    @copyright 2020 Audio Logic Inc

    DeveloperName
    Audio Logic Inc
    985 Technology Blvd
    Bozeman, MT 59718
    openspeech@flatearthinc.com
*/
```

4. use include guards in all header files
```c
#ifndef FILENAME_H
#define FILENAME_H
...
...
...
#endif // FILENAME_H
```
5. license: MIT for general code, GPL for device drivers

## Naming Conventions
1. variables and functions are in snake_case
2. defines are in ALL_CAPS

## Variable Declarations
1. only declare one variable per line
e.g. don't do this
```c
double dbl1, dbl2, dbl3;
int *pint1, int2, int3;
```
2. declare variables close to their first usage
3. when declaring pointers, put the asterisk next to the variable name
e.g.
```c
list_node *head;
double *foo
```

## Bracket Style
1. opening brackets are on the same line as the statement
2. closing brackets are at the same indentation level as the statement
3. `else` goes on a separate line
example:
```c
void some_function(int a) {
    if (a < 3) {
        ...
    }
    else {
        ...
    }
}
```
4. prefer brackets for single-line statements
    1. not doing so is an inevitable maintenance problem; at some point you'll forget to add brackets when you add another line to the expression, and then you'll have a bug
    ```c
    for (i = 0; i < num; i++) {
        do_something();
    }
    ```

## Comments
1. use Doxygen comments when appropriate
  1. for single line comments, prefer `//! descriptive doxygen comment`
2. leave a blank line before comments

### Multi-line comments
1. don't use `*`'s on every line of a comment
```c
/**
  This is the correct
  comment style
*/
```

## Functions
1. each function should have a doxygen function header
```c
/** Brief function description

    Detailed function description

    @param describe function parameter1
    @param describe function parameter2
    @returns describe return value
*/
```

## General Style
1. use 2 spaces, no tabs
2. surround loop and conditional expressions with spaces
```c
while (1) {
    ...
}
if (a < 3) {
    ...
}
```
3. limit line lengths to 120 characters
    1. this is a soft limit; it's okay to exceed it if doing so makes the code more readable
4. split long lines after operators or commas
e.g.
```c
a = (b + c + d) *
    (e + f) - g
```

## Data Types
1. prefer types defined in `stdint.h` when you need a specific number of bits
    1. e.g. use `uint8_t` or `int8_t` instead of `char`
    2. if your data type is unsigned, use the unsigned types `uint*_t`
    3. if your data type is signed, use the signed types `int*_t`

# References
[Code Complete](http://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670)

[Doxygen Manual](http://www.doxygen.nl/manual/index.html)

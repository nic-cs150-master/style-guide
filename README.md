# Style Guide for C++
> Adapted from [Harvard's CS50 Style Guide](https://github.com/cs50/cs50.readthedocs.io/blob/rel/style/c.md), and from [Google C++ Style Guide for Drake](https://drake.mit.edu/styleguide/cppguide.htm)

There's no one, right way to stylize code. But there are definitely a lot of wrong (or, at least, bad ways). Even so, CS150/151 does ask that you adhere to the conventions below so that we can reliably analyze your code's style. Similarly do companies typically adopt their own, company-wide conventions for style.

## Indentation

Use 4 spaces for indenting a line of code. Properly indenting your code increases the readability of your code. While each company's standard of indenting may vary between using tabs or spaces, and even the number of spaces 2, 3 or 4, but applying proper indentation in your code is a standard practice in the industry.

### Brace placement
You may use **Allman** or **K&R style** but ***I prefer Allman style***. No other styles is allowed! Read more about [indentation styles](https://en.wikipedia.org/wiki/Indentation_style).

## Line Length

By convention the maximum length of a line of code is 80 characters long in C/C++, with that being historically grounded in standard-sized monitors on older computer terminals, which could display 24 lines vertically and 80 characters horizontally. Though modern technology has obsoleted the need to keep lines capped at 80 characters, it is still a guideline that should be considered a "soft stop," and a line of 100 characters should really be the longest you write in C/C++, else readers will generally need to scroll. If you need more than 100 characters, it may be time to rethink either your variable names or your overall design!

```cpp
// These next lines of code first prompt the user to give two integer values and then multiplies those two integer values together so they can be used later in the program
int firstCollectedIntegerValueFromUser = get_int("Integer please: ");
int secondCollectedIntegerValueFromUser = get_int("Another integer please: ");
int productOfTheTwoIntegerValuesFromUser = firstCollectedIntegerValueFromUser * secondCollectedIntegerValueFromUser;
```

## Comments

Comments make code more readable, not only for others (e.g., your instructor, team members) but also for you, especially when hours, days, weeks, months, or years pass between writing and reading your own code. Commenting too little is bad. Commenting too much is bad. Where's the sweet spot? Commenting every few lines of code (i.e., interesting blocks) is a decent guideline. Try to write comments that address one or both of these questions:

1. What does this block do?
1. Why did I implement this block in this way?

### Inline Comments
Within functions, use "inline comments" and keep them short (e.g., one line), else it becomes difficult to distinguish comments from code, even with [syntax highlighting](http://en.wikipedia.org/wiki/Syntax_highlighting). Place the comment above the line(s) to which it applies. No need to write in full sentences, but do capitalize the comment's first word (unless it's the name of a function, variable, or the like), and do leave one space between the `//` and your comment's first character, as in:

```cpp
// Convert Fahrenheit to Celsius
float c = 5.0f / 9.0f * (f - 32.0f);
```

In other words, **DO NOT** do this:

```cpp
//Convert Fahrenheit to Celsius
float c = 5.0f / 9.0f * (f - 32.0f);
```

Or this:

```cpp
// convert Fahrenheit to Celsius
float c = 5.0f / 9.0f * (f - 32.0f);
```

Or this:

```cpp
float c = 5.0f / 9.0f * (f - 32.0f); // Convert Fahrenheit to Celsius
```

### File Header Comment
Atop your .cpp and .h files should be a header comment that includes the name of the file, a description that summarizes what your program (or that particular file) does, programmer's name, date initiated, as in:

```cpp
/**
 * @file   main.cpp
 * @brief  Says hello to the world
 * @author John Doe
 * @date   08/19/2020 or August 19, 2020
 *
 */
```

### Function Header Comment
Atop each of your functions (except, perhaps, `main`), meanwhile, should be a comment that summarizes what your function is doing, as in:

```cpp
/**
 * @brief Compute and return the square of n
 * 
 * @param  n   number to be squared
 * @return int square of n
 */
int square(int n)
{
    return n * n;
}
```

## Variables

Do NOT define all of your variables at the very top of your functions but, rather, when and where you actually need them. Moreover, scope your variables as tightly as possible. For instance, if `i` is only needed for the sake of a loop, declare `i` within the loop itself:

```cpp
for (int i = 0; i < LIMIT; i++)
{
    cout << i << '\n';
}
```

Though it's fine to use variables like `i`, `j`, and `k` for iteration, most of your variables should be more specifically named. If you're summing some values, for instance, call your variable `sum`. If your variable's name warrants two words (e.g., `isReady`), capitalize the first letter of the second word, a convention popular in C++ known as "[camel case](https://en.wikipedia.org/wiki/Camel_case)".

If declaring multiple variables of the same type at once, it's fine to declare them together, as in:

```cpp
int quarters, dimes, nickels, pennies;
```

Just **DO NOT** initialize some but not others, as in:

```cpp
int quarters, dimes = 0, nickels = 0 , pennies;
```

Also take care to declare pointers separately from non-pointers, as in:

```cpp
int *p;
int n;
```

**DO NOT** declare pointers on the same line as non-pointers, as in:

```cpp
int *p, n;
```

## Constant Names

Variables declared as `const`, and whose value is fixed for the duration of the program, are named with a leading `k` followed by a mixed case. Underscores can be used in the rare cases where capitalization cannot be used for separation. For example:
```cpp
const int kDaysInAWeek = 7;
const int kAndroid8_0_0 = 24;  // Android 8.0.0
```
Although it is **discouraged**, Macro style is also allowed.
```cpp
const int DAYS_IN_A_WEEK = 7;
const int ANDROID_8_0_0 = 24;
```

## Conditions

Conditions should use [Allman style](https://en.wikipedia.org/wiki/Indentation_style#Brace_placement_in_compound_statements) as follows:

```cpp
if (x > 0)
{
    cout << "x is positive\n";
}
else if (x < 0)
{
    cout << "x is negative\n";
}
else
{
    cout << "x is zero\n";
}
```

Notice how:

- the curly braces line up nicely, each on its own line, making perfectly clear what's inside the branch;
- there's a single space after each `if`;
- each call to `cout` is indented with 4 spaces;
- there are single spaces around the `<<`;
- there are single spaces around the `>` and around the `<`; and
- there isn't any space immediately after each `(` or immediately before each `)`.

You may also use [K&R style]([Allman style](https://en.wikipedia.org/wiki/Indentation_style#Brace_placement_in_compound_statements). To save space, some programmers like to keep the first curly brace on the same line as the condition itself. Although I don't recommend it, as it's harder to read, it is ok to do so but you need to be consistent. Pick one style:

```cpp
if (x < 0) {
    cout << "x is negative\n";
} else if (x < 0) {
    cout << "x is negative\n";
}
```

And definitely **DO NOT** do this:

```cpp
if (x < 0)
    {
    cout << "x is negative\n";
    }
else
    {
    cout << "x is negative\n";
    }
```

## Switches

Declare a `switch` as follows:

```cpp
switch (n)
{
    case -1:
        cout << "n is -1\n";
        break;

    case 1:
        cout << "n is 1\n";
        break;

    default:
        cout << "n is neither -1 nor 1\n";
        break;
}
```

Notice how:

- each curly brace is on its own line;
- there's a single space after `switch`;
- there isn't any space immediately after each `(` or immediately before each `)`;
- the switch's cases are indented with 4 spaces;
- the cases' bodies are indented further with 4 spaces; and
- each `case` (including `default`) ends with a `break`.

## Enumerated Types
Enumerators should be named either like [constants](#constant-names) or like macros: either `kEnumName` or `ENUM_NAME`.

Preferably, the individual enumerators should be named like constants. However, it is also acceptable to name them like macros. The enumeration name, `UrlTableErrors` (and `AlternateTableErrors`), is a type, and therefore mixed case. Pick one and be consistent.

Constant style,
```cpp
enum UrlTableErrors
{
    kOk = 0,
    kErrorOutOfMemory,
    kErrorMalformedInput
};
```

Macro style,
```cpp
enum AlternateUrlTableErrors
{
    OK = 0,
    OUT_OF_MEMORY = 1,
    MALFORMED_INPUT = 2
};
```


## Functions

Be sure to declare `main` with:

```cpp
int main()
{

}
```

or, with:

```cpp
int main(void)
{

}
```

or with:

```cpp
int main(int argc, char *argv[])
{

}
```

or even with:

```cpp
int main(int argc, char **argv)
{

}
```

Do NOT declare `main` with:

```cpp
void main()
{

}
```

or with:

```cpp
main()
{

}
```

As for your own functions, be sure to define them similiarly, with each curly brace on its own line and with the return type on the same line as the function's name, just as we've done with `main`.

## Indentation

Indent your code four spaces at a time to make clear which blocks of code are inside of others. If you use your keyboard's Tab key to do so, be sure that your text editor's configured to convert tabs (`\t`) to four spaces, else your code may not print or display properly on someone else's computer, since `\t` renders differently in different editors.

Here's some nicely indented code:

```cpp
// Print command-line arguments one per line
cout << "\n";
for (int i = 0; i < argc; i++)
{
    for (int j = 0, n = strlen(argv[i]); j < n; j++)
    {
        cout << argv[i][j] << '\n';
    }
    cout << '\n';
}
```

## Loops

### for

Whenever you need temporary variables for iteration, use `i`, then `j`, then `k`, unless more specific names would make your code more readable:

```cpp
for (int i = 0; i < LIMIT; i++)
{
    for (int j = 0; j < LIMIT; j++)
    {
        for (int k = 0; k < LIMIT; k++)
        {
            // Do something
        }
    }
}
```

If you need more than three variables for iteration, it might be time to rethink your design!

### while

Declare `while` loops as follows:

```cpp
while (condition)
{
    // Do something
}
```

Notice how:

- each curly brace is on its own line;
- there's a single space after `while`;
- there isn't any space immediately after the `(` or immediately before the `)`; and
- the loop's body (a comment in this case) is indented with 4 spaces.

### do ... while

Although `do ... while` exist, I do not use it often. I recommend using `while` loop instead. 

If you do use it, declare `do ... while` loops as follows:

```cpp
do
{
    // Do something
} while (condition);
```

Notice how:

- each curly brace is on its own line;
- there isn't any space immediately after the `(` or immediately before the `)`; and
- the loop's body (a comment in this case) is indented with 4 spaces.

## Classes

Declare a `class` as a type as follows, with the type's name proceeding the keyword `class`, with each curly brace on its own line, access specifiers (e.g. `public`, `private`, and `protected`) should be aligned with the `class` keyword and braces. Member variables and functions should be indented 4 spaces. All class member variables should be prefix with `m` follow by a capital first letter of the variable name. This makes it easier to differentiate local variables from class member variables.

```cpp
class Student
{
public:
    Student();
    ~Student();
    string getName() const;
    string getDorm() const;
    void setName(string name);
    void setDorm(string dorm);
    
private:
    string mName;
    string mDorm;
};
```

## Structures

Declare a `struct` as a type as follows, with the type's name proceeding the keyword `struct`, with each curly brace on its own line and member variables indented therein:

```cpp
struct Student
{
    string name;
    string dorm;
};
```

If the `struct` contains as a member a pointer to another such `struct`, declare the `struct` as having a name identical to the type, without using underscores:

```cpp
struct Node
{
    int n;
    Node *next;
};
```

## Pointers

When declaring a pointer, write the `*` next to the variable, as in:

```cpp
int *p;
```

**DO NOT** write it next to the type, as in:

```cpp
int* p;
```

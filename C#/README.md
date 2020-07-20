# C# Notes

## Basics

### Libraries
Libraries can be imported using the `using <library>;` syntax.

### Assembly
An asembly is a container for related namespaces (.dll or .exe)

### Namespace
A namespace is simply a container for related classes

### Class
A class is a container for related functions

### Method/Function
1. Main method is the entry point to the application. Default format is as follows:
- `static <output> Method(<type> <parameters>)`
- "void" simply means nothing is output

### Variables/Constants
As the name implies, these are values that are declared in the program. Variables can change, constants must stay the same.
- `<type> <identifier>;`
- `const <type> <identifier> = <value>;` *You cannot declare a constant without assigning a value*
- Example: `int bugs = 2;`
- camelCase is prefered naming convention for variables
- PascalCase is the preferred naming convention for constants
- For declaring variables as specific type, type identifier needs added at the end: `float totalPrice = 19.99f;`
- Common types: `byte`, `int`, `long`, `float`, `double`, `char`, `string`, `bool`
- To have the compiler auto-detect data type, use `var` as the type

### Type Conversion
Can type cast variables to state risk of data-loss is known
- `int = i; byte = (byte)i;`

For non-compatible types, you can convert using `Convert` class.
- `string s = "1"; int i = Convert.ToInt32(s);`
- common methods: `ToByte()`, `ToInt16()`, `ToInt32()`, `ToInt64()`

## Overflowing
Exceeding boundary of data type overflows by default. Use `checked{}` to prevent overflowing (or use larger data type).

## Platform Invoke (P/Invoke)
Working with native libraries

### Using P/Invoke to pop a message box using user32.dll on Windows
1. DllImport tells the runtime to look up the method being declared in another DLL instead of expecting it to be written
2. Function name and expected parameters are declared 
```
class MainClass
{
  [DllImport("user32", CharSet=CharSet.Auto)]
  static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);
  
  static void Main(string[] args)
  {
    MessageBox(IntPtr.Zero, "Hello world!", "Hello world!", 0);
  }
}
```

### Using P/Invoke to print text on Linux
The same applies to Linux libraries
```
class MainClass
{
  [DllImport("libc")]
  static extern void printf(string message);
  
  static void Main(string[] args)
  {
    printf("Hello world!");
  }
}
```

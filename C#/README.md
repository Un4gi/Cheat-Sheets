# C# Notes

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

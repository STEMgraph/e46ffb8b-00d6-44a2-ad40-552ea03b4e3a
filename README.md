<!---
{
  "id": "e46ffb8b-00d6-44a2-ad40-552ea03b4e3a",
  "teaches": "Interacting with the Shell: Input, Output & Files",
  "depends_on": [],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-01",
  "keywords": ["shell", "echo", "ls", "cat", "stdout", "stdin", "redirection", "functions", "filesystem"]
}
--->

# Interacting with the Shell: Input, Output & Files

## 1) Introduction

## The Shell and the Idea of Files

When we are talking about **computers**, what we mean is a piece of electronic hardware that is able to perform algorithmic and logic mappings from a binary number to another binary number.

Interfacing with this hardware can be tricky — that’s why modern computers come with an **operating system**. This operating system provides us with a helper program called the **Shell**.

### What is the Shell?

The Shell is a program that *wraps* around the operating system’s inner core, also known as the **kernel**.

Sending commands directly to the kernel can be tedious and error-prone, which is why the Shell gives us a more user-friendly interface. The Shell interprets our input from RAM, prepares the data for the kernel, sends a request to have it evaluated, and stores the hardware’s answer back in RAM.

### From Switches to Terminals

Before interactive keyboard terminals, the contents of RAM were set manually by connecting switches and wires to high or low voltages.

In the 1950s, the **MIT Whirlwind** computer was the first computer to use an **electronic typewriter** to interact with the user in real-time — performing *read-compute-write* cycles while the computer was running.

An electric typewriter is a magnificent machine. Unlike mechanical typewriters that have a direct mechanical connection between each key and a specific hammer, electric typewriters use switches to select characters and a motor to perform the hammering action.

The concept of an interactive terminal was to intercept the electrical signal from the keyboard and reroute it to a computer. The computer would transform the signal and send a new electrical signal to the typing mechanism.

A key press on the keyboard was translated into a signal and sent to the computer’s memory using a **serializer-deserializer** circuit. The computer performed a transformation and generated a new sequence of signals. The Shell’s output, written to memory, was translated back into a signal and sent to the terminal's typing system.

### Terminal Emulators

Modern systems still follow this basic structure, but instead of a physical electric typewriter, we use **terminal emulators** — programs that mimic the behavior of old hardware terminals.

It is important to remember: the **calculation mechanism of the computer** and the **input/output systems** are separate!

### The Emergence of POSIX

In 1988, a group of electrical engineers, mathematicians, and physicists proposed a **standardized interface** to describe how input, output, and operating systems should interact. This made it easier for programmers to write software for different types of computers.

Before this standardization, every computer was essentially completely different.

The resulting standard is still in use today in an updated form. It is called the **Portable Operating System Interface**, or **POSIX**.

POSIX also defines what a *FILE* is supposed to be and how it should behave. While you probably know files from your home computer, we will soon talk about a different kind of files used in system-level programming.

### What is a Filesystem?

Operating systems include a piece of software called a **filesystem**. It is the filesystem’s job to give every accessible memory region on the computer a **human-readable name**.

Keep in mind: the computer is just wires, capacitors, transistors, and such. There are no "real" names for your hard disk, RAM, or anything else.

The filesystem is configured to allow us to address memory regions by **aliases or identifiers**, called **filenames**.

---

Let’s explore some basic commands of the command-line interpreter that we can use to interact with the filesystem!


## 2) Tasks

1. **Echoing**: `echo` is a subroutine, that is build into the command-line-interpreter. Everytime a program or programmer calls the `echo`-routine, the command-line-interpreter will write the argument to the standard output.

Run and observe the output:
```bash
echo "Hallo"
```

2. **Listing Files**: `ls` is a program that is installed on your computer. It generates a list of files, that are available to you at the moment and echos it to the standard output. If you have not used the terminal that much before, you might see only a few or no files at all. If you have used your computer and especially the terminal a lot, you might see more files there. 

Run and observe the output:
```bash
ls
```

3. **Writing into a new File**: The redirection-operator of the shell `>`, takes the `stdout` of the first operand and redirects it to the `stdin` of the second operand. If we redirect to a filename, the `stdout` will be written to storage:

Create a file using output redirection:
```bash
echo 'My First Text' > new_file.txt
```
Run `ls` again and observe the change.

4. **Viewing File Content and Redirection**: To inspect the content of a file, we can use the program `cat`. Run and observe:
  
```bash
cat new_file.txt
```

5. **Concatinating outputs**:  `cat`s name is derived from _concatinate_. You can also give it two filenames as parameters and it will print both of them in concatination.
```bash
echo "More text" > new_file2.txt
cat new_file2.txt
cat new_file.txt new_file.txt
cat new_file.txt new_file2.txt > new_file3.txt
cat new_file3.txt
```

6. **Overwrite vs. Append**: Redirecting comes in two flavors called _overwriting_ and _appending_. Run both commands individually and observe their behavior.
```bash
echo "Hello World" > new_file3.txt
cat new_file3.txt
```

```bash
echo "A next line" >> new_file3.txt
cat new_file3.txt
```

7. **Group Commands and Redirect**: Parenthesis give you the opportunity within the shell, to run multiple commands as a group and redirect their output to a common location. Run and observe.
```bash
(cat new_file.txt new_file2.txt; echo "Another Line") > new_file4.txt
cat new_file4.txt
```

## 3) Questions
1. What does `echo` do?
2. What does `ls` do?
3. What happens when you use `>` after `echo`?
4. What does `cat` do with one file? With two?
5. What's the difference between `>` and `>>`?
6. What do parentheses and `;` do?

## 4) Advice

The shell is a powerful and flexible interface to your system. Understanding how redirection works and how you can define and reuse functions makes you much more productive. Try to treat everything as a file, and remember that your terminal is just a program that handles I/O between you and the OS.

Later, you’ll learn how to automatically load such functions when a terminal starts using `.bashrc` or `.zshrc`.


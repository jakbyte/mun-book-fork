# Hello, fibonacci?

Most programming languages start off with a "Hello, world!" example, but not Mun. Mun is designed
around the concept of hot reloading. Our philosophy is to only add new language constructs when
those can be hot reloaded. Since the first building blocks of Mun were native types and functions
our divergent example has become fibonacci, hence "Hello, fibonacci?".

## Creating a Project Directory

The Mun compiler is agnostic to the location of a project directory, as long as all source files
are in the same place. Let's open a terminal to create our first project directory:

```
mkdir hello_fibonacci
cd hello_fibonacci
```

## Writing and Running a Mun Library

Next, make a new source file and call it *hello_fibonacci.mun*. Mun files always end with the *.mun extension*. If your file name consists of multiple words, separate them using underscores.

Open up the new source file and enter the code in Listing 1-1.

Filename: hello_fibonacci.mun

```mun
fn fibonacci5() -> int {
    fibonacci(5)
}

fn fibonacci(n: int) -> int {
    if n <= 1 {
        n
    } else {
        fibonacci(n - 1) + fibonacci(n - 2)
    }
}
```

<span class="caption">Listing 1-1: A function that calculates a fibonacci number</span>

Save the file and go back to your terminal window. You are now ready to compile your first Mun
library. Enter the following command to compile the file:

```
mun build hello_fibonacci.mun
```

Contrary to many other languages, Mun doesn't support standalone applications, instead it is shipped
in the form of shared libraries. That's why Mun comes with a command-line interface (CLI) that can
both compile and run Mun libraries. As each operating system has their own extension for shared
libraries, you'll need to use slighty different commands on different operating systems.

On Linux, enter the following command run the Mun library:

```
mun start hello_fibonacci.so --entry fibonacci5
```

On macOS, enter the following commands to run the Mun library:

```
mun start hello_fibonacci.dylib --entry fibonacci5
```

On Windows, enter the following commands to run the Mun library:

```
mun start hello_fibonacci.dll --entry fibonacci5
```

The result of `fibonacci5` (i.e. `5`) should now appear in your terminal. Congratulations! You just
successfully created and ran your first Mun library.


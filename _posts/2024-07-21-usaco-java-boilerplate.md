---
title: USACO Java Boilerplate
date: 2024-07-21
layout: post
published: true
author: Pablo E. Cortez
---

## Compilation in Java

In Java, class names correspond to file names. So if you are working on a project
with a class called `Main` that looks like this:

```java
public class Main {
    public static void main (String[] args) {
        ...
    }
}
```

You will compile by writing the following commands in the terminal. Double check your working directory.

To compile the program run:

```console
$ javac Main.java
```

To run the program:

```console
$ java Main
```

# USACO Boilerplate Code

To parse the input in USACO problems, we prepare a Java file with boilerplate 
code. 

> **boilerplate code**: code that gets repeated from file to file because it needs few to no
changes across distinct uses.

Below are some examples of the three necessary classes.


## Example with `BufferedReader`, `PrintWriter`, and `StringTokenizer`

### BufferedReader

```java
public class Example {
    public static void main (String[] args) {
        BufferedReader r = new BufferedReader(
          new InputStreamReader(System.in));
    }
}
```

In the example above, `BufferedReader` is used to read text from the input 
stream *efficiently*, while `InputStreamReader` accepts bytes from `System.in` 
and turns them to text characters that `BufferedReader` can read.


### StringTokenizer

```java
import java.util.StringTokenizer

public class Example {
    public static void main (String[] args) {
        String str = "This is a test string.";
        StringTokenizer st = new StringTokenizer(str, " ");

        while (st.hasMoreTokens()) {
            System.out.println(st.nextToken());
        }
    }
}

```

With the `StringTokenizer` object named `st`, we can split each line into tokens based on the specified delimiter (the default value is whitespace). 

In the example above, the `st` object  has access to the `hasMoreTokens()` and the `nextToken()` methods through the class `StringTokenizer`. 

You can find more examples at the [official documentation](https://docs.oracle.com/javase/8/docs/api/java/util/StringTokenizer.html) for the class.

### PrintWriter

We leave `PrintWriter` at the end, when we are ready to print onto the console. 
This class is a wrapper around `System.out.println`, so you replace `System.out` with the name of the `PrintWriter` object you declared (in our case we called it `pw`) 
followed by the method you want to use.

```java
public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader r = new BufferedReader(new InputStreamReader(System.in));

        // Create the PrintWriter object
        PrintWriter pw = new PrintWriter(System.out);

        ...

        // Output the results
        writer.println("The answer is...");

        writer.println(result); // Pretend there is a variable called result
        

        // Close the writer after we finish using it.
        writer.close();
    }
}
```

### Summary

These three classes together look like this in our [USACO Hungry Cow](https://usaco.org/index.php?page=viewproblem2&cpid=1299) sample problem:

```java
import java.io.*;
import java.util.StringTokenizer;

public class HungryCow {
    public static void main(String[] args) throws IOException {
        BufferedReader r = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(System.out);

        StringTokenizer st = new StringTokenizer(r.readLine());
        int N = Integer.parseInt(st.nextToken());
        int T = Integer.parseInt(st.nextToken());

        int[] days = new int[N];
        int[] haybales = new int[N];

        for (int i = 0; i < N; i++) {
            st = new StringTokenizer(r.readLine());
            days[i] = Integer.parseInt(st.nextToken());
            haybales[i] = Integer.parseInt(st.nextToken());
        }

        pw.println("N: " + N + ", T: " + T);
        for (int i = 0; i < N; i++) {
            pw.println("Day: " + days[i] + ", Haybales: " + haybales[i]);
        }

        pw.close();
    }
}
```
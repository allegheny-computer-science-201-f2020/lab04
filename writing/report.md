# LAB 04 Report

## Add your name

Please note, in addition to implementation and documentation tasks to be done in the provided source program templates, TODO tags in this document identify writing tasks that are to be completed.

### 1\. Short-circuit Evaluation.

Find the file `Lab4Short.java` in the "src" directory of your lab repository. Compile it and look at its bytecode using `javap -c Lab4Short` command.

TODO: Write a step-by-step description of the bytecode in a code block below, indicating what each line of the bytecode is responsible for. We are most interested in seeing how the bytecode demonstrates "short circuit evaluation" of the boolean`\verb$&&$'' operator, so be careful when explaining those parts. Specifically, you must identify the line where the short circuit happens.

```bash
0: bipush 10        push the constant 10 onto the stack
2: istore_1         pop the 10 and save it in i
3: bipush 20        push 20 onto the stack
5: istore_2           ... etc. ...
... etc. ...
```

### 2\. Recursive Functions.

Recall from CMPSC 101 that a _recursive_ function or method is one that either directly or indirectly calls itself. The most frequently cited example is the factorial function, defined as follows:

```Java
public static int factorial(int n) {
  if (n <= 0) {
    return 1;
  }
  else {
    return n * factorial(n-1);
  }
```

### Part 2a.

Find the file `Lab4Part2a.java` in the "src" directory of your lab repository. Complete it by writing a _recursive_ `static int` function named `pow` with one parameter, an integer `num`. The function is defined as follows: "if $num <= 0 then pow(num) = 1\. Otherwise, pow(num) = 2 pow(num-1)."

Now implement the same program in Cobol using `Lab4Part2a.cbl` template.

- To compile a Cobol program named "Lab4Part2a.cbl" in the lab, type:

`cobc -x -free -o Lab4Part2a Lab4Part2a.cbl`

- Then, to run it, you can run the following command:

`./Lab4Part2a`

TODO: Compare and contrast control structures (conditionals and loops) in Java and in Cobol using this sample program you wrote. What are similarities, what are differences?

### Part 2b.

Find the file "Lab4Part2b.java" in the "src" directory of your lab repository. Complete it by writing a recursive static int function named `recur` that is defined as follows:

```bash
if i ≤ 0 or j ≤ 0, recur(i, j) = 0\.
if i = j, recur(i,j) = i.
if i > j, recur(i,j) = j.
In all other cases, recur(i, j) = 2 · recur(i − 1, j) + recur(j − 1, i)
```

Now implement the same program in C, using `Lab4Part2b.c` template.

- To compile a C program named "Lab4Part2b.c" in the lab, type:

`gcc Lab4Part2b.c -o Lab4Part2b`

(but please don’t type `-o Lab4Part2b.c` because this will erase your C program!).

- Then, to execute it, type: `./Lab4Part2b`

TODO: Compare and contrast control structures (conditionals and loops) in Java, C and in Cobol using these two sample programs you wrote. What are similarities? Are there any differences? How do control structures in Java and C compare to their execution in Cobol?

### 3\. Loops.

The term ["syntactic sugar"](https://en.wikipedia.org/wiki/Syntactic_sugar) stands for any language syntax that exists purely to make the language easier to read or use; usually it stands for some other, less readable but equivalent syntax.

Is the for-loop in Java merely "syntactic sugar"? You probably learned in CMPSC 100 that a `while` loop can do the same thing as a `for` loop. In this exercise we will see if the Java bytecode for the two is identical.

Find the file `Lab4ForLoop.java` in the "src" directory of your lab repository. Compile and produce Java bytecode. You should see something like this:

```bash
public class Lab4ForLoop {
  public Lab4ForLoop();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public void func();
    Code:
       0: iconst_0
       1: istore_1
       2: iconst_0
       3: istore_2
       4: iload_2
       5: bipush        10
       7: if_icmpge     20
      10: iload_1
      11: iload_2
      12: iadd
      13: istore_1
      14: iinc          2, 1
      17: goto          4
      20: return
}
```

Variable "sum" is stored in location 1; the command "iload_1" pushes this onto the stack, the command "istore_1" pops the top value off the stack and stores it in sum. Similarly, variable "i" is stored in location 2, with corresponding remarks about "iload_2" and "istore_2". The program operates by pushing, popping, and computing with objects on the stack. Here are the steps in detail; you should follow through with the code and make sure you understand:

```bash
0 iconst_0    push constant 0 onto the stack
1 istore_1    pop stack and store in location 1 (sum = 0)
2 iconst_0    push constant 0 onto the stack
3 istore_2    pop stack and store in location 2 (i = 0)
4 iload_2     push contents of location 2 onto stack (i)
5 bipush 10   push constant 10 onto stack
7 if_icmpge 20  pop two elements and compare with ">=" (if (i >= 10))
     if test is true, go to line 20
10 iload_1     [test was false:] push sum onto stack
11 iload_2     push i onto stack
12 iadd        pop two elements, add, push result onto stack
13 istore_1    pop stack and store in sum (sum = sum + i)
14 iinc 2 by 1 increment location 2 by 1 (i=i+1)
17 goto 4      go back to line 4 and repeat the loop
20 return
```

When the loop has finished executing (when the `if_icmpge` statement sends us to line 20), the stack should be empty and sum (location 1) should contain the value of 0 + 1 + ... + 9.

TODO: Implement a Java program using a `while` loop in the `Lab4WhileLoop.java` program that generates exactly the same bytecode as program `Lab4ForLoop.java`. Then, compile `Lab4WhileLoop.java` program and make sure generated bytecode is the same one as the one from `Lab4ForLoop.java` program displayed above.

### Reflection

What were your biggest learning points during this lab and what challenges have you encountered during this lab?

TODO:

## I Adhered to the Code of Conduct Guide while Completing this Lab Project.

TODO: Add Your Name Here

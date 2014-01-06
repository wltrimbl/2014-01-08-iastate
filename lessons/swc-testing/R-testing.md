---
layout: lesson
root: ../..
title: ISU Bootcamp Computing Practices Tutorial
---

# An aside - how to write and execute an R script on the command line

An R script can be written in any text editor.  For example, here is a simple R script that you can write and save as test.R.

    #!/usr/bin/Rscript

    cat("Hello world", sep="\n")

To run this script on the command line, you could type:

    Rscript test.R

And you should see the output as:

    Hello world

Sometimes you want to be able to pass values to an R script that are manipulated by your program.  To do this, we could use the following and save it in a script called test-args.R:

    #!/bin/usr/Rscript

    args <- commandArgs(TRUE) #tells R your going to be passing arguments
    cat(args[1], sep="\n")
    cat(args[2], sep="\n")
    cat(args[3], sep="\n")

Then when we execute this script with arguments passed, like so:

    Rscript test-args.R one two three

Or...

    Rscript test-args.R 1 2 3

It will return as an output the first three arguments.

We're going to be learning how to execute functions and tests in R using this trick next.

# Testing (Not just your own code) & Debugging (Mostly your own code)

## Why do we test?

Short answer? it is easy to make mistakes

### System testing
Core idea: Treat the 'system' as a black box.  Feed the system a small set of selected data and compare the system's output to the expected.

* The system could be a biological system
* Hardware system
* Software system
  * As simple as a program
  * As complex as a large analysis pipeline

This is what we'll focus on!

Our testing system will be a divide function.

## How do we test?

Or, how do we select small sets of data to test with?

Domain knowledge
* I know these types of inputs are common
* I know these types of input are important
* I know these types of inputs could cause problems

EXERCISE: Write a script containing a function (in R) called divideBy with the parameters dividend and divisor. Use the trick above so that you can accept the divident and divisor as arguments. Use the cat function to display the answer of the function.

Given that we're working with the divide operation, what are some inputs that could cause problems?

## RUnit

RUnit is a package in R that can help you test your scripts.  To install it, start R, and install it.

    install.packages("RUnit")

This package has built in functions which can test the function that you previously wrote.  To test your divideBy function, you want to first identify test cases for your function.  Let's just do a few examples.

   test_divideBy <- function() {
       checkEquals(divideBy(4, 2), 2)
       checkTrue(is.na(divideBy(4, 0)))
       checkEqualsNumeric(divideBy(4, 1.2345), 3.24, tolerance=1.0e-4)
   }

   test_divideBy

Let's add this function to the end of our function like so in R:

    library(RUnit)

    divideBy <- function(dividend, divisor) {
        return(dividend / divisor)
    }

    test_divideBy <- function() {
        checkEquals(divideBy(4, 2), 2)
        checkTrue(is.na(divideBy(4, 0)))
        checkEqualsNumeric(divideBy(4, 1.2345), 3.24, tolerance=1.0e-4)
    }

Now, let's execute the test function:

    test_divideBy()

You'll see the following output indicating that a test failed, and you should fix your function:

    Error in checkTrue(is.na(divideBy(4, 0))) : Test not TRUE

Let's try this fix:

    divideBy <- function(dividend, divisor) {
        if (divisor == 0)
            return(NA)
        return(dividend / divisor)
    }

And rerun, test_divideBy() and now we'll get this output indicating that our tests have passed!:

   [1] TRUE

If you are integrating this function in a part of a package you are writing to R, because you named this function with the prefix "test_...", it would get checked during the package install.  More information on this can be found here:  http://www.bioconductor.org/developers/unitTesting-guidelines/.


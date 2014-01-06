---
layout: lesson
root: ../..
title: ISU Bootcamp Computing Practices Tutorial
---

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

Or, how do we select small sets of data to test with?  This is really important.  At minimum, I'll test my scripts or functions with a small dataset which I know the output.

Domain knowledge
* I know these types of inputs are common
* I know these types of input are important
* I know these types of inputs could cause problems

EXERCISE: In R, write a function called divideBy with the parameters dividend and divisor. Given that we're working with the divide operation, what are some inputs that could cause problems?  Try these out with your function.  

## RUnit

RUnit is a package in R that can help you test your scripts.  To install it, start R, and install it.

    install.packages("RUnit")

This package has built in functions which can test the function that you previously wrote.  To test your divideBy function, you want to first identify test cases for your function.  Let's just do a few examples.

    test_divideBy <- function() {
        checkEquals(divideBy(4, 2), 2)
        checkTrue(is.na(divideBy(4, 0)))
        checkEqualsNumeric(divideBy(4, 1.2345), 3.24, tolerance=1.0e-4)
    }


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

If you are integrating this function in a part of a package you are writing to R, because you named this function with the prefix "test_...", it would get checked during the package install.  More information on this can be found here:  http://www.bioconductor.org/developers/unitTesting-guidelines/.  You can also imagine requiring that a test passed (e.g., with an if loop), requiring that test functions passed prior to proceeding in a script.




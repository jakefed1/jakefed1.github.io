---
layout: post
title: Creating a Postfix Calculator Using Python
subtitle: What is postfix notation, and how can we use Python to implement it?
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Art of Data]
---

## What is Postfix Notation?

When you see 2-1, you immediately know you must subtract the 1 from the 2, because the subtraction sign, the operator, is between the two numbers, or operands. However, infix notation, as this format is called, is not the only way to write expressions. In prefix notation, the operator comes before the operands, and in postfix, it resides after. Strangely enough, even though humans are very comfortable with infix notation, postfix notation is easier for computers to understand. One way we can experiment with postfix notation is by building a calculator that evaluates postfix expressions, and we will call on Python to help us.

## Creating the Calculator

So you have a CSV with 100 rows, each containing 13 elements, of which 7 are numbers are 6 are operators. Each row begins with 2 numbers and ends with an operator. This setup is ripe for evaluating with postfix notation, so, let's get right to it.

## Strategy

The basic strategy can actually be boiled down to just a few relatively simple steps. First, we want to create a stack for each row in the dataset. Then, we want to cycle through each row, and when we see a number, we want to convert it to a float, then push it into the stack. When we see an operator, we want to determine which operator it is that we have stumbled upon before popping two numbers out of the stack, performing the operation on them, and then pushing the result back into the stack. Finally, we want to peek at the top of the stack, print the value we see, and return the stack. It sounds complicated, but if one has a good understanding of stacks, then this will make sense. The result could be a function like this:

    def evaluate(list):
    x = Stack([])
    l = len(list)
    for i in range(0, (len(list))):
        if (list[i] not in ["+", "-", "*"]):
            x.push(float(list[i]))
        else:
            a = x.pop()
            b = x.pop()
            if list[i] == "+":
                c = b + a
                x.push(c)
            elif list[i] == "-":
                c = b - a
                x.push(c)
            elif list[i] == "*":
                c = b * a
                x.push(c)
    print(x.peek())
    return x

The stack is especially useful compared to a list or a queue because it allows us to access the most recent elements. When we see an operator, we want to pull out the two most recent numbers, not the next two numbers, so by using a stack, we can grab these numbers with ease.

To see your calculator in action, simply perform your function on each row of the CSV when you import it. If you want to find the average of all the final values, create a list for the final values before you read in the CSV, append the floated values from each row to your list, then perform an average function on to the list. For those that don't already have an average function they can import from another file, this will suffice.

    def average(list):
    u = 0
    for i in range(0,len(list)):
        u+=list[i]
    m = u/len(list)
    return m

One of the steps of the process that gave me difficulty was tracking the numbers that I pushed into and popped out of the stack. A challenge of stacks is that once you pop something out of a stack, the value goes away, so if you need to save it for later, you have to track it yourself. Kush Malhotra, Aidan Resnick, Lucca Correia, and I eventually realized that we could track it in the same way we track any other value, by assigning a variable to it, and that doing so is possible because the pop function actually returns the value that was popped. I also learned a cool little trick for determining whether the value in the row is an operator or a number. Instead of a hard coded statement like _if (list[i] != "+") and (list[i] != "-") and (list[i] != "*"):_, one could simply write _if (list[i] not in ["+", "-", "*"]):_.

## Final results

If you are using the same dataset as me, when you print the final results, you should see the following list of values when you print:
* 6.0
* 40.0
* -162.0
* -692.0
* 2.0
* -19.0
* 93.0
* 95.0
* -11.0
* 49000.0
* 38.0
* 84.0
* -100.0
* 115.0
* 3.0
* 142.0
* 791.0
* 82.0
* -192.0
* -4.0
* 143.0
* 3060.0
* 137.0
* 384.0
* 11.0
* 48.0
* 805.0
* 11.0
* -2700.0
* 190.0
* -96.0
* 1715.0
* 60.0
* 48.0
* -25.0
* -4.0
* -135.0
* -77.0
* 663.0
* 40.0
* 10.0
* -81.0
* -15.0
* -311.0
* 1095.0
* 1076.0
* 1260.0
* -204.0
* 91.0
* 416.0
* -26.0
* 34.0
* -19.0
* -343.0
* 11.0
* -110.0
* 192.0
* -63.0
* -2.0
* 9.0
* 13.0
* -33.0
* -223.0
* 152.0
* 75.0
* 54.0
* 517.0
* 2110.0
* 412.0
* 10.0
* -571.0
* 3432.0
* 23.0
* -48.0
* 1764.0
* 7.0
* 240.0
* -2.0
* -936.0
* 9.0
* 1.0
* 5.0
* 414.0
* 386.0
* 128.0
* -115.0
* 1.0
* -18.0
* 0.0
* -16186.0
* 1391.0
* 29.0
* 233.0
* 38.0
* 63.0
* 1560.0
* 591.0
* -36.0
* 917.0
* -25.0

Additionally, the average turned out to be 529.91. If you got all these same values, congratulations, you have successfully built a working postfix calculator with Python!
# Python Week 5 Workshop

---

#### Note on workshop attendance...

Remember that the assessment portfolio requires submissions from 6/8 workshops, and you must upload your work to the ELE assessed portfolio quiz before leaving the session.

---

Work in CodeSpaces. 

You may use the following cheat sheets if you need to look up any Python commands.

https://github.com/phil-lewis-exe/PythonCheatSheets

**This week try not to use other websites to help you code or translate the questions, as these won't be allowed in the graded workshops at the end of term.**

---

## TASKS


### Part 1: Rolling Dice

Work in code file `5_part1.py`

This contains starter code that:

 - defines a function to simulate a dice roll. 
 - demonstrates how to call this function to roll a dice, storing the dice roll as variable `x1` then displaying the result.

```python
# library to generate random numbers
import random

def roll_one_dice():
    n_sides = 6
    roll = random.randint(1,n_sides)
    return roll

x1 = roll_one_dice()
print(f"The result of the 1st call to roll_one_dice() was: {x1}")
```

**Task 1.1**

Add code that runs the function again, storing the result as `x2` and that shows the output using a message like:

```
The result of the 2nd call to roll_one_dice() was: ...
```

Run the program three times. What do you notice?

**Task 1.2**

Directly below the definition for `roll_one_dice` (above the line `x1 = ...`) write the function `roll_n_dice`. 

This should take a single argument `n_dice` that determines how many dice are being rolled.

You can adapt the code above, but start by defining an empty list `rolls`, then using a `for` loop to fill the list with the right amount of dice rolls (as stored in `n_dice`).

Once you have written your function, add the following lines of code to the end of your program to test it.

```python
x3 = roll_n_dice(3)
print(f"The result of roll_n_dice(3) was: {x3}")
```

**Task 1.3**

Restructure and change the function `roll_n_dice` so that `n_dice` will take a default value of 2 if not provided.

Add a call to demonstrate this function working (storing the result in `x4`) and using a suitable message to show the result.

**Task 1.4**

Now change the function so it takes the two arguments `n_dice` and `n_sides` (e.g. an 8 sided dice can return values 1-8)

If not provided `n_sides` will take a default value of 6.

At the bottom of the code add additional demonstrations storing the results as `x5` `x6` and `x7` displaying the results in each case:

`x5` : shows how to call the function without specifying arguments (so that the default values are used).

`x6` : shows how to call the function to roll three 10 sided dice

`x7` : shows how to call the function to roll four dice with 8 sides, specifying the arguments in reverse order 

(i.e. the values must be passed in the order `n_sides` then `n_dice` as keyword arguments).



---

### Part 2: Functions with any number of arguments

Work in code file `5_part2.py`

Start with the following code that demonstrates a way to check items in a list to identify the highest value it contains.

You have to work out what code goes into the `???` that has been left for you to complete.

```python
def max_value_in_list(my_values):
    current_max = None
    print("start of loop")

    for item in my_values:
        print(f"running loop with item: {item} and current_max: {current_max}")
        if current_max is None:
            current_max = item
        elif item ??? current_max: # complete this line
            current_max = item

    print("end of loop")
    print(f"current_max: {current_max}")

    return current_max

demo1 = max_value_in_list([4,2,8,1,9])
print(f"result of call to max_value_in_list was: {demo1}")
```

**Task 2.1**

Write a new function `max_value()` which can take any number of input values as arguments, i.e. be called using

```python
max_value( 4, 2, 8, 1, 9 )  # uses individual values instead of list
```

**Hint** You should need to change two lines.

 - the function definition line needs to accept any number of arguments
 - the line `for item in my_values:` needs updating to refer to the input arguments instead of iterating over list `my_values`.

When the code is working, remove any `print()` statements so the function will run and return the result without displaying any messages.

To demonstrate add the following additional code examples to show your function works correctly in each case: 

```python
demo2 = max_value(99)
print(f"result of call to max_value with 99 was: {demo2}")

demo3 = max_value(2,99)
print(f"result of call to max_value with 2,99 was: {demo3}")

demo4 = max_value(6,8,3)
print(f"result of call to max_value with 6,8,3 was: {demo4}")
```

**Task 2.2**

In this task we will write a function `max_length` that has arguments which will accept a variable number of words, then return the length of the longest word.

Start by copying and renaming the `max_value` function to `max_length`, (you should place this directly below the existing `max_value()` function).

You can reuse the same code structure but adapt where needed so that the lengths of words are compared, instead of the size of the values.

(You can assume all arguments passed to the function will be valid Python strings).

Test your function by using the code below.

```python
demo5 = max_length("cat","beetles","dogs")
print(f"result of call to max_length with: cat beetles dogs was {demo5}")
```

**Task 2.3**

Write the following code examples to show your function works correctly in each case: 

```
demo6 : run the function with the single word "cats"

demo7 : run the function with the two words "cats" and "dogs"

demo8 : run the function with the words "mouse" "cat" "apple" "banana" and "enormous"
```

---


### Part 3: Processing a string to make replacements

Work in code file `5_part3.py`

This contains the following starter code that defines a function `process_str_v1`.

You have to work out what code goes into the `???` that has been left for you to complete.

```python
def process_str_v1(mystr, target1, replacement1, target2, replacement2):
    task_dict = {target1: replacement1,
                 target2: replacement2}

    print(f"task_dict stores: {task_dict}")
    print("starting loop")
    for key, value in ???: # complete this line
        target = key
        replacement = value
        print(f"mystr is now: {mystr}")
        print(f" ( replacing {target} with {replacement} ) ")
        mystr = mystr.replace(target, replacement)

    print("ended loop")
    print(f"mystr is: {mystr}")
    return mystr

demo1 = process_str_v1("The cat sat on the red mat.", "cat", "dog", "red", "blue" )
print(demo1)
```

This is set up to take arguments:

 - `mystr` that contains a text string to process
 - `target1` a word to replace
 - `replacement1` the word to use when replacing `target1`
 - `target2` a word to replace
 - `replacement2` the word to use when replacing `target2`
   
It then demonstrates how to call this function, stores the value returned in variable `demo1` and displays the result.

**Task 3.1**

Add another demonstration of the function that will take in the string `Exams can be very stressful!!!` and replace `Exams` with `Coding` and `stressful` with `easy`, store the result in `demo2` and display the result.

**Task 3.2**

Write a new function `process_str_v2` which will work with any set of target and replacement pairs passed as an arbitrary number of keyword arguments `kwargs`. 

i.e. to carry out the original string replacement we would run:

```python
demo3 = process_str_v2("The cat sat on the red mat.", cat="dog", red="blue")
print(demo3)
```

**Task 3.3**

Then add the additional demonstrations to show that your code works correctly in each case.

```python
demo4 = process_str_v2("The cat sat on the red mat.", cat="mouse")
print(demo4)

demo5 = process_str_v2("The cat sat on the red mat.", cat="flea", sat="hopped", mat="dog")
print(demo5)
```

**Task 3.4**

Can you replace the two words "red mat" with "green rug" using a call to the function using a single keyword argument? 

Write your answer as a Python comment.

---

### Part 4: Creating a greetings module

The following python code defines some functions to display greetings. 

```python
def say_hello(name):
    print(f"Hello {name}!")

def say_hi(name=None):
    if name is None:
        print("Hi, whoever you are!")
    else:
        print(f"Hi, it's good to see you {name}!")

```

We want to store these functions so that we can call them as python module `greetings`.

**Task 4.1**

Create an appropriately named python module file to do this. (e.g. click on the new file icon in the file panel toolbar).

**Task 4.2**

Next work in code file `5_part4.py`

Show how to import the `greetings` module and call the functions it contains using appropriate code so that the file will produce the following output:

```
Hi, it's good to see you Sarah!
Hello Fred!
Hi, whoever you are!
```

---


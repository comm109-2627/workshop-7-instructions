# Python Week 7 Workshop

---

#### Note on workshop attendance...

Remember that the assessment portfolio requires submissions from 6/8 workshops, and you must upload your work to the ELE assessed portfolio quiz before leaving the session.

---

Work in CodeSpaces. 

You may use the following cheat sheets if you need to look up any Python commands.

https://github.com/phil-lewis-exe/PythonCheatSheets

**This week try not to use other websites to help you code or translate the questions, as these won't be allowed in the graded workshops at the end of term.**

---

Coding Activity Markdown

### Task 1

Create a code file named `w7_part1.py` and copy in the code below:

```python
import time
import os

def clear():
    os.system('cls' if os.name == 'nt' else 'clear')


clear()

print("***** Welcome to the True or False quiz ******")
print()
user_input = input("Press enter to continue")

clear()

print("*** Q1 ***\n")
print("T/F: 2 + 2 = 5")
print()

ans = input("Enter T or F: ")
ans = ans.upper()

print("checking...")
print()

time.sleep(0.4)

if ans == "F":
    print("You were right!")
else:
    print("Sorry, incorrect.")

print()

user_input = input("Press enter to quit")
clear()
```

Run the code by typing the following into the terminal prompt:

```
python w7_part1.py
```

Look through the code and check you understand how it works:

What does the `clear()` function do?

What do the `print()` lines do?

What does the `\n` at the end of print("*** Q1 ***\n") do?

What does `time.sleep(0.4)` do?

What does line `ans = ans.upper()` do?

To investigate in each case you can try running the code 
after commenting out or changing the code line.

#### Task 1A

At the moment what happens if the user presses a key other than "T" or "F"?

Move the code that takes the answer (see below) into a loop:

```python
ans = input("Enter T or F: ")
ans = ans.upper()
```

Your loop should keep asking for input, until a valid answer has been given.

#### Task 1B

Customise your quiz with your own messages that welcome the player and  
tell them their result.


### Task 2

We want to be able to run the quiz with multiple questions.

One way to do this is to store both the question and answer within a dictionary.

```python
q1_dict = {
    'question': ...
    'answer': ...
}
```

Copy your code into new file `w7_task2.py` and edit to add code that sets up `q1_dict` after the imports and function definitions.

Then edit the code so that the question text is taken from the dictionary, 
and the answer is compared with the stored answer.

### Task 3

A quiz game should be able to ask more that one question. To store multiple questions
we can define a list storing several question dictionaries:

```python
q_list = [  {    'question': ... , 'answer': ... },
            {    'question': ... , 'answer': ... },
            {    'question': ... , 'answer': ... }  ]
```

Copy your code into new file `w7_task3.py` and edit to replace the line that
sets up a single `q_dict` with the code setting up `q_list`.

Set up three questions of your own.

Put the entire code that asks the question and checks the answer into a loop,
that runs over the questions in `q_list` and asks them one by one, telling you 
if you are correct or incorrect each time.

### Task 4

Copy your code into new file `w7_task4.py`.

We want to be able to record the score of someone playing the game.

#### Task 4A

Start by adding code to set up a `score` variable after the `q_list` is defined.

What should the initial value for `score` be?

Make sure that each time the code checks an answer, the score is updated as appropriate.
(+1 point for a correct answer).

At the end of the game display a message: `"You scored ___"`

#### Task 4B

Now change the code so that it tells you your score as a percentage (1 d.p.).

Hint. to do this you can compare the score with the number of questions in the list.

Add code to give an appropriate message based on the % score
(you can pick your own messages and boundaries).

e.g. 

 - below 33% `"...that was terrible."`
 - below 67% `"...that was weak."`
 - below 100% `...pretty good!"`
 - exactly 100% `"...Perfect!"`

### Task 5

We now have a working quiz. Let's see how we can restructure the code
using functions.

Copy your code into new file `w7_task5.py`.

Suppose we decide to create the following functions. 

Before writing each function think about what input argument(s) it should
take and what information it needs to return: 

 - `ask_question()`: asks a single question
  
 - `get_ans()`: takes an answer from a user, ensuring it is valid

 - `display_result()`: displays final score and the result message 

### Task 6

#### Task 6A

Put the whole code that runs a round of the game into function:

`play_game()`: plays a full game of the True / False game.

Then make a `main()` function that runs the program by calling `play_game()`

```python
def main():
    play_game()
```

At the bottom of your code file put:

```python
if __name__ == "__main__":
    main()
```

This is a common convention in Python. 

The `__name__` is a special Python variable that stores whether 
the file is being used as the **main** program or has been imported 
as a Python module.

Suppose our game was stored in file `quiz.py` you run `python quiz.py` and Python runs code from the file
the `__name__` variable will be set to `__main__`.

However suppose we were using the code within another file via an import.

```python
from quiz import get_ans
```

In this case when any code in the file executes `__name__` 
is set to the module name in this case `quiz`.

The following code acts as a guard, so we can specify code to run only
when the file is executed, but that will not run when Python loads the file
as an imported module: 

```python
# check if file is being run as main program
if __name__ == "__main__":
    # if so run the code in the main function
    main()
```

This allows us to import functions from a file for reuse in other projects.


#### Task 6B

Now edit the code in the `main` function, so that after each game 
it asks the user:

```python
Press enter to play again (or q to quit):  
```

and use a loop to keep playing until the user quits the game. 

### Task 7 (extension)

We can make an alternative version of the game where a player only
gets information on how they did at the end of each round, and has
five attempts to try to get all T/F answers correct.

You can try this game here (Coded with AI in JavaScript and HTML):

https://gemini.google.com/share/8ca9566b360d

Use Python to try to recreate the game.

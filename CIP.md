# 4.27 1st class

define a function

use the function

import a package

anatomy of a program

> import
>
> main function
>
> helper function
>
> start program
>
> ![1682562594776](code in place.assets/1682562594776.png)



code blocks

# 4.27 2nd class

control flow

recap

comment

descriptive naming, lower word and underscore

conditions 

loops (how many times will loop : while-no or for-yes) (postcondition matches precondition)

control flow

> ![1682568894096](code in place.assets/1682568894096.png)

beepers_present



# code1 :  Jigsaw Karel

complete this puzzle made up of beepers

```python
from karel.stanfordkarel import *

"""
File: PuzzleKarel.py
--------------------
Karel should finish the puzzle by picking up the last beeper 
(puzzle piece) and placing it in the right spot. Karel should 
end in the same position Karel starts in -- the bottom left 
corner of the world.
"""


def main():
    move()
    move()
    pick_beeper()
    move()
    turn_left()
    move()
    move()
    # put the beeper in the square
    put_beeper()
    # leave the square
    turn_left()
    turn_left()
    move()
    move()
    turn_right()
    move()
    move()
    move()
    turn_right()
    turn_right()

def turn_right():
    turn_left()
    turn_left()
    turn_left()


# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```

# code2 :  2023 Karel

placing 20 beepers, moving Karel one step, placing 23 beepers, and moving Karel one more step

```python
from karel.stanfordkarel import *

"""
File: 2021.py
--------------------
When you finish writing this file, Karel should be able to 
place 20 beepers, then 23 beepers, and end facing East to 
the right of the 23 beepers.
"""

def main():
    for i in range(20):
        put_beeper()

    move()
    for j in range(23):
        put_beeper()
    move()
    
if __name__ == '__main__':
    main()
```

code3 : Stone Mason Karel

build the columns in the Temple of Artemis in Efes. In particular, there are a set of arches where the stones (represented by beepers, of course) are missing from the columns supporting the arches. When Karel is done, the missing columns should be replaced by beepers

```python
from karel.stanfordkarel import *

"""
File: main.py
--------------------
When you finish writing this file, Karel should have repaired 
each of the columns in the temple
"""

# def main():
#     for k in range(2):
#         round_one()
#     turn_left()
#     put_beeper()
#     for i in range(5):
#         if front_is_clear():
#             mo_put()
#         else:
#             turn_right()
#             for k in range(4):
#                 move()
#     turn_right()
#     put_beeper()
#     for j in range(4):
#         mo_put()
#     turn_left()
        
# def round_one():
#     turn_left()
#     put_beeper()
#     for i in range(5):
#         if front_is_clear():
#             mo_put()
#         else:
#             turn_right()
#             for k in range(4):
#                 move()
#     turn_right()
#     for j in range(4):
#         move()
#     turn_left()
    
def main():
    for i in range(4):
        version_two()

def version_two():
    turn_left()
    put_beeper()
    for i in range(5):
        if front_is_clear():
            mo_put()
        else:
            turn_left()
            turn_left()
            for t in range(4):
                move()
            turn_left()
            for k in range(4):
                move()

def turn_right():
    turn_left()
    turn_left()
    turn_left()
    
def mo_put():
    move()
    put_beeper()

if __name__ == '__main__':
    main()
```

# section1 : Hospital Karel

1. Karel starts facing east at (1, 1) with an infinite number of beepers in its beeper bag.
2. The beepers indicating the positions at which hospitals should be built will be spaced so that there is room to build the hospitals without overlapping or hitting walls.
3. You will not have to build a hospital that starts in the last column.

```python
from karel.stanfordkarel import *

# # Here is a place to program your Section problem


# ------------------my codes--------------------
def main():
    while front_is_clear():
        if beepers_present() :
            build()
        else:
            move()

def build():
    turn_left()
    mo_pu()
    mo_pu()
    turn_right()
    mo_pu()
    turn_right()
    mo_pu()
    mo_pu()
    turn_left()
    if front_is_blocked():
        facing_east()
    else:
        move()
    
def turn_right():
    turn_left()
    turn_left()
    turn_left()

def mo_pu():
    move()
    put_beeper()

if __name__ == '__main__':
    main()


# ------------------martin's codes--------------------


# Here is a place to program your Section problem

# def main():
#     """
#     Have Karel go to each beeper and build a hospital.
#     """
#     build_and_move()

# def turn_right():
#     turn_left()
#     turn_left()
#     turn_left()

# def build_column():
#     for i in range(2):
#         move()
#         put_beeper()

# def build_hospital():
#     turn_left()
#     build_column()
#     turn_right()
#     move()
#     turn_right()
#     put_beeper()
#     build_column()
#     turn_left()
#     if front_is_blocked():
#         facing_east()
#     else:
#         move()
    

# # def build_and_move():
# #     while no_beepers_present():
# #         move()
# #     build_hospital()
# #     if front_is_blocked():
# #         facing_east()
# #     else:
# #         move()
        
# def build_and_move():
#     while front_is_clear():
#         if beepers_present() :
#             build_hospital()
#         else:
#             move()

# if __name__ == '__main__':
#     main()

if __name__ == '__main__':
    main()
```



# 5.05  3rd class

**goal :** approach to "top down" by decomposition (stepwise refinement)

**decomposition :** take the big problem into small pieces

**key :** what is the difference between success and not

**precondition** and **postcondition** must be the same

![1683287147808](code in place.assets/1683287147808.png)

> we find  the way which makes precondition and postcondition keep the same.

## **refinement**

关键思想是你应该**从顶部开始设计**你的程序，它指的是程序在概念上最高和最抽象的层次。

重要的是要查看分解的每个级别

## Iterative testing

警告：尝试编写整个程序而不进行测试是很危险的。如果你犯了错误，将很难找到错误。

作为指导原则，如果您有一个复杂的循环，请在编写整个循环之前测试循环体。

通常，通过观察最初看起来特殊的情况可以用与更一般情况完全相同的方式来处理，可以使程序变得更简单。

## Function preconditions and postconditions

当你定义一个函数时，如果你准确地写下前置条件和后置条件是什么，那么你遇到的麻烦就会少得多。

完成后，您需要确保您编写的代码始终满足后置条件，假设前提条件一开始就已满足。

> functions
>
> loops : for 
>
> if / else statement
>
> ![1683289747878](code in place.assets/1683289747878.png)
>
> infinite loop
>
> pre / post that do not match

## section meeting

finish the exercises

# 5.05 4th class

## rules of naming variable

descriptive and in snake case

> 1. start with a letter / underscore
> 2. only letter / digits / underscore
> 3. can not be a build-in command in python
> 4. case sensitive

## data types

integer : int

float : real number value

string : text characters

boolean : logical values

> why do we have int and float?

## transformation

```python
int()
str()
float()
```

## concatenate string

```python
+
```

## print spaces

```python
print("x =",x,"and y =",y)
# do not need to tranform type
```

##  Python Reader

### Interpreted vs Compiled

Python is what’s known as an **interpreted language**. When you run code in an interpreted language, another program called the **interpreter** reads your code and tells the computer what to do. This is different from other languages like Java or C++, which are **compiled languages**. With a compiled language, a **compiler** translates your code into **binary**, the language your computer understands. The computer itself then reads that binary and runs it. 

### distinction between single and block comments

*a single-line comment is fully ignored* by the interpreter, while *a block comment is valid code* that has no effect on the outcome of the program. If the interpreter sees a hashtag, it thinks to itself, “Great, I can skip this part!” With block comments, however, the interpreter doesn’t ignore the comment at all; it's just that the comment isn’t an instruction per se. The interpreter just reads it as, “Ok, there’s a comment here!” and continues on.

All of this really just means that you need to properly indent your block comments if you nest them inside of something like a loop. If you forget, Python will either yell at you for not indenting correctly, or worse, your code will break. If the block comment is not nested inside of anything, you can safely leave it unindented.

### Console

The console is where you will see error messages, prompts for user input, and output from print statements

To run a program in the  console, you write your program name after the keyword python:

python [filename.py](http://filename.py)

### print

The text you give **print** is called an **argument**

### Escape Characters

| **Code** | **Meaning**  | **Example**          | **Result**          |
| -------- | ------------ | -------------------- | ------------------- |
| \’       | Single Quote | ‘I\’m a programmer!’ | I’m a programmer    |
| \n       | New Line     | “Good\nMorning”      | GoodMorning         |
| \t       | Tab          | “Code\tIn Place”     | Code       In Place |
| \b       | Backspace    | ‘Pytho\bn’           | Pythn               |

### input

# code3 :  Fill Karel

no matter the size of the world, Karel should fill it with beepers.

```python
from karel.stanfordkarel import *

"""
Karel should fill the whole world with beepers.
"""


def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    for i in range(5):
        round()

    
def round():
    while front_is_clear():
        check_put()
    turn_around()
    while front_is_clear():
        check_put()
    condition_test()
            
def condition_test():
    if right_is_clear():
        turn_right()
        move()
        turn_right()
    else:
        turn_around()
        while front_is_clear():
            move()

def check_put():
    if no_beepers_present():
        put_beeper()
    move()
    
def turn_around():
    turn_left()
    turn_left()

def turn_right():
    turn_left()
    turn_left()
    turn_left()
    
# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```

# code4 :  Hello Name

Write a customizable version of the classic "hello world!" program in `main.py` which, instead of saying "hello world!", prompts the user for their name and then says hello to them! 

```python
def main():
    """
    You should write your code here. Make sure to delete 
    the 'pass' line before starting to write your own code.
    """
    name = input("What is your name? ")
    print("Hello "+name)

if __name__ == '__main__':
    main()
```

# section2 : **Karel Problem Solving**

In this task, Karel will always start by standing in front of a pile of beepers. Karel needs to pick up the entire pile of beepers and spread them out along the row so that there is exactly one beeper in each cell, and exactly as many cells with beepers as were in the original pile. Karel should spread the first beeper into the cell where the pile was.

```python
from karel.stanfordkarel import *

# ------------------ my codes--------------------------

def main():
    """
    Firstly, we go to the start position.
    Secondly, we take the second position in a line as start position,
    open the loop that we pick and put beepers.
    when the start position is empty, it can be broken.
    In the end, we put the last beeper into the start place. 
    """
    move() 
    while beepers_present():
        one_round()
    turn_around()
    move()
    turn_around()
    move()
    put_beeper()
    turn_around()
    move()
    turn_around()

def one_round():
    '''
    This is one action that we pick and put one beeper.
    The key is if the beeper in the start position is the last bepper.
    If it is the last one, we take it and go out of the loop to move.
    so we just take it and leave the position empty.
    when next time we go to the start position, we can stop the loop.
    If it not the last one, we take one, go to next place, put it down and go back. 
    '''
    pick_beeper()
    if no_beepers_present():
        back()
    else:
        while beepers_present():
            move()
        put_beeper()
        back()

def back():
    '''
    When we end up putting the beeper, we go back to the start position.
    Start position is the second position in one line.
    Make the precondition and the postcondition keep the same.
    Take the second position in a line as start position 
    and back to this position.
    '''
    turn_around()
    while front_is_clear():
        move()
    turn_around()
    move()

def turn_around():
    turn_left()
    turn_left()

# ------------------ leader's codes--------------------------

# def main():
#     move()
#     spread()
#     step_back()
    
# def spread():
#     while beepers_present():
#         pick_beeper()
#         if beepers_present():
#             move_to_end()
#             put_beeper()
#             reset()
#     put_beeper()

# def move_to_end():
#     while beepers_present():
#         move()

# def reset():
#     turn_around()
#     move_to_wall()
#     turn_around()
#     move()

# def move_to_wall():
#     while front_is_clear():
#         move()

# def turn_around():
#     turn_left()
#     turn_left()
    
# def step_back():
#     turn_around()
#     move()
#     turn_around()

# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```

# 5.09 5th class : expressions

## expressions

### get input

### arithmetic operators

addition+ \ subtraction- \ multiplication* \ division/ \ integer division// \ remainder% \ exponentiation \ negation

### precedence

**()** —— ****** —— - —— ***,/,//,%** —— **+,-**

> operators in same predencence categpry are evaluated left to right

### type conversion

exponentiation depends on the result

float sometimes is not exact

### shorthands

## constants

is outside (before) the function

## math library

```python
import math

# build-in constants
math.pi
path.e

# useful function
math.sqrt(x) # square root
math.exp(x) # exponent
math.log(x) 
```

## random numbers

```python
import random

# pseudorandom number : use seed
random.randint(min,max) # integer (inclusive)
random.random() # real number between 0~1
random.uniform(min,max) # real number
random.seed(x) # set seed for random number
```

## dice simulator

## reading

###   REPL : **Read**-**Eval**-**Print Loop**

```
To use REPL in the terminal, you can simply type python: 
$ python
>>> 

You can exit the REPL by pressing Ctrl+D and you should see your normal starting terminal line: 
$ python
>>> [Ctrl+D]
$ 
```

>The triple arrow shows up to let you know that you have entered the REPL. You can type any line of python code and hit enter and then the terminal will read the line, evaluate it, and print the results out to the user just like we would see in the Python Console!

###  Basic Arithmetic 

**how to account for conversion loss**?

it is important to note that the int() function simply chops off anything after the decimal. No rounding is involved. This can be dangerous. If we convert a float to an int and then back again, we might lose information. This is called **conversion loss.**

### random

###  Advanced Arithmetic 

| Operation        | Symbol  | Example                   |
| ---------------- | ------- | ------------------------- |
| Integer Division | **//**  | $ python>>> 10 // 42      |
| Exponentiation   | ***\*** | >>> 2 ** 38>>> 2 ** -10.5 |
| Modulus          | **%**   | >>> 8 % 32                |
| Unary Negation   | **-**   | >>> x = 0.5>>> -x-0.5     |

```python
def main(): 
    x = 36.0 // 10
    y = -5 // 2
    print(x) # 3.0
    print(y) # -3

if __name__ == '__main__':
    main()
```

>The second example is just meant to show what rounding down looks like for negative numbers. -5 / 2 is -2.5 and because integer division rounds down instead of truncating the value, the result is -3 (since -3 is less than -2). 

#### Precedence

**highest**

| () parentheses    |
| ----------------- |
| ** exponentiation |
| -   negation      |
| *  /  //  %       |
| +  -              |
| comparison        |
| not               |
| and or            |

**lowest**

```python
import math

def main(): 
    ans = math.exp(math.sqrt(-1) * math.pi)
    ans += 1
    print(ans)

if __name__ == '__main__':
    main()
```

>We’ve reached an error 🛑. Negative numbers are outside of the domain of square roots, so when we try to call math.sqrt(-1) we get an error. The same is true for calling math.log() on zero or negative numbers.

 # code5 :  Mad Libs 

Edit constant for to have the value 

# code6 : Multiply Two Numbers

Write a Python program that takes two integer inputs from the user and calculates the value of the first number multiplied with the second. 

# 5.10 6th class : [Control Flow](https://codeinplace.stanford.edu/cip3/learn/lesson-6-overall)

## recap

what is variable?

how to create, modify, use the variable?

binary operators

## while / if

condition is boolean that is either true or false

### create the evaluation mechanism by ourselves

comparison operators

> **==** / **!=** / **<** / **>** / **<=** / **>=**

algebraic relation

## booleans

logical operator

> **not** / **and** / **or**

can chain tests in condition as in algebra

precedence

> **arithmetic** > **comparison** > **not** > **and/or**

boolean variables

```python
x = 1 < 2 # True
y = 5.0 == 4.0 # False
c = True
```

## for loops

## reading

###  Conditionals 

Comparison Operations

Logical Operations

Logical Expressions

Precedence : use parentheses 

### Loops 

For vs While Loops

For Loops

range()

While Loops

Infinite Loops

# code7 : Joke Bot

Write a simple joke bot. The bot starts by asking the user what they want. However, your program will only respond to one response: **Joke**. 

# code8 : Random Numbers

The starter code for this program prints out a single random number in the range 1 to 100, inclusive. Modify this program so that instead of printing one random number, it prints 10. 

# code9 : Double It 

Write a program that asks a user to enter a number. Your program will then double that number and print out the result. It will repeat that process until the value is 100 or greater.

# code10 : Liftoff 

Write a program that prints out the calls for a spaceship that is about to launch. Countdown from 10 to 1 and then output `Liftoff!`

# section3 : **Console Programming**

## [Mars Weight Calculator](https://codeinplace.stanford.edu/cip3/ide/a/marsweight)

```python
"""
Prompts the user for a weight on Earth
and prints the equivalent weight on Mars.
"""

def main():
    # Fill this function out!
    earth_w = float(input("Enter a weight on Earth: ") )
    mars_w = 37.8 / 100 * earth_w
    # print(f"The equivalent weight on Mars: {round(mars_w,2)}")
    # print("The equivalent weight on Mars: ",round(mars_w,2)) # easiest
    # print("The equivalent weight on Mars: "+str(round(mars_w,2)))
    
    print(f"The equivalent weight on Mars: {mars_w:.2f}")
    
    # print(f"string {variables}")

if __name__ == "__main__":
    main()
```

## [Planetary Weight Calculator ](https://codeinplace.stanford.edu/cip3/ide/a/planetaryweights)

> \- Mercury: 37.6%
>
> \- Venus: 88.9%
>
> \- Mars: 37.8%
>
> \- Jupiter: 236.0%
>
> \- Saturn: 108.1%
>
> \- Uranus: 81.5%
>
> \- Neptune: 114.0%

```python
"""
Prompts the user for a weight on Earth
and a planet (in separate inputs). Then 
prints the equivalent weight on that planet.

Note that the user should type in a planet with 
the first letter as uppercase, and you do not need
to handle the case where a user types in something 
other than one of the planets (that is not Earth). 
"""
FRACTION = {"Mercury":37.6 / 100,"Venus":88.9 / 100,"Mars":37.8 / 100,"Jupiter": 236.0 / 100,"Saturn":108.1 / 100,"Uranus":81.5 / 100,"Neptune":114.0 / 100}

def main():
    # Fill this function out!
    earth_w = float(input("Enter a weight on Earth: "))
    
    loop = True
    while loop:
        name_planet = input("Enter a planet: ")
        name_planet = name_planet.capitalize()
        if name_planet == "Mercury":
            planet_w = FRACTION["Mercury"] * earth_w
            loop = False
        elif name_planet == "Venus":
            planet_w = FRACTION["Venus"] * earth_w
            loop = False
        elif name_planet == "Mars":
            planet_w = FRACTION["Mars"] * earth_w
            loop = False
        elif name_planet == "Jupiter":
            planet_w = FRACTION["Jupiter"] * earth_w
            loop = False
        elif name_planet == "Saturn":
            planet_w = FRACTION["Saturn"] * earth_w
            loop = False
        elif name_planet == "Uranus":
            planet_w = FRACTION["Uranus"] * earth_w
            loop = False
        elif name_planet == "Neptune":
            planet_w = FRACTION["Neptune"] * earth_w
            loop = False
        else :
            print("Your input is invalid. Please try again.")

    print(f"The equivalent weight on {name_planet}: {round(planet_w,2)}")

if __name__ == "__main__":
    main()
```



# 5.18 7th class : graphics

```python
from graphics import Canvas

# create the canvas : canvas(weight,height)
# origin point (0,0)
canvas = Canvas(800,200)

# create a blue rectangle 
# high left point is in (20,20)
# low right point is in (100,100)
# the default color is black 
canvas.create_rectangle(20,20,100,100,"blue")

# create a line
canvas.create.line(0,0,800,200)

# create an "品红" oval
canvas.create_oval(250,150,500,500,"magenta")

# create an image
canvas.create_image(10,180,"image.png")

# create a text
canvas.create_text(50,20,"Programming is Awesome!!!",color="green",font="Courier",font_size=20)
```

```python
# create a centered square
from graphics import Canvas

CANVAS_WIDTH = 400
CANVAS_HEIGHT = 300
SQUARE_SIZE = 100

def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    
    # get the middle of the canvas
    middle_x = CANVAS_WIDTH/2
    middle_y = CANVAS_HEIGHT/2
    
    # calculate the top left corner position
    left_x = middle_x - SQUARE_SIZE/2
    top_y = middle_y - SQUARE_SIZE/2
    
    # calculate the right and bottom of the square
    right_x = left_x + SQUARE_SIZE
    bottom_y = top_y + SQUARE_SIZE
    
    # draw the square
    canvas.create_rectangle(left_x, top_y, right_x, bottom_y, 'blue')

if __name__ == '__main__':
    main()
```

```python
# rects and loops
from graphics import Canvas

def main():
    # make a canvas
    canvas = Canvas(300,300)

    # create 20 squares to show diagonal line
    for i in range(30):
        left_x = i*10
        top_y = i*10
        right_x = left_x + 10
        bottom_y = top_y + 10
        canvas.create_rectangle(left_x, top_y, right_x ,bottom_y,"blue")
        # keep track of i
        print(i)
   
if __name__ == '__main__':
    main()
```

# 5.18 8th class : functions

```python
# call functions
function_name(input)

# define a function
def function_name(parameters):
    """explain the function"""
    ... # content
    ... # content
    return "result" # end the fuction and give back a value (feedback)

#  
```

> **argument** is the information that is given when we call it;
>
> **parameter** is the variable you name

```python
# draw a circle
from graphics import Canvas

# draw a japanese flag
circle(weight,height,color,center_weight,center_height,radius,circle_color)

# draw a bangladesh flag
circle(weight,height,color,center_weight,center_height,radius,circle_color)

def circle(weight,height,color,center_weight,center_height,radius,circle_color):
    canvas = Canvas(weight,height,color)
    canvas.create_oval(center_weight-radius, center_height-radius, center_weight+radius, center_height+radius, circle_color)
```

```python
# teacher's method
from graphics import Canvas

CANVAS_WIDTH = 400
CANVAS_HEIGHT = 300

def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    draw_japan_flag(canvas)
    canvas.wait_for_click()
    
    draw_bangladesh_flag(canvas)
    canvas.wait_for_click()
    
    draw_pulau_flag(canvas)
    canvas.wait_for_click()
    
    draw_georgia_flag(canvas)
 

def draw_japan_flag(canvas):
    draw_circle(canvas, CANVAS_WIDTH/2, CANVAS_HEIGHT/2, 120, 'red')

    
def draw_bangladesh_flag(canvas):
    canvas.create_rectangle(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT, 'darkgreen')
    draw_circle(canvas, CANVAS_WIDTH * 0.4, CANVAS_HEIGHT / 2, 150, 'red')

    
def draw_pulau_flag(canvas):
    canvas.create_rectangle(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT, 'dodgerblue')
    draw_circle(canvas, CANVAS_WIDTH * 0.4, CANVAS_HEIGHT / 2, 150, 'yellow')


def draw_circle(canvas, center_x, center_y, size, color):
    """
    draw a circle on the given canvas. Centered at the given location, in
    the given color
    """
    left_x = center_x - size/2
    top_y = center_y - size/2
    right_x = left_x + size
    bottom_y = top_y + size
    canvas.create_oval(left_x, top_y, right_x, bottom_y, color)

    
def draw_georgia_flag(canvas):
    canvas.clear()
    # some calculations for where the pluses go!
    x_left = CANVAS_WIDTH * 1/4
    x_right = CANVAS_WIDTH * 3/4
    y_top = CANVAS_HEIGHT * 1/4
    y_bottom = CANVAS_HEIGHT * 3/4
    
    # four calls to draw_plus
    draw_plus(canvas, x_left - 20, y_top - 20, x_left+20, y_top+20, 10)
    draw_plus(canvas, x_right - 20, y_top - 20, x_right+20, y_top+20, 10)
    draw_plus(canvas, x_left - 20, y_bottom - 20, x_left+20, y_bottom+20, 10)
    draw_plus(canvas, x_right - 20, y_bottom - 20, x_right+20, y_bottom+20, 10)
    
    # big background plus
    draw_plus(canvas, 0, 0, CANVAS_WIDTH, CANVAS_HEIGHT, 30)
    
    
def draw_plus(canvas, x_1, y_1, x_2, y_2, width):
    """
    Draws a plus which is inscribed in the rectangle defined by the two 
    points (x_1, y_1) and (x_2, y_2). The thickness of each arm of the plus
    is also passed in as a parameter
    """
    # compute the middle of the plus
    mid_x = x_1 + (x_2 - x_1) / 2
    mid_y = y_1 + (y_2 - y_1) / 2
    
    # half an arm thickness
    half = width/2
    
    # create the two rectangles
    canvas.create_rectangle(x_1, mid_y - half, x_2, mid_y + half, 'red')
    canvas.create_rectangle(mid_x - half, y_1, mid_x + half, y_2, 'red')
    
       
if __name__ == '__main__':
    main()
```

```python
# chessboard
from graphics import Canvas
import random

CANVAS_WIDTH = 400
CANVAS_HEIGHT = CANVAS_WIDTH
N_ROWS = 8
N_COLS = N_ROWS
SIZE = CANVAS_WIDTH / N_ROWS

def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    for r in range(N_ROWS):
        for c in range(N_COLS):
            draw_square(canvas, r, c)
            
def draw_square(canvas, r, c):
    print(r, c)
    color = get_color(r, c)
    x = c * SIZE
    y = r * SIZE
    end_x = x + SIZE
    end_y = y + SIZE
    
    canvas.create_rectangle(x, y, end_x, end_y, color, 'black')
            
        
def get_color(r, c):
    if is_even(r+c):
        return "green"
    else:
        return "beige"
'''def get_color(r, c):
    if is_even(r+c):
        return "black"
    else:
        return "white"'''
        
def is_even(value):
    return value % 2 == 0
            
if __name__ == '__main__':
    main()
```













# 5.26 9th class : information flow



## reading : update functions



# 5.26 10th class : animation

## animated square

```python
from graphics import Canvas
import time

CANVAS_WIDTH = 400
CANVAS_HEIGHT = 400
SQUARE_SIZE = 40
VELOCITY = 2
DELAY = 0.01
# move to center
def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    start_x = 0
    start_y = CANVAS_HEIGHT / 2 - SQUARE_SIZE / 2
    square = canvas.create_rectangle(start_x, start_y,
                    SQUARE_SIZE,
                    start_y + SQUARE_SIZE)  
	# animation loop
    while (start_x + SQUARE_SIZE / 2) < (CANVAS_WIDTH / 2):
            start_x += VELOCITY
            print("x:", start_x)
            canvas.moveto(square, start_x, start_y)
            time.sleep(DELAY)
            
	print("Done!")

if __name__ == '__main__':
	main()
```



## bouncing ball

```python
from graphics import Canvas
import time

CANVAS_WIDTH = 400
CANVAS_HEIGHT = 450
BALL_DIAMETER = 30
INITIAL_VELOCITY = 5
START_X = 0
START_Y = 0
DELAY = 0.001

def main():
    # create the canvas
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    # set the velocity of ball
    x_velocity = INITIAL_VELOCITY
    y_velocity = INITIAL_VELOCITY
    # set the ball's primitive position
    ball_x = START_X
    ball_y = START_Y
    # create the ball
    ball = canvas.create_oval(ball_x, ball_y,
                              ball_x + BALL_DIAMETER,
                              ball_y + BALL_DIAMETER,
                              'blue')
    # set the rules of ball movement
    while True:
        if (ball_x < 0) or (ball_x + BALL_DIAMETER >= CANVAS_WIDTH):
            x_velocity = -x_velocity
        if (ball_y < 0) or (ball_y + BALL_DIAMETER >= CANVAS_HEIGHT):
            y_velocity = -y_velocity
        # set the ball's position after moving
        ball_x += x_velocity
        ball_y += y_velocity
        canvas.moveto(ball, ball_x, ball_y)
        time.sleep(DELAY)

if __name__ == '__main__':
    main()
```



## graphics function

```python
# get the x and y location of the mouse
mouse_x = canvas.get_mouse_x()
mouse_y = canvas.get_mouse_y()

# move shape to some new coordinates
canvas.moveto(shape, new_x, new_y)

# move shape by a given change_x and change_y
canvas.move(shape, change_x, change_y)

# get the coordinates of a shape
top_y = canvas.get_top_y(shape)
left_x = canvas.get_left_x(shape)

# return a list of elements in a rectangle area
results = canvas.find_overlapping(left_x, top_t, right_x, bottom_y)
```



## mouse tracker

```python
# Mouse Tracker
from graphics import Canvas
import time

CANVAS_SIZE = 400
PAUSE_TIME = 1/50

def main():
    canvas = Canvas(CANVAS_SIZE, CANVAS_SIZE)
    while True:
        mouse_x = canvas.get_mouse_x()
        mouse_y = canvas.get_mouse_y()
        time.sleep(PAUSE_TIME)
        print("Mouse location: (" + str(mouse_x) + ", " + str(mouse_y) + ")")

if __name__ == '__main__':
    main() 
```



## reading : animation

**GOAL 1: Make a square move to the center.** 

```

```

**GOAL 2: Make a Bouncing Ball Program**

```

```



# section meeting

what is animation?

how can we move a shape using a function?
















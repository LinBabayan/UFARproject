# UFARproject

import random     
import sys 
     
a = input("welcome to the game of chance,\ndo you need instructions? type (yes) or (no) \n")
 
if a.lower() == "yes":
    print(''' 1. player rolls two six-sided dice and adds the numbers rolled together.
              2. On this first roll, a 7 or an 11 automatically wins, and a 2, 3, or 12automatically loses, and play is over.
                 If a 4, 5, 6, 8, 9, or 10 are rolled on this first roll, that number becomes the 'point.'
              3. The player continues to roll the two dice again until one of two things happens:
                 either they roll the 'point' again, in which case they win; or they roll a 7, in which case they lose.''')
 
elif a.lower() == "no":
    print("good luck!!!")
 
 
# function to generate dice throws   
def diceNumber():
   
    _ = input("press enter to roll the dice ")
     
    # this will enable to select a
    # random number from 1 to 6
    die1 = random.randrange(1, 7)
    die2 = random.randrange(1, 7)
     
    # returns the diceNumber values
    # in the form of tuple
    return (die1, die2) 
 
# function to get dice sum 
def twoDice(dices):
    die1, die2 = dices
    print("The sum of dice {} + {} = {}".format(die1, die2, sum(dices)))
 
 
# call  diceNumber to get value return the roll and then store that in value.
value = diceNumber()
twoDice(value)
 
# find the sum of two outcomes
sum_of_dices = sum(value)
 
 
# find if sum of dices is 7 or 11 
if sum_of_dices in (7, 11):
    result = "congratulations you won"
 
# find if sum of dices is 2 , 3 , 12 
elif sum_of_dices in (2, 3, 12):
    result = "you lost, \ntry again next time"
     
else: 
    result = "continue your game please"
    currentpoint = sum_of_dices
    print("current point :", currentpoint)
 
 
# game continues if you have not scored 2 , 3 , 7 , 11 , 12 

while result == "continue your game please":
    value = diceNumber()
    twoDice(value)
    sum_of_dices = sum(value)
     
    if sum_of_dices == currentpoint:
        result = "congratulations you won"
         
    elif sum_of_dices == 7:
        result = "you lost,\n try again next time"
 
# outcome of the game
if result == "congratulations you won":
    print("congratulations,you won")
     
else:
    print("you lost, \ntry again next time")

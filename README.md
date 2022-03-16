import sys
import random
name = input("can i know your name please???\n")
def run():
  print("Hello",name,"let's play hangman!")
  print("Start guessing...")
  # Defining the list of words
  w = ["NAINITAL","UDAIPUR","UTTAR PRADESH","JODHPUR","AURANGABAD","AMRITSAR","LADAKH","KERALA","DELHI","MADURAI","AGRA","JAIPUR","GOA","RAJASTHAN","PARIS","MUMBAI","KARNATAKA","HYDERABAD"]
  word = random.choice(w)
  guesses = " "
  turns = 10
  while turns > 0:
    failed = 0
    for char in word:
      if char in guesses:
        print(char)
      else:
        print("_")
        failed += 1
    if failed == 0:
      print("You win!")
      choice = input("Would you like to play again? y/n\n")
      if "y" in choice:
        run()
      elif "n" in choice:
        sys.exit()
      else:
        print("Something went wrong, type y or n.")
    guess = input("Guess a character:")
    guesses += guess
    if guess not in word:
      turns -= 1
      print("Wrong!")
      print("You have ",turns,"more guesses.")
      if turns == 0:
        print("You lose!")
        choice = input("Would you like to play again? y/n\n")
        if "y" in choice:
          run()
        elif "n" in choice:
          sys.exit()
        else:
          print("Something went wrong, type y or n.")
run()

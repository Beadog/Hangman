# Hangman
Hangman game in Python using turtle

    import random
    import turtle


    def main():
        listOfWords = ["yoga", "chair", "jump", "towel", "heat", "fuzz", "rocks",
                   "python", "asana", "daisy", "says", "said", "test",
                   "today", "clock", "hello", "pizza", "jumpy", "knives",
                   "ninjas", "juicy", "jumble", "hijack", "pyjama", "jumped"]

    # draw hanger upon startup
    turtle.penup()
    turtle.goto(-60, -120)
    turtle.pendown()
    turtle.forward(120)
    turtle.right(90)
    turtle.forward(15)
    turtle.right(90)
    turtle.forward(120)
    turtle.right(90)
    turtle.forward(275)
    turtle.right(90)
    turtle.forward(60)
    turtle.right(90)
    turtle.forward(30)
    turtle.left(90)

    again = True # variable created to keep the game going if user wants to play multiple times
    while again: # loop that keeps going until user ends the game

        guessWord = random.choice(listOfWords) # chooses a randomly out of the words in the variable listofWords
        board = "*" * len(guessWord) #prints how many letters are with *'s in place of letters
        alreadySaid = set() # a set to hold the guessed letters
        mistakes = 6 # the mistakes start at 6

        print()
        print(" ".join(board)) # joining other letters/ replace * with the actual letters

        guessed = False
        while not guessed and mistakes > 0:
            guess = input("Guess a letter: ") # gets letter from user
            print()
            if guess in alreadySaid: # this catches duplicate entries so the hangman will not try to redraw what was already drawn
                print("You already tried", guess, "...please try again.")
                print()
            elif guess == '':
                print("Oops! You didn't enter a letter. Please try again.")
                print()
            elif guess in guessWord: #if the letter you guessed is in the randomly selected word
                alreadySaid.add(guess) #add it to whats already been said
                board = "".join([char if char in alreadySaid else "*" for char in guessWord]) # join them
                if board == guessWord: # once the board is filled, the guessed variable changes to True to stop the loop
                    guessed = True
            else:
                alreadySaid.add(guess)  # add it to whats already been said
                mistakes -= 1 # subtract 1 from the value of mistakes (7) if you get the guess wrong
                print("Nope.", mistakes, "mistakes left.") # if what you guessed is wrong then print nope and how many mistakes are remaining
                if mistakes == 5:
                    # draw head
                    turtle.penup()
                    turtle.goto(0, 50)
                    turtle.pendown()
                    turtle.circle(30)

                if mistakes == 4:
                    # draw left facing arm and return turtle to starting position
                    turtle.right(135)
                    turtle.forward(50)
                    turtle.penup()
                    turtle.goto(0, 50)
                    turtle.left(135)

                if mistakes == 3:
                    # draw right facing arm and return turtle to starting position
                    turtle.right(45)
                    turtle.pendown()
                    turtle.forward(50)
                    turtle.penup()
                    turtle.goto(0, 50)
                    turtle.left(45)

                if mistakes == 2:
                    # draw body and return turtle to starting position
                    turtle.right(90)
                    turtle.pendown()
                    turtle.forward(75)
                    turtle.penup()
                    turtle.left(90)
                    turtle.goto(0, 50)

                if mistakes == 1:
                    # draw left facing leg and return turtle to starting position
                    turtle.goto(0, -25)
                    turtle.right(115)
                    turtle.pendown()
                    turtle.forward(65)
                    turtle.penup()
                    turtle.left(115)
                    turtle.goto(0, 50)

                if mistakes == 0:
                    # draw right facing leg and return turtle to starting position
                    turtle.goto(0, -25)
                    turtle.right(65)
                    turtle.pendown()
                    turtle.forward(65)
                    turtle.penup()
                    turtle.left(65)
                    turtle.goto(0, 50)

            print(" ".join(board))
            print()
            print("Here's what you guessed so far: ", alreadySaid)

        if mistakes == 0:
            print()
            print("Sorry! Game over.")
        else:
            print()
            print('Nice! You win.')

        again = (input("Would you like to play again [y/n]: ").lower() == 'y') # asks if you want to go again -- changes it to lower cap
        turtle.clear()

        if again is True:
            # draw hanger
            turtle.penup()
            turtle.goto(-60, -120)
            turtle.pendown()
            turtle.forward(120)
            turtle.right(90)
            turtle.forward(15)
            turtle.right(90)
            turtle.forward(120)
            turtle.right(90)
            turtle.forward(275)
            turtle.right(90)
            turtle.forward(60)
            turtle.right(90)
            turtle.forward(30)
            turtle.left(90)

        else:
            print("Thanks for playing!")


    main()

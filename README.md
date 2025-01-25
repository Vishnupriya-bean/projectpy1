import random

def greet_user():
    """Function to greet the user"""
    print("Welcome to the Number Guessing Game! 🎉")
    print("I have chosen a number between 1 and 10. Can you guess it?")

def get_user_guess():
    """Function to get the user's guess with input validation"""
    while True:
        try:
            guess = int(input("Enter your guess: "))
            if guess < 1 or guess > 10:
                print("Please guess a number between 1 and 10.")
            else:
                return guess
        except ValueError:
            print("That's not a valid number! Please enter a number between 1 and 10.")
        except EOFError:
            print("\nInput error. Exiting game.")
            exit()

def check_guess(guess, number):
    """Function to check if the guess is correct"""
    if guess < number:
        return "Too low! Try again."
    elif guess > number:
        return "Too high! Try again."
    else:
        return "Correct! You've guessed the number! 🎉"

def play_game():
    """Function to run the game loop"""
    greet_user()
    
    # Generate a random number between 1 and 10
    number_to_guess = random.randint(1, 10)
    
    # Loop until the user guesses the number correctly
    while True:
        user_guess = get_user_guess()
        result = check_guess(user_guess, number_to_guess)
        print(result)
        
        if result == "Correct! You've guessed the number! 🎉":
            break


play_game()

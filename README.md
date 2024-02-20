# Guessing-number-gam
import random
import math

# Get input for lower and upper bounds
lower_bound = int(input("Enter the lower bound: "))
upper_bound = int(input("Enter the upper bound: "))

# Validate that the upper bound is greater than the lower bound
if lower_bound >= upper_bound:
    print("Error: Upper bound must be greater than lower bound.")
    exit()

# Generate the secret number
secret_number = random.randint(lower_bound, upper_bound)

# Calculate the number of guesses (base-2 logarithm)
number_of_guesses = math.log2(upper_bound - lower_bound + 1)

# Tell the user how many guesses they have
print("\nYou have only", int(number_of_guesses), "chances to guess the number!\n")

# Start the guessing loop
guess_count = 0
while guess_count < number_of_guesses:
    guess_count += 1

    # Get the user's guess
    guess = int(input("Guess a number: "))

    # Check if the guess is correct
    if guess == secret_number:
        print("Congratulations, you guessed the number in", guess_count, "tries!")
        break

    # Provide feedback based on the guess
    elif guess < secret_number:
        print("Too low! Try again.")
    else:
        print("Too high! Try again.")

# If the user runs out of guesses, reveal the answer
if guess_count >= number_of_guesses:
    print("\nThe number was", secret_number)
    print("Better luck next time!")

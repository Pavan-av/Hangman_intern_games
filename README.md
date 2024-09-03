import random

def hangman_game():
    
    words = ['python', 'programming', 'hangman', 'challenge', 'developer']
    
  
    word = random.choice(words)
    word_length = len(word)
    
    
    guessed_letters = set()
    incorrect_guesses = 0
    max_incorrect_guesses = 6
    display_word = ['_'] * word_length
    
    print("Welcome to Hangman!")
    print("Try to guess the word.")
    
    while incorrect_guesses < max_incorrect_guesses and '_' in display_word:
        print("\nCurrent word:", ' '.join(display_word))
        print(f"Guessed letters: {', '.join(sorted(guessed_letters))}")
        print(f"Incorrect guesses left: {max_incorrect_guesses - incorrect_guesses}")
        
        
        guess = input("Guess a letter: ").lower()
        
        
        if not guess.isalpha() or len(guess) != 1:
            print("Please enter a single letter.")
            continue
        
        
        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue
        
        
        guessed_letters.add(guess)
        
        
        if guess in word:
            
            for index, letter in enumerate(word):
                if letter == guess:
                    display_word[index] = guess
        else:
            
            incorrect_guesses += 1
            print(f"Incorrect guess. '{guess}' is not in the word.")
        
        
        if '_' not in display_word:
            print("\nCongratulations! You've guessed the word:", word)
            return
    
    
    print("\nGame Over! The word was:", word)


hangman_game()

#imported libraries
import random 
import time
import sys

##### arrays #####
words = ["lion", "umbrella", "window", "computer", "glass", "juice", "chair", "desktop", "laptop", "dog", "cat", "lemon", "cabel", "mirror", "hat", "egypt", "automobile", "world", "python", "miniority", "treehouse", "friend", "program" , "people"]
indication_length_word = []

#### variables ####
horizontal_border = ("------------------------------------------------------------------")
alphabet = "abcdefghijklmnopqrstuvwxyz"


#### funtions ####
#function where startmenu is defined and coded in
def startmenu():
    print(horizontal_border)
    print("|                         HANGMAN                                |")
    print("|                                                                |")
    print("|                         Start                                  |")
    print("|                          Help                                  |")
    print("|                          Quit                                  |")
    print("|                                                                |")
    print("|                Made by Raoul Scholtens 2019                    |")
    print(horizontal_border)
    start_game_input = input(" \n > ").lower()
    if start_game_input == "start":
        startgame()
    elif start_game_input == "help":
        help_menu()
    elif start_game_input == "quit":
        sys.exit("Goodbye")
    else:
        print("Please enter a valid input")
        startmenu()
        

#function where the game is coded in
def startgame():
        wrong_letters = []
        right_letters = []
        word = random.choice(words)
        length_word = len(word)
        letters_guessed = [ ]
        
        for character in word:
            indication_length_word.append("_")
        print("This is an indication of the length of the word:")
        print(indication_length_word)
        print("Enter a letter from the alphabet")
        guessing_attempts = 0

        while guessing_attempts < 5 + length_word:
            guess = input("Type your letter guesses here \n > ").lower()
            if guess not in alphabet:
                print("please enter one single letter from the alphabet")
            elif guess in letters_guessed:
                print("You have already guessed this letter")
            
            else:
                guessing_attempts += 1
                if guess in word:
                    print("That letter is right")
                    letters_guessed.append(guess)
                    for x in range(0, length_word): 
                        if word[x] == guess:
                            indication_length_word[x] = guess
                            print(indication_length_word)                        
                elif guess not in word:
                    letters_guessed.append(guess)
                    print("That letter is not in the word")
                if "_" not in indication_length_word:
                    print("You gave guessed the word")
                    victorymenu()
        GameOverScreen(word)                                       
                    
         
               
        


#function where helpmenu is coded in
def help_menu():
    print(horizontal_border)
    print("|                        How to play                             |")
    print("|             The computer has chosen a random word              |")
    print("|         Your task is to guess this word letter by letter       |")
    print("|             If you are sure that you know the word             |")
    print("|         You can type in \"i am sure\" and guess the whole word   |")
    print("|           If you are done reading this help menu type \"done\"   |")
    print("|                                                                |")
    print("|                Made by Raoul Scholtens 2019                    |")
    print(horizontal_border)
    helpmenu = input(" \n > ").lower()
    if helpmenu == "done":
        startmenu()

def GameOverScreen(word1):
    blankspace = " " * (32 - len(word1))
    print(horizontal_border)
    print("|                                                                |")
    print("|         _____ ____  _      _____   ____  _     _____ ____      |")
    print("|        /  __//  _ \/ \__/|/  __/  /  _ \/ \ |\/  __//  __\     |")
    print("|        | |  _| / \|| |\/|||  \    | / \|| | //|  \  |  \/|     |")
    print("|        | |_//| |-||| |  |||  /_   | \_/|| \// |  /_ |    /     |")
    print("|         \____\\_/ \|\_/  \|\____\  \____/\__/  \____\\_/\_\    |")
    print("|                                                                |")
    print("|             Too bad you have tried too many times              |")
    print("|                   the word was "+ word1 + blankspace + "|")
    print("|                                                                |")
    print("|                Made by Raoul Scholtens 2019                    |")
    print(horizontal_border)
    startmenu()




def victorymenu():
    print(horizontal_border)
    print("|                        Congratulations!!                       |")
    print("|                 You have guessed the right word                |")
    print("|           As a reward for this you are awarded this medal      |")
    print("|                                                                |")
    print("|                                                                |")
    print("|                        |@@@@|     |####|                       |") 
    print("|                        |@@@@|     |####|                       |") 
    print("|                        |@@@@|     |####|                       |")
    print("|                        \@@@@|     |####/                       |")    
    print("|                         \@@@|     |###/                        |")
    print("|                          `@@|_____|##'                         |")    
    print("|                               (O)                              |") 
    print("|                            .-'''''-.                           |") 
    print("|                          .'  * * *  `.                         |") 
    print("|                         :  *       *  :                        |") 
    print("|                        : ~  HANGMAN ~  :                       |")
    print("|                        : ~ A W A R D ~ :                       |")
    print("|                         :  *       *  :                        |")
    print("|                          `.  * * *  .'                         |")
    print("|                            `-.....-'                           |")                      
    print("|                                                                |")
    print("|                                                                |")
    print("|                                                                |")
    print("|                Made by Raoul Scholtens 2019                    |")
    print(horizontal_border)
    startmenu()
#### main code ####
startmenu()
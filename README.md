# App1
First Application
import json
from difflib import get_close_matches

data = json.load(open("D:\Desktop\python\Application1\data.json"))

def translate(word):
    word = word.lower()
    if word in data:
        return data[word]
    elif len(get_close_matches(word, data.keys())) > 0:
        ask = input("Is it %s you wanted to search?\n\n If yes press y, or n if no: " % get_close_matches(word, data.keys())[0])
        ask = ask.lower()
        if ask == "y":
            return data[get_close_matches(word, data.keys())[0]]
        elif ask == "n":
            return "The word doesn't exist in dictionary. Please check the word."
        else:
            return "Please choose between yes or no."
    else:
        return "The word doesn't exist in dictionary. Please check the word."

word = input("Enter the word: ")

output = translate(word)

if type(output) == list:
    for item in output:
        print(item)
else:
    print(output)

# ICE2-MysteryNumber
Daniel Prazeres ST10454581

This project was hell on earth due to two major bugs that impeded all progress. The first was a type mismatch bug that occurred when relaying the
text inputs value to the checking guess function, the second was an inability to apply a value from inside a function to one outside of it. 

This app's function is to provide the user with an unknown number with a value between 1 - 100, then providing them the functionality to guess the value of this number with a
count of how many times they had guessed already. Moreover the app provides the user feedback on their guesses, telling the user if they need to
either guess higher, lower or if they guessed correct. The app plays very similarly to the game "Hot or Cold" where you guide a blinded teammate towards
something simply by describing the distance between them and said thing on a scale of temperature( Hot being close, cold being far). The app also
provides the user with a reset button that sets their guess count to 0 and generates a new random number between 1 - 100.

First bug:
On paper this should be a simple fix, type converters have existed for decades, however I couldn't have been more wrong. I attempted to use multiple different 
functions for type conversion with little to no sucsess. There seemed to be many functionswithin react and react native that should've been able to 
convert the string received from the text input and then convert it into an integer. But none worked, I ended up using a javascript function called 
"parseInt" which took in the variable that was to be converted as its first argument and then the numeric base of the int as its second argument. 
This miraculously worked and I had sucsessfully done something a junior programmer should have been able to do in less than 30 seconds over the 
period of 2 days.

Second bug:
This bug was infuriating to no end, it challenged my very preconvieced notions as to how variable assignment can be written within react native.
My goal was to set the resulting value from the converting function mentioned in the bug above, to the userGuess variable. Again something easy
on paper, but in practice a different story was told. I had called the type conversion function within an onPress attribute which worked 
perfectly fine. However react native seemed to take issue when i attempted to assign the return value of said function to the setUserGuess variable
within the onPress attribute. I am still unsure what the problem was, most of the errors were written in what I can only describe as Elvish.
Needless to say they were of no help here, and neither was the internet. It took give or take 3 days for me to realize that the compiler was 
determining the proper syntax of type assignment for useState variables is also determined by its placement within the script. Placed before
the App() functions return statement, the assignment of "variable = setDifferentVariable" works just as expected, however when written within an
attribute in the return statement, the compiler throws a fit stating that either there is a type mismatch or that constants cannot have their 
data changed. I managed to fix this by treating the setVariable portion of the useState as a function rather than a variable. But only within
the refrenced function as typing it out in app's return statement caused errors.

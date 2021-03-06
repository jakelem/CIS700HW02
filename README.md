# CIS700HW02
For my Action Castle parser, I implemented WordNet support by first taking a list of several of my commands from my original Action Castle and running them through the annotator given in part 1 to get the list of annotations, which I then copied into my code as a simple global dictionary. I then implemented Word embeddings by filling out the functions from part 2 and copying them over into the code as well; I also wrote a function that only returned the closest matching command above a certain threshold. I then created a "decode_command" function that first checked for any synonymous commands through WordNet and returned it if it was found; otherwise, it would iterate through all of the commands and return the closest one if it matched above a certain threshold using Word Embeddings. I called this function in the parse_command function, in the case where the player's intent wasn't clearly apparent from the outset.

For part 3, I implemented word embedding as well in a similar fashion to my Action Castle game, along with sentiment analysis. In my original game, the kitchen contained a lone box of stale chicken nuggets. In the improved version, there is a chef named Mario in the kitchen whom the player can either insult or compliment. In the first case, the chef will unhappily hand the player the stale nuggets:

>&gt;  you're ugly

>current score:  16

>Mario looks upset, and offers you a half eaten box of chicken nuggets.

On the other hand, if you say something nice, he gives you a slightly better reward:

>&gt;  i love you

>current score:  26

>With tears of pure joy in his eyes, Mario prepares you the most
                    beautiful, decadent meal you've ever seen: a whole lobster covered in saffron, foie gras, 
                    and solid silver and gold leaf truffles.

You can use either of these items to solve a puzzle later in the game, where you can reach the final goal through different means. I think it makes the game more fun since it adds a bit more humanity to the characters and creates a more interactive, first person experience where the player can actually choose what to say to the characters in game.

To account for sentiment analysis, I use the TextBlob package in the decode_command function. If no decoded command is found through word embeddings, I analyze the sentiment of the command, and if it is above or below a certain threshold a special_action is returned that represents a positive or negative communication. I then add this action to items to elicit a positive/negative response.

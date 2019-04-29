• General shape of most used 4-gram chords
	• This kind of plot is called a rank-frequency plot.
	• Plot the y axis on a log scale. What do you observe?
• Do not write white spaces before colons. This is different in English and French.
• A# is not the minor 7th, but the augmented 6th of C. Of cause, all your calculations are modulo 12, but you have to clarify your terminology here. The minor 7th is probably right, but then it should actually be Bb instead of A#.
• What does the third plot show? Bigrams or 4-grams? Plot title and text are contradictory.
• C, G, Am, F is also known as the chords of the 4-chord songs • If parts of the music are played in a loop, (A,F,G,C) is not distinguishable from (G,C,A,F)
	• It would be interesting to look at n-grams classes of cyclic permutations to account for these loops • Is the term “diff-gram” already established or did you invent it? That must be made clear. If it is established cite references, otherwise motivate the concept in greater detail.
• When you are looking at 4-grams using C, G, A and F,  do you actually want to look at cyclic permutation classes of (C,G,A,F)?
• Mode evolution plot
	• The percentages do not sum up to one for any year. What exactly is plotted here? Use equations to explain what you are calculating.
• The plot Proportion of notes belonging to major and minor scales has to be explained better.
• Change “Our results seem to show that ...” to “We observe a trend that ...”
• According to the n-gram difficulties
	• As mentioned above, you could look at cyclic permutation classes of n-grams.
	• Another idea is to look at n-grams that are present in at least 2 different songs and then filter-out all their suffix n-grams. Have a Look at the slides of this talk: http://www.mu-on.org/download/frieler_patternology_2017_en.pdf 
	• You could have a look at the diversity of n-grams over time. Normalized (conditional) entropy could help to quantify the diversity.
	• Think about removing repeated chords in your data. This will be more informative about the actual chord transition patterns.
	• Do you have section information in you dataset? Then you might use it to exclude n-grams that go across section boundaries.
	• The “ambiguity” problem is not clear. The purpose of n-grams is not to reflect chords that form a group in the piece (since groups are ambiguous, as you have written), but they rather capture which chords appear in sequence (without necessarily belonging to the same group). In particular, there is no relationship between n-grams of different length (such as (5,0) and (5,0,5,0)) besides being generated from the same chord sequence, so there is no “either/or” here.
• Good discussion of next steps towards the final analysis

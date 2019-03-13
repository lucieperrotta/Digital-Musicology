# Digital Musicology - Milestone 1

## Project title: Chord progressions in pop songs match theoretical jazz cadences

Membrado Jean-Baptiste: jean-baptiste.membrado@epfl.ch
Barret Lucien: lucien.barret@epfl.ch
Perrotta Lucie: lucie.perrotta@epfl.ch


### Research Question:

We would like to study the chord progressions in pop songs from 1950 to nowadays.
Our project deals with harmony in songs, and the succession of chords that form a song.

We would like to identify chord patterns used in different songs, and then see the evolution of those specific chord patterns in songs across time. Many questions can arise from our analysis: when were some chords used the most, do we see a specific chord pattern corresponding to a certain period of time, are there geographical constraints ? We can also spot the creation of some chord patterns, or the movement of some chords 

We might also see the evolution of specific chord patterns: a pattern may go through various transformation over time and place. For instance, some chord in a pattern could have a note added (turning it into a 4-notes chord) or more. We define a pattern to be an evolution of another chord if the fundamental, third and fifth are the same.
Our original question was to ask whether those patterns typically correspond to the theoretical cadences we can find in Jazz, for instance the II-V-I chord progression, or the cadences of classical music theory. If they are different we wanted to see in which way they differ and why. However, we found out that this had almost already been studied entirely before us.

### Concepts and Data:

The project focuses on the chord structures found in modern pop songs. We were thinking of using an online guitar tablature dataset, in order to get directly the chords of the songs we want. We will use the chords provided by this dataset as well as the the position of the chords in the song. We will have to transpose all the chords of our dataset in the same key, so that we can compare the musical structures in different scales. We might also have to simplify the chords found if there is for example chords with added 7ths, to understand and identify the general structure.
We also could use directly the “hooktheory” dataset, in which they already structure the data in a very similar way to what we would like to use, having already transposed all the songs and even classified the songs with respect to the chord patterns used. We would have to extract the dataset from their website.

### Methods:

From a chords dataset, we could use clustering techniques to find structure in our data. One complicated part will be that the chord sequences that are relevant might have different lengths, (for example 3, 4 or 5 chords). We will have to make groups to find out the lengths of each chord structure before, and then apply clustering on these groups.
The easiest way would be to “steal the “hooktheory” dataset from their website, keeping only the chord structure of the song, the year and maybe the genre.



### Literature:

[http://www.hooktheory.com/blog/i-analyzed-the-chords-of-1300-popular-songs-for-patterns-this-is-what-i-found/]
[http://www.hooktheory.com/blog/music-theory-analysis-1300-songs-for-songwriting-part2/]

This site called hooktheory already does pretty much exactly what we would like to do: they obtained a dataset of 1300 chords and transposed everything in the same key in order to analyse it. They obtained a ranking of the most commonly used chord patterns. Their dataset is now much bigger than the original 1300 chords, because people are contributing to their dataset.
One big problem of the “hooktheory” approach is that they consider the songs to be only written in a single scale all the time, whereas very often songs change scale in the middle.
In part 2, they also looked at cadences and how they were represented in pop music. However they are not very precise in the article, they simply look at the way the songs in their dataset go back to the tonic. It could be done much better by trying to see where the theoretical cadences fit in the chord patterns.
They also did not try to look at the geographical or spatial origins of the chord patterns they had found, in order to try to trace the history of the most common chord patterns. 
They also did not try to see the evolution of a specific pattern.
This is what we intend to do with our project.


[https://libres.uncg.edu/ir/uncg/f/G_Capuzzo_Neo_2004.pdf]
“Neo-Riemannian theory and the analysis of pop music” by Guy Capuzzo
In this article, Guy Capuzzo explains that transposing a full chord progression in a single key sometimes does not make much sense, because there can be key modulations, taking the example of the song “Shake the disease” by Depeche mode. Instead, Guy Capuzzo proposes to use neo-riemannian operators to describe chord patterns, which only relate each chord to the preceding chord, allowing to find more patterns than those we could describe only taking the point of view of a single scale. We could make the same kind of statistics “hooktheory” did using Neo-Riemannian operators instead of romanian scale notations, and try to find different kind of patterns in chord progressions. 
“Making sense of rock’s tonal system” by W Everett,
In this article, W Everett seems to say that at the origin, pop music of the 1950s was based on “common practice tonality”, but that nowadays more and more songs do not respect anymore the “normal” tonal rules.

[https://hal.archives-ouvertes.fr/hal-01801060/document]
Relevance of musical features for cadence detection. This article is focused specifically on the detection of the classical cadences (here separated into 44 different types). Even if our project is focused on chord patterns, that problem shares some characteristics with ours. This article can thus serve as a good basis for Computational implementation and gives us ideas on how to separate chord patterns.

### Two more things:
The most important for us now is to get feedback on how / where to focus our research. We’ve got ideas and we’d need to get advice on if our research is precise enough and if the research question is clear.

The main dataset we’re willing to use are the tablatures from [https://www.ultimate-guitar.com/]

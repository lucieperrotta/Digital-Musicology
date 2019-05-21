# Digital Musicology - Milestone 3

Barret Lucien: lucien.barret@epfl.ch

Membrado Jean-Baptiste: jean-baptiste.membrado@epfl.ch

Perrotta Lucie: lucie.perrotta@epfl.ch

## Initial Analysis

>Based on the data description from Milestone 2, what have you found out regarding your research question?

Our initial goal for this milestone was to answer the following question: which patterns do we find most commonly in our dataset, and try to trace back their origin and evolution through time. From our data processing, we came up with new ideas and chose to extend a bit our research question towards : "To what extent popular music has become more various over time ?".

We obtained several results that participate to answering our research questions. However, we have to be careful on how we interpretate the results we get since defining 'more various' or 'complex' in music is hard, and no definition is uniformly accepted.

> Which methods led to which results?

#### N-grams analysis and histograms of patterns
N-grams are sequences of n chords, with n being an integer. Grouping n-grams in songs gives us an insight on what sequences are the most popular. For this milestone, we focused a lot on 4-grams, that is the sequences of 4 chords, since most Billboard songs are 4/4. We obtained similar results for different N, but from N=4 we have enough complexity to really obtain patterns that are meaningful on their own.
When we look at the first 500 most used 4-grams, the distribution looks like an exponential decay: ![](https://i.imgur.com/n7m1ZmI.png)

The most used n-grams only use the first, fourth and fifth of the scale. The majority of them contain repeated chords, and they are not very interesting musically: they do not represent a 'musical' pattern, but more structural elements. The first 10 most common 4-grams transposed to the key of C are plotted below: ![](https://i.imgur.com/fRUaqm0.png)

 The 4-gram of 4 root chords is as we could expect the most popular. We see that the following most popular 4-grams are (F,C,F,C) and (C,F,C,F), which means the songs analyzed often used this bigram alternating structure. This can also be seen in the patterns (C,C,F,F) and (F,F,C,C), which are only an 2 times slower extension of the previous pattern. 
 
The first pattern using notes different from C, F and G is the 21st most common pattern : (C,Bb,F,C). This means that the 3rd most popular scale degree after the dominant and the subdominant is the minor 7th. We looked at this more in detail afterwards and plotted the popularity of bigrams containing C and A# over time:![](https://i.imgur.com/CDhmGq9.png)
We can observe that those bigrams were very rare during the 1960s but became more and more popular until the 1980s, during which their proportion became more or less constant.

 The first 4-gram in which the 4 notes are different from each other is the 33rd most common pattern: (A,F,G,C). This is quite close to what we expected to find, the famous C, G, Am, F progression described here in [HK10]. We also plotted the most used 4-grams of chords containing different chords:![](https://i.imgur.com/lzziyIC.png) 
 
 We can notice that most of them use the 4 notes C, G, A and F, which is very similar to the most popular patterns described on the hooktheory website.
These n-grams showed that the most common patterns in our dataset are also the most simple ones in the sense that they use a lot of repetitions of chords and only the root, the dominant and the subdominant.

#### Diff-grams

After looking at chord progressions relatively to the tonic, we wanted to have a look at chords progression relatively to the previous chord, ie. by only counting the jump in semitones from a chord to the next. The goal in making diff-grams was to free ourselves from the influence of the tonic in the chord progression. The reason to do so was that there could be modulations between different parts of the songs, or that the tonic could have been not correctly given. Here are the results we obtained: ![](https://i.imgur.com/ceG561b.png)

As we could have expected, this distribution exactly follows our first 4-grams plot. There seems to be no strong effect coming from the choice of the tonic.

#### Analysis of use over time using the proportion of the usage of chords

In order to analyze the popularity of some 4-grams, we plotted the evolution of the use of 4-grams using C, G, A and F chords as a function of time, because we saw in the previous section that they were particularly important. The results are shown here:![](https://i.imgur.com/AibQfZg.png)

We see a small decline of the usage of these chords during the 1970s, as if the public was getting tired of these chord progressions, but they were widely used from 1985, where we might see a "rediscovery" of those patterns. However, these changes are of course very small and therefore hard to interpret.

Another such evolution analysis is to estimate how much each song fits the 7 music modes. We created mode templates, each containing all the natural triads and tetrads chords belonging to the very mode, as listed on https://en.wikipedia.org/wiki/Roman_numeral_analysis. For example, the ionian mode contained Cmaj, Cmaj7, Dmin, D7, Em, E7, Fmaj, Fmaj7, Gmaj, G7, Amin, A7, Bmin and B7 (because it was not possible for us to note diminished chords for B).

We then grouped all songs by year, and computed, for each mode, how much in average all this years' songs fit each mode. This method highlighted that all modes tend to lose popularity over time, especially the ionian mode (major scale):![](https://i.imgur.com/CbanelT.png)

For example, as of 1960, 80% of the songs in our dataset could be considerated as ionian, but this ratio decreases to reach the value of 50% in 1990. 
 We also tried to plot the diatonicity of songs as a function of time, i.e. the percentage of songs belonging to any of the modes. We were hoping to see more and more pop songs that did not belong to any mode as a function of time. Unfortunately, all the songs of our dataset belong to at least one of the 7 modes, with the way we defined them.
 
 One possible way to interpret these results is to say that popular music is becoming more and more free from the classic diatonic modes, and possibly moves towards more diverse forms. Another interpretation is to say that chords tend to becore richer with years (pentads or more, suspended chords...), while still belonging to the classical modes. Since our mode templates only included triad and tetrad chords, this could explain the decrease in the use of the modes in the "simple chords" fashion.

#### Proportion of notes belonging to major and minor scales

We measured the proportion of chords' root notes that belonged to either the major scale, minor scale, or any of the two:![](https://i.imgur.com/Z99FMdN.png)
 We observe a decrease of the ratio of notes belonging to major and minor scales (but more strongly marked for major). 
 We might interpret this result as a fashion of songs to explore more accidental notes in the songs with time, and therefore an increase in song diversity. Note that this method should not be confused with the above one, as it only tests the chords' root notes belonging to major or minor scales, while the above section tested for while chord matches.

> How do you discuss and interpret your findings?

Our results seem to show that popular music harmony has become more various during the 1960-1990 period, allowing songs to feature more surprising and accidental notes, hence making it harder to classify songs into a few categories.

The increasing diversity in harmony may be directly influenced by the fast diversification of popular music genres starting around 1950, as can be seen on this interactive map of music evolution: [C16]. 

>Do they confirm or challenge your hypotheses? Do they fit into or contrast with findings in the literature?

The results mostly confirm the general idea behind the research question, which was that pop music seems to be growing in diversity over time, while raising some unexpected particularities. These particularities include for example the opposition between the fast decrease of the major scale popularity against the small decrease of the minor scale popularity. We're not sure how to explain this difference yet, but this may be explained by the (possibly decreasing) evolution of "happiness" in songs between 1960 and 1990. However, other articles seem to have found that valence, a possible measure for happiness in music, does not decreases over that period, challenging this theory [EVB].

On one hand, due to the very ambivalent definition of diversity, our results don't match everything that can be found in literature. Examples such as [TD18] show opposite results when basing song complexity on 8 acoustic factors, but without relying on the melody or harmony. Their results could be interpreted as the music industry using more similar production methods and tools, hence making songs sounding similar from an acoustic point of view. It is also possible that different subsets of pop music have different diversity evolutions : while the most popular songs become more and more similar over time, the extent of pop music constantly grows and becomes more and more diverse.

On the other hand, in the time frame we're interested in, globalization brought cultures to shock and mix, and new technologies allowed more and more people to have easy access to a large amount of information through mass media. More recently, phone applications like Spotify tend to favorize automatic "music mix" of different artists, over traditional album listening, leading people to listen to more various music and genres, as explained in [EP17]. Although the dataset ends around 1990, we can consider that such a phenomena was already present at a least scale during the analyzed period. Being brought to musical diversity can motivate diversified music composition and appreciation, hence leading more various songs.

Additionaly, due to globalization, the music industry has grown a lot and increased its influence over the world. Although we have easier access to a wider variety of music than before, the music we are exposed to passively (present in our environment, for example through radio stations or commercials), is more and more uniform everywhere around the world because it is chosen by a single music industry. Even a platform like spotify, which we cited before, encourages people to listen to the most popular music. By definition, the most popular music pleases the widest possible range of people. It is arguable whether this contributes to music diversity: a specific template might be more efficient than others in order to please the public, and therefore all songs end up sounding similar.


## Arising Difficulties

>Did you encounter any difficulties? Which kind? Are they related to the data, the methods you chose, or your specific questions?

Most difficulties came with the N-grams. Indeed, as no explicit correct grouping of chords can be figured out, we have to compute all n-grams over a song, leading to "duplicates" of chords, for example the 2-grams (0,5) and (5,0) from the sequence (0,5,0,5). Since we can't discriminate between them, we have to arbitrarily filter out "obvious" and "spurious" n-grams, for example the (0,0) 2-gram. We hence prefer to focus on the popularity of selected known chord progressions than checking all n-grams and see which are popular.

This problem can't be avoided since it directly comes from the ambiguous bounds of one chord progression, which cannot be considerated as unique. One could consider a sequence of 10 chords as 2 chord progressions of 5 chords, or as one of 10 chords. Separation of chord progressions into patterns isn't unique. For example, not everyone could agree on classifying a sequence of chords from a transition between 2 parts, as belonging to the preceeding part, or to the following one.

Another difficulty we are facing now is how to interpret the results, and the possible contradictions that may emerge from comparing or theories with onther articles. However, the ambiguous notions used in our research as well as in other articles could be used as a reason for contradictory results.

>How are you going to deal with them? Propose clear and feasible solutions!

A solution for the n-grams problem is to analyse the general shape of the n-grams histogram rather than the precise most used n-grams. We could also focus on a chosen set of n-grams that we know are pleasant to the human ear (corresponding to simple ratio intervals).

## Interesting Problems

>Did you find something unexpected?

Most of the surprising results were already explained above.

>Did you encounter problems that can’t be solved given the limits of your project?

We tried to implement a pattern extractor that would take as input the list of chords from the chorus and verse and output the different patterns used in each. However, the patterns extracted ended up being too specific to each song, and therefore we had almost never 2 songs sharing the same patterns. In the end, we decided that N-gram analysis was much more interesting.

## Next steps towards the final analysis

>What are your next steps?

So far, our results are interesing but we haven't explicited the relation between them and the motivation behind some choices we made. We now shall order our results and build a sensible research path in our writing process, which should lead the reader to a logical list of results that each in turn motivate the question leading to the next one. One very important coming step is hence the redaction of the common thread of our research, sticking all our results and questions together.

>Which aspects of your findings do you want to put in the center?

The aspects focusing on the relative popularity of chords patterns with each other should be privileged over analyzing the absolute ranking of the popularity of the chord patterns. Since a lot of n-grams are only duplicates-like of other n-grams, but can't be avoided, comparing only n-grams that we know make sense is way more sensible.

We will also focus on the proportion plots over years, since they're really demonstrative and highlight a interesting phenomena of diversification which would merit further digging to spot where does this diversification comes from exactly. One possible idea is that we could also make analyze if some groups of chord patterns sharing similarities between each other get more popular over time.

>Which ones do you decide not to pursue further?

Due to time limitations, we decide not to pursue certain topics, however they could be used as a starting point for further and related research.

- In the mode analysis, it could be interesting to assign a mode to each song based on the most used mode of each song, and see the evolution of the number of chords played in the songs that do not belong to this assigned mode. 

- It would also be interesting to plot the number of different modes a specific song belongs to. However it is not really a measure of the musical diversity of a song since songs using very few chords will belong to a lot of different modes, and songs using a lot of different chords will also.

- It could also be interesting to analyze whether 4-grams found only in the chorus and verses of the songs are more representative musically, and maybe less repetitive, than the global 4-grams we computed.

- It might be interesting to try to find diversity measures supporting our hypothesis that although globally the diversity of pop music increased, the diversity of the most popular songs produced by the music industry was reduced.

## References

[C16] Kwinten Crauwels, 2016. *musicmap.* https://musicmap.info/

[EP17] David Erlandsson and Jomar Perez, 2017. *Listening Diversity Increases Nearly 40 Percent on Spotify.* https://insights.spotify.com/us/2017/11/02/listening-diversity-spotify/

[EVB] Eliot Van Buskirk, 2013. *Plotting Music’s Emotional Valence, 1950-2013.* https://insights.spotify.com/us/2013/11/05/musics-emotion-over-time/

[TD18] Andrew Thompson and Matt Daniels, 2018. *Are Hit Songs Becoming Less Musically Diverse?* https://pudding.cool/2018/05/similarity/

[HK10] Hooktheory website 2010 https://www.hooktheory.com/theorytab/common-chord-progressions
# Milestone 4: Final analysis and results

Barret Lucien: lucien.barret@epfl.ch

Membrado Jean-Baptiste: jean-baptiste.membrado@epfl.ch

Perrotta Lucie: lucie.perrotta@epfl.ch

## Precision of Research Question

> State the final version of your research question.

Our final research question is: How can we assess the evolution of chord patterns between years 1950 to 1990 ? 

>Make all assumptions and hypotheses explicit.

We assume that the Billboard songs present in our dataset are in general a good representation of popular songs at a given time, and that we could expect to find similar results when analysing a larger dataset of popular songs.

We also assume that for a song to belong to a scale or mode, we can simply list all the chords belonging to the scale and count how many of a song's chords belong to that scale. This gives us a ratio of belonging. Other methods could have been used but would have probably been more computationally demanding and more ambiguous about what it does mean for a chord to belong to a scale) take for example accidental chords which, while belonging to a scale are deliberately "out of tune"). One problem of this assumption is the use of chords like A minor with maj 7 in A minor, i.e. the use of harmonically specific scales.

Then, we also assume that 4-grams (resp. 3-grams) are a good representation of the behaviour of a chord progression, as suggested in the course. Similarly, we assume that chords have a similar behaviour regardless of the octave pitch they're played at. We then choose to pass all the chords through a modulo 12 operation to restrict them to only one octave. Then, we center all the chords around the tonic note (denoted 0).

>Briefly restate your dataset representation and preprocessing steps (not too detailed, but mention important decisions).

The dataset is parsed in order to get for each song: its title, chord list, year. We then work for each song with all the 4-grams of chords, and also with a subset of all the 4-grams (with cycles and repetions removed). The subset generation will be discussed in the Refinement of Methods section.

We chose to use 3 kinds of plots and methods to analyse the data. 
- First, a 2-diffgram heatmap (representing a 3-gram) in both linear and logarithmic scales, in order to see which 3-grams are mostly used in chords for all songs. We also plot the 3-grams in de-duplicated form (no repetitions) in order to highlight which progressions are popular without taking the length of each chord in account. 3-gram was chosen for its nice plotting properties, and seemed to give a nice idea of the behaviour of the data, that we could later on further analyse with 4-grams patterns.

Let us precise that the term diff-gram was invented by us as it is a derivation from the term n-gram but for the case of interval differences between two subsequent chords. Instead of considering the n-grams being the sequence of chords, we consider here the intervals between chords as our elements of the sequence, hence the name "diff-gram".


![](https://i.imgur.com/PhbuNg5.png)

- Second, we use rank-frequency plots to spot the popularity of each chord, each chord progression (as a 4-gram) in a logarithmic fashion. As expected, most of these plots look very regularily decreasing when plotted logarithmically. These plots confirm the popularities first highlighted by the heatmap (high use of the fifth, fourth, etc.). We also tried to fit the mathematical models onto the data we obtained. We thought about power-law models, but when plotting the y axis in log scale, we cannot find out a suitable function to model our data. It seems that no particular model can efficiently correspond to the rank-frequency plot.


- Third, we use plots over years. These plots are feature:
    - Plots of the popularity of some chord (progression) as a 4-gram over years, with and without repetitions.
    - Plots of the ratio of chords belonging to some mode in all songs of each year, also with and without repetitions. This means that for all the songs of each year, we count how many of their chords actually belong to the major, minor scale, and modes. This results in a percentage for each song, that we then average with all the other songs of the year. This plots principally helped us spotting differences between the two data versions (with and without repetitions).

Example with repetitions (eg. we consider the 4-gram [C,C,C,C]) and with repetitions removed (eg. we only consider 4-grams with no 2 times the same chord in a row):
![](https://puu.sh/DseZu/131d52b449.png)


## Refinement of Methods

>How did you deal with the problems you mentioned in Milestone 3?

We implemented alternative measures with repetitions removed, to compare them with our previous results. This approach was suggested in the feedback for Milestone 3. Applying different cleaning procedures to the data helped us highlight some inferences, that we could not isolate in the results with only one cleaning method. Now, we can compare the results with different cleaning methods and compare the similarities (bias coming from the dataset) and differences (bias coming from the processing). We see that they mostly look the same (on a different scale), so apparently repetitions of chords did not play a important role in our results.

Another problem we had was results interpretation. Since results are not easily explainable (we have only little information about inferences in results, and about underlying causes that may be responsible for the results), we will have to set clear assumptions and disclaimers in order to explain our results unanimously and avoid ambiguity as much as possible. Describing the results as simply as they are is also always a good approach to avoid dragging hurried conclusions.

One important cleaning method we wanted to add in this milestone is the pattern extractor module. Its goal is the same as the de-cycler and de-duplicater: clean our dataset in order to try obtaining more interesting patterns. 
We based the pattern extractor on what is described in Frieler, Klaus. "Computational melody analysis." Inside the Jazzomat. New Perspectives for Jazz Research: 41-84A. A pattern is an ngram that can be found in at least 2 different separate songs. Then, we remove the subpatterns (patterns that appear only inside another pattern, like AB appears in ABC). However, when we tried running the algorithm on our data, we realised it would take a very long time to collect all the patterns as we had 3 intricated for loops. After trying to run the algorithm for more than 12 hours, we decided to let it go especially since the results would theoretically be exactly the same as what we already obtained for ngrams, and would only remove a few ngrams compared with what we already had. In the end, as we take let us say the top 500 most used patterns, it would not have mattered if we remove the patterns that only appear in one song.

Finally, ordering our results in the final paper in order to create a progressive construction of our research will help us structure our findings and establish a clearer meaning to the results. Actually some of our results don't necesseraly lead nor are consequent to other results, but simply help give some additional context to the research and confirm typical results we would expect to find in such a research. For example, the heatmaps don't necessarily help understanding the plots about progression over years, but confirm the typical trend of the chord progression (for instance the bottom-left to top-right diagonal effect).

>Which methods did you use to obtain the final results?

The first thing we did was plotting heatmaps, to give a general idea of the repartition of the chords in the dataset. These plots highlight the repartition of chords in a diagonal like expected, that is, when chords rise, they quickly tend to go back down and inversely. We also figure a high popularity of simple integer ratios in intervals, displayed as red points corresponding to the fifths and fourths. We also note the low popularity of the tritone.

Then, we get to the core of the research, a 4-gram analysis of our dataset. We chose to work with 4-grams to have a higher number of patterns meaningful on their own, and try to avoid pattern fractions or transitions. The choice for 4-grams was suggested during the course as it provides the best results on average (although it depends: trigrams were also mentioned as one of the well performing n-grams for analysis). We first plotted the different 4-grams on a rank-frequency plot in logarithmic scale, and we noticed that the 4-grams matched quite well a decaying exponential, as the occurences of 4-grams in log-scale looks close to linear (especially after the first 100 points):

![](https://puu.sh/DsbVI/5b6d329cea.png)
![](https://i.imgur.com/wgYeFOj.png)

The most common 4-grams are not very interesting because they did not represent a 'musical' pattern, but more structural elements. We tried to select the most interesting patterns through different cleaning techniques: 
- We grouped n-grams into diff-grams, in which we only considered the interval distance between each chord.
- We took all different cyclic permutations of each  patterns and grouped them to one (de-cycling)
- We took all chord repetitions and replaced them by the version without repetitions (de-duplicating)
- We made a pattern finder: out of all N-grams from verse and chorus of songs, we only keep the ones that appear in at least 2 different songs. Among those, we remove sub ngrams (small ngrams which are contained inside a bigger one).
- We plotted separately the 4-grams containing only chords different from each other.

By writing a Python function called `same_pattern`, we were able to get rid of cycles in n-grams. We call the normal data (all the n-grams) the *raw* data, and the n-grams without cycles and repetitions, the *de-cycled, de-duplicated* data. The two datas show a different behaviour, especially when comparing the evolution of the popularity over years. Are "rotated" n-grams of chords really different between them? Is a repeated chord just one longer chord, or many times a short chord?

>Explain your core calculations using equations.

Let's call the dataset $D$ and each song of the dataset $s \in D$, the list of all songs $S$, each chord in a song $c \in s$, the list of all chords $C$. For each computation, the chords $c$ and chord list $C$ were computed in both raw, and de-cycled, de-deplicated form (remove cycles and repetitions in n-grams).

- Get proportion of 4-grams:
$$  (c_n,c_{n+1},c_{n+2},c_{n+3}) , \frac{\#(c_n,c_{n+1},c_{n+2},c_{n+3})}{(a,b,c,d)} \forall a,b,c,d \in C $$
where $(a,b,c,d)$ is any 4-gram and $(c_n,c_{n+1},c_{n+2},c_{n+3})$ is the very 4-gram we're counting the occurences of. A similar computation goes for other n-grams.

- Popularity of 2-grams over 1 year:
$$  (c_n,c_{n+1}) , \frac{\#(c_n,c_{n+1})}{(a,b)} \forall a,b \in c | c.year=year, \forall c \in C  $$

Now, let's name the set of all chords belonging to major, resp. minor, or a mode, $maj$, $min$, $mode$.

- Proportion of songs belonging to major, minor, or a mode over years:
$$ \forall s | s.year=year, \frac{\# s.c \in major}{\# s.c}, \forall year $$
$$ \forall s | s.year=year, \frac{\# s.c \in minor}{\# s.c}, \forall year $$ 
$$ \forall s | s.year=year, \frac{\# s.c \in mode}{\# s.c}, \forall year $$ 
This should not be confused with the proportion of songs entirely fitting major or minor mode, but the average of the proportion of chords belonging to major or minor for **each** song.


>Do not describe all the methods you tried out but only those that lead to the results.

Several results (such as removing the duplicates) didn't lead to anything conclusive in many cases, and we will indeed prefer not to include that into the final report.

>Specify any adjustments you made to pre-existing methods.

As already stated before, the main adjustment was the addition of a de-duplicater and a de-cycler to obtain a more "clean" vision of the behaviour of n-grams. The main results actually come from the comparision between all n-grams, and de-duplicated n-grams.

## Presentation of final results

>Present your results in relation to your research question.

Our research question is : "How can we assess the evolution of chord patterns between years 1950 to 1990" ? 

To answer this question, we first need to look at our dataset's general shape. This is what we explore in the rank frequency plots of 4-grams and heatmaps of trigrams.
Then we look at the evolution of the 4-grams and heatmap plots as a function of time, for each decade. The results are not very telling directly:

![](https://i.imgur.com/tCwCAH7.png)

However, we can compute the difference between each heatmap, and get interesting results. 
For example, if we plot the difference between the heatmap of 1950s and 1960s, we obtain: 

![](https://i.imgur.com/jXj8eTD.png)

On the other hand, when we plot the difference between 1960s and 1970s:

![](https://i.imgur.com/OqN2Rbx.png)

On this graph, we can directly see the differences between chords used in the 1950s and the 1960s.
Our final important result is what we obtained in milestone 3, the plot showing the evolution of the use of certain modes with respect to time:![](https://i.imgur.com/QljSRXg.png)



>Present them in a logical order that does not have to be the order in which you achieved them.

Basically, the results we have can be summarized in the following order : 

- The results of the most-used n-grams being the most obvious analysis at first. We can choose a particular pattern and plot its popularity along years.

- Another possible visualization we saw before is the heatmap as it efficiently shows the repartition of 3-diffgrams in  a 2D space.

- Finally, we saw the plots of the use of major and minor modes among time that ae a little bit more evolved in terms of analysis.

We can add to this the de-duplication and de-cycling steps as well as the pattern extractor module we talked about earlier.

## Discussion of final results

>Interpret and discuss your findings (NOT finding something is also a finding!)

Our findings are quite straightforward to interpret : we found some ways to analyse the complexity of chord progressions along time. What they seem to lead to is that chord progressions seem to be less constrained by major/minor paradigms and globally expand the space spanned on the heatmaps overtime (see the heatmaps for decade 1960s and decade 1970s).

However, such results are highly dependent on the confidence we place in our indexes, and are subject to interpretation. Thus, our results rely more on the methods we propose now than on the results we can draw from the use of those methods.

## Create report template that you will use for your milestone 5 submission

https://www.overleaf.com/8221385371syyzjgcbqfcq
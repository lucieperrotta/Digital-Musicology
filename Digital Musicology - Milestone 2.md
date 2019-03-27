# Digital Musicology - Milestone 2

Barret Lucien: lucien.barret@epfl.ch
Membrado Jean-Baptiste: jean-baptiste.membrado@epfl.ch
Perrotta Lucie: lucie.perrotta@epfl.ch

## Data Gathering
> *How was the data created?
> How did you obtain it?
> In which format is the data?*

We tried scraping the data from the ultimate guitar tabs website, but the scripts we found online to do so either no longer worked or were not available anymore due to legal issues. In the end, we chose to use the **McGill Billboard** dataset as described in [BWF]. The dataset was created to be used as a test set for algorithms of the SALAMI project, whose aim is to find the structure of a song from raw audio data. It was created by expert annotations during 10 months, and most songs in the dataset were double-keyed (analyzed by 2 independent annotators). The dataset was made as diverse as possible by choosing songs classified in [MMF], a dataset in which the authors classified songs using over 50 subgenre labels.
The McGill Billboard dataset is available for free on the ddmal website: http://ddmal.music.mcgill.ca/research/billboard.

The corpus contains 890 songs. The data is split in an index file `index.csv` containing metadata for all songs, and one text file per song (always named `salami_chords.txt`) containing the chord structure. The metadata contains the date of release of the song, the title, the artist and the rank it had on the billboard. Each `salami_chords.txt` file contains the song title, artist, metre, tonic note, as well as a list of chord progressions, their starting times, and the instrument that plays each of them.


## Preprocessing
> *Transform data so that you can effectively work with it.
> Is there missing data that you need to account for?
> Do you need to deal with biases in the data? How?*

We read the corpus' files and parse them into a Numpy array with Python. The parsing reads the index file, and for each row, it looks up the corresponding `salami_chords.txt` file. In order to compare chord progressions across different keys, we choose to store the chords relatively to the tonic. That is, the tonic is always set to be 0, and the song chords are numbered according to the distance to the tonic, in semitones. For instance, if the tonic is C and the first chord is D#, the tonic will be converted to 0 and the first chord to 2.

The parser stores the data into an Numpy array `clean_data` that contains 1 entry per song. Each entry is itself an array of one song's information: `(index, date, name, artist, [relative to the tonic] chord progression list).` Each `chord progression list` is a Numpy array of chords, where each chord is stored as a string of the form `"[relative key]:[chord name]"`.

As said above, the dataset was built to be as diverse as possible, so we don't expect any bias to modify our results.

## Basic Statistics and visualizations
> *How are the features of the data distributed?
> What are appropriate visualizations of the raw data?
> Can you identify correlations of features?
> What can you already infer regarding your research question?
> What are suitable visualizations for the initial results?*
 
Most of the visualization on our data relies on the analysis of the tonic note of the songs and the chord progressions of each song. Those are the main features we can analyze numerically.

For raw data, we plotted the histogram of lengths in number of chords for the songs. We also plotted the repartition of songs written in each possible key. Finally, we plotted the proportions that occupy the three first most used chords in each chord. Basically, we computed the number of times each chord appears in each song, and for each song the percentage of appearance of the three most used chords in the song.

There is an obvious correlation between the note in which the song is written and the chords used in the song. However, when we consider the clean data on which we already "de-rooted" the chords, we can see some interesting phenomenons.
For example, we plotted the chord notes of the chords relative to the key in which the song is written, and we see that songs contain mostly chords that are from the root, the fourth or the fifth of this key.

We also plotted the most used chord modes. Obviously, the most used modes are major, minor and dominant.

For the research question, the main point we can highlight is the predominance of chords coming from the root, the fourth and the fifth : it may be linked to the fact that ascending or descending fifths in transition are particularly pleasant to the ear.
Except for that, we have no further results as we only want to do the pre-processing and visualization of the data for now.


## Concretization of research question
> *Which concrete aspect(s) of your overall research question presented in milestone 1 will you study?
> How can your concrete question(s) be translated into quantitative measures?*

We will extract the chord patterns from our dataset, and answer our first question: which patterns do we find most commonly in the songs and in how many songs do they appear in.
After identifying the main chord patterns, we will try to trace back their origin in our dataset or using other sources, and see if it is possible to retrace the "path" of specific chord patterns across time and space.


## Subsequent steps
> *How will you proceed?
> How do you need to adjust your research plan?
> Which methods did you decide to use?*

So far, we managed to get the full list of all chords played during a song. 
We now need to extract from this list the chord progressions, which are the different patterns that are repeated. We can also extract the number of times each progression is played, and therefore identify which kinds of chords are used for transitions, choruses, verses, etc. 

We will obtain the chord progressions as numerals, as we already transposed them with respect to the given tonic. However there are limitations to this approach: a single song may have modulations (key changes) between two different chord patterns, or may not be written in a well-defined key. As proposed in [BS], we will process our chord progressions to extract 3 features for each chord changes: the quality of the first chord, the interval separating the chord roots, and the quality of the second chord.

## References
**[BWF]** John Ashley Burgoyne, Jonathan Wild, and Ichiro Fujinaga, *An Expert Ground Truth Set for Audio Chord Recognition and Music Analysis*, in Proceedings of the 12th International Society for Music Information Retrieval Conference, ed. Anssi Klapuri and Colby Leider (Miami, FL, 2011), pp. 633–38

**[MMF]** McKay, C., D. McEnnis, and I. Fujinaga. 2006. *A large publicly accessible prototype audio database for music research.* Proc. ISMIR, 160–3.

**[BS]** Broze, Yuri & Shanahan, Daniel. (2013). *Diachronic Changes in Jazz Harmony: A Cognitive Perspective.* Music Perception: An Interdisciplinary Journal. 31. 32-45. 10.1525/mp.2013.31.1.32. 
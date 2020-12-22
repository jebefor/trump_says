# *Trump says*. PDA with NLP+visualization for 35 Trump rallies from 2019-2020.

**Objective**: 
- Helping to solve basic PDA with NLP.

**Main tools**: 
- spaCy, NLTK, visualization (matplotlib, plotly, seaborn, yellowbrick)
- language: Python :snake:

**Dataset**:
- https://www.kaggle.com/christianlillelund/donald-trumps-rallies

**Content**:


    1. Word frequencies
    What's the speech average length and unique words count?
    Which words are more common per word category (noun, adjective and verb)?
    Are verbs used more or less than nouns?
    Which are the most common ngrams?

    2. Named Entities
    Which types of words usually accompany certain NEs?
    Which are the most common NEs for person, organization and geopolitical entities?

    3. Word distributions
    Do certain words appear evenly distributed through the speeches or is it more a temporary usage?
    How two or more words compare in frequency distribution?
    Do certain words appear in the same context?

    4. Sentiment
    Which is the overall sentiment?
    Which is the sentiment flow within the speeches? Is there a pattern?
    Which sentiment usually describes a certain NE?

**Results**:

**1. Word frequencies**:

Our main question here was how complex is the discourse. For the given speeches, the language used proved to be quite simple, with 0.12% of the total unique words accounting for 10.83% of the total oral text. 

![alt text](visualizations/1.word_frequencies/total_vs_unique_words.png)

Furthermore, we looked at the noun/verb ratio, linked to the amount of tension in the political discourse. While [Carlos Ahumada's analysis](https://towardsdatascience.com/nlp-using-spacyr-to-analyze-presidential-speeches-49c10ef37aef) reported a score of 1.24 for Trump's inauguration speech back in 2016 (meaning slightly more nouns are used compared to verbs, i.e., less tension), our analysis shows a drop to 0.91 (increasing tension).

**2. Named Entities**:

The purpose of this section was to see the use of different named entities in Trump's rallies (person, geopolitical and organization entities).

While for organizations the amount of mentions to the respective entities are much more balanced (see [here](https://plotly.com/~jebefor/9/) the interactive plot), we observed that for person Joe Biden (24.4%), Donald Trump (13.6%), Hillary Clinton (7%) and Mike Pence (6.52%) make up more than half the mentions to person names (plot [here](https://plotly.com/~jebefor/1/)). Even more, America (33.1%) and China (14.1%) alone make up almost 50% the mentions of geopolitical entities (plot [here](https://plotly.com/~jebefor/7/)).

A good illustrator of these results are the collected wordclouds on the types of words that usually accompany these entities (i.e., nouns, verbs and adjectives). 
Not only these clearly show a focus on certain entities over others that we can expect from the political context, but also show the different treatment depending on the gender in both frequency (lower) and types of accompanying words (mentions to attractiveness, both in the case of women).

- Examples: 

ent: **Ivanka**, word type: adj

![alt text](visualizations/2.acc_words_NE/ADJ/Ivanka_ADJ.png)

ent: **Kamala**, word type: noun

![alt text](visualizations/2.acc_words_NE/NOUN/Kamala_NOUN.png)

ent: **Joe**, word type: adj

![alt text](visualizations/2.acc_words_NE/ADJ/Joe_ADJ.png)

ent: **AOC**, word type: adj

![alt text](visualizations/2.acc_words_NE/ADJ/AOC_ADJ.png)

ent: **Bernie**, word type: adj

![alt text](visualizations/2.acc_words_NE/ADJ/Bernie_ADJ.png)

**3. Word distributions**:

In this part of the analysis we go over two different approaches to see how words are distributed throughout the discourse.

The first one deals with single word frequencies over the rallies, as seen in the examples below. Red and blue hues correspond to the winning party in the cities' state in the 2016 Elections. Thus we can observe the importance a given word has at both the global and local level of the speech.

![alt text](visualizations/3.word_distribution/word_biden_by_rally.png)

![alt text](visualizations/3.word_distribution/word_virus_by_rally.png)

In the second approach, we look at lexical dispersion plots to:

- compare the frequency of several words at a time:

![alt text](visualizations/3.word_distribution/lexical_dispersion2.png)

- or to see if these words usually occur in the same context:

![alt text](visualizations/3.word_distribution/lexical_dispersion4.png)

**4. Sentiment**:

In the last part of the analysis we go over the predominant sentiment in the speeches and towards certain entities.

Being -1 the most extreme negative and 1 the most extreme positive, the average compound (sentiment) rate for all rally speeches is of 0.16.

![alt text](visualizations/4.sentiment_flow/average_rates_by_rally.png)

Another interesting observation we make is comparing the overall pattern for different periods, taking into account a certain event. In our case, we look at how the COVID-19 pandemic may have affected the intensity of the sentiment flow.

*Before April 2020*

![alt text](visualizations/4.sentiment_flow/coronavirus/before_april_2020.png)

*After April 2020*

![alt text](visualizations/4.sentiment_flow/coronavirus/after_april_2020.png)

Finally, concerning sentiment rates of words accompanying certain named entities, we look at some remarkable examples by calculating the mean over the sentiment of all adjectives that come up in the same context window.

*keyword* | Bernie | Biden | Obama | China | Trump | America | Pence 
--- | --- | --- | --- | --- | --- | --- | --- 
*sentiment compound* | -0.15 | -0.09 | 0.07 | 0.14 | 0.23 | 0.42 | 0.54

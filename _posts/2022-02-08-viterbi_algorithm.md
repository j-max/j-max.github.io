---
layout: post
title: Viterbi
---

The second week of the Coursera NLP specialization course,
"Probabilistic Models in NLP", focuses on the Viterbi algorithm.  The
Viterbi algorithm is a Hidden Markov Model used to tag a corpus by
part of speech. The coding exercise for this week is fairly intense,
but getting through it helped me understand key components of the
algorithm: the HMM and the transition and emission matrices.  This
post will explain these concepts at a high level.

Markov chains are a type of stochastic model which use prior states to
predict future states via probabilities associated with different
transitions.  For all the possible changes to the system, a
probability for reaching another state from a previous state is
calculated. I.E., what is the probability the state will stay the
same, what is the probability the state will change from A to B.  In
the case of POS tagging, the states are the part of speech of any
given word.  So, if the prior word is a noun at the beginning of a
sentence, because of the common SVO pattern in the English language,
one would expect a verb to have a higher probability of coming next
than an object.

In a Hidden Markov Model, the states are not observable. In the
instance of a sentence that is not POS tagged, the part-of-speech tags
are not visible to the machine, and are thus hidden.  In order to tag
the words, the model trains on a tagged corpus to compute 2
probability matrices: the transition and emission matrices.  It then
uses these probabilities to compute the most likely tags for sentence.

The transition matrix holds the probability of transitioning from each
part of speech present in the corpus to every other part of speech.
This is a relatively simple calculation. Using the training corpus,
count the number of times a given POS tag (A) is followed by another
POS tag (B).  Then divide this count by the count of all occurrences
of the POS tag (A).  There are a few details, such as smoothing and
consideration of words that start a sentence, which I will not discuss
here.

The emission matrix holds the probability of a word appearing given a
part of speech tag.  Again, this is a relatively simple calculation.
Count the number of times a word has a part of speech, and divide that
number by the number of appearances of that part of speech.

The Viterbi Algorithm then uses these two matrices to create the
probability of a sequence of tags for an entire sentences.  It starts
by scanning all possible choices for the POS of the first word from
the transition matrix. Then it multiplies that probability by the
probability of the first word having that part of speech, as read in
the emission matrix.  It then continues this multiplication pattern of
transition and emission for each word in the sentence, and calculates
a probability for the POS tag for the entire sentence.  It repeats
this process for other paths, and selects the path with the highest
probability as the correct POS selection.


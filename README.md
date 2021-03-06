# SentimentAnalysis
Semeval challenge 2013, Implementation of paper NRC-Canada:Building the State-of-the-Art in Sentiment Analysis of Tweets


This project implements the approach of paper [1], for the course work of CmpE 561 - Natural Language Processing.
It is for analyzing the sentiment of a given tweet, extracting feature vectors and using svm to predict according to a training dataset. We followed the approach  pf Muhammed et.al.[1] and also added our own annotated lexicons to the feature vector.

The features we used were;
+ Adjectives
  * Tokenize training tweets (Outputs of CMU Pos Tagger is used)[7]
  * Create a dictionary with adjectives that has at least 3 occurrences.
  * Extract features from tweets using the dictionary.
  * Better than using word n-grams since this one leads to more dense feature vectors.
+ POS
  * CMU Pos Tagger is used for tagging tweets.[7]
  * There are 25 tags.
  * The number of occurrences of each part-of-speech tag is used as feature.
+ Lexicons
+ Emoticons
+ Negation
  * The number of negated context is used as feature.
  * The list of negation words was adopted from Christopher Potts’ sentiment tutorial.[8]
  * Negated context also affects n-grams and lexicon feature.


The lexicons used;
+ NRC Emotion Lexicon [11,12]
+ MPQA Lexicon [13]
+ Bing Liu Lexicon [9]
+ NRC Hashtag Sentiment Lexicon [1]
+ Sentiment140 Lexicon [10]
+ DGE Emoticon Lexicon :) (Our own annotated data)

4 features extracted from lexicons;
+ total count of tokens in the tweet with score(w, p) > 0;
+ total score of the tweet ;
+ the maximal word score in tweet ;
+ the score of the last token in the tweet with score(w, p) > 0;

Classification;
+ SVM [6]
+ 3 classes; Positive, Negative and Neutral
+ C = 0.005 or C = 1
+ Extra penalty weight for misclassification for negative tweets - because underrepresented.

The results can be found on the report.pdf

References

1. Mohammad, Saif M., Svetlana Kiritchenko, and Xiaodan Zhu. "NRC-Canada: Building the state-of-the-art in sentiment analysis
of tweets." arXiv preprint arXiv:1308.6242 (2013).

2. Kökciyan, Nadin, et al. "Bounce: Sentiment classification in Twitter using rich feature sets." Second Joint Conference on Lexical
and Computational Semantics (* SEM). Vol. 2. 2013.

3. Mohammad, Saif M., and Peter D. Turney. "Crowdsourcing a word–emotion association lexicon." Computational Intelligence
29.3 (2013): 436-465.

4. Wilson, Theresa, Janyce Wiebe, and Paul Hoffmann. "Recognizing contextual polarity in phrase-level sentiment analysis."
Proceedings of the conference on human language technology and empirical methods in natural language processing.
Association for Computational Linguistics, 2005.

5. Hu, Minqing, and Bing Liu. "Mining and summarizing customer reviews."Proceedings of the tenth ACM SIGKDD international
conference on Knowledge discovery and data mining. ACM, 2004.

6. Chih-Chung Chang and Chih-Jen Lin, LIBSVM : a library for support vector machines. ACM Transactions on Intelligent Systems
and Technology, 2:27:1--27:27, 2011. Software available at http://www.csie.ntu.edu.tw/~cjlin/libsvm

7. Gimpel, Kevin, et al. "Part-of-speech tagging for twitter: Annotation, features, and experiments." Proceedings of the 49th Annual
Meeting of the Association for Computational Linguistics: Human Language Technologies: short papers-Volume 2. Association
for Computational Linguistics, 2011.

8. Potts, Christopher. "Sentiment Symposium Tutorial." Sentiment Symposium Tutorial. N.p., n.d. Web. 08 Feb. 2017. <http://sentiment.christopherpotts.net/index.html>

9. Minqing Hu and Bing Liu. 2004. Mining and summarizing customer reviews. In Proceedings of the tenth ACM SIGKDD international conference on Knowledge discovery and data mining, KDD ’04, pages 168–177, New York, NY, USA. ACM.

10. Alec Go, Richa Bhayani, and Lei Huang. 2009. Twitter Sentiment Classification using Distant Supervision. In Final Projects from CS224N for Spring 2008/2009 at The Stanford Natural Language Processing Group.

11. Saif M. Mohammad and Peter D. Turney. 2010. Emotions Evoked by Common Words and Phrases: Using Mechanical Turk to Create an Emotion Lexicon. In Proceedings of the NAACL-HLT 2010 Workshop on Computational Approaches to Analysis and Generation of Emotion in Text, LA, California.

12. Saif Mohammad and Tony Yang. 2011. Tracking Sentiment in Mail: How Genders Differ on Emotional Axes. In Proceedings of the 2nd Workshop on Computational Approaches to Subjectivity and Sentiment Analysis (WASSA 2.011), pages 70–79, Portland, Oregon. Association for Computational Linguistics.

13. Theresa Wilson, Janyce Wiebe, and Paul Hoffmann. 2005. Recognizing contextual polarity in phrase-level sentiment analysis. In Proceedings of the conference on Human Language Technology and Empirical Methods in Natural Language Processing, HLT ’05, pages 347–354, Stroudsburg, PA, USA. Association for Computational Linguistics.

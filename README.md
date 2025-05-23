# KOSAC
KOrean Sentiment Analysis Corpus


## About
The KOrean Sentiment Analysis Corpus, KOSAC, is built for capturing sentiment expressions and their patterns in Korean and representing their meaning to be interpretable for a computer. To represent the meaning, a fine-grained annotation scheme called KSML (Shin et al., 2012) is developed identifying key components and properties of sentiments based on solid theoretical background. The annotation scheme has been employed in the manual annotation of a 7,713-sentence corpus of 332 news articles from the Sejong syntactic parsed corpus.

You can find details in our [Annotation Scheme (PACLIC26)](http://ling.snu.ac.kr/kosac/pub/PACLIC26.pdf) and [Annotation Guideline](http://ling.snu.ac.kr/kosac/pub/Sentiment_Markup_total-v1.2.pdf).

### Annotated Sentences
|Subjective|Objective|Total|
|:----------:|:---------:|:-----:|
|2658      |5055     |7713 |

### Annotated Seed Tags
|	Agree.	|Argu.	|Emotion	|Intention	|Judgment	|Speculation	|Others	|Total|
|:---------:|-------:|---------:|-----------:|---------:|-------------:|-------:|-----:|
|Dir-Action	|1	|9	|71	|8	|38	|0	|1	|128|
|Dir-Explicit	|156	|277	|341	|276	|2740	|157	|40	|3987|
|Dir-Speech	|8	|1149	|22	|28	|86	|13	|7	|1313|
|Indirect	|255	|321	|720	|409	|6086	|63	|22	|7876|
|Writing-Device	|5	|98	|9	|306	|764	|172	|2957	|4311|
|Total	|425	|1854	|1163	|1027	|9714	|405	|3027	|17615|

<br>

## ReadMe

### About Corpus
The KOSAC data in the csv formatted file contains all annotated tags: subjective, objective, and seed tags.

This README is to provide a guide to understand the listed tags in csv format.
Each column is explained with number below.

***For detailed explanations of column values, see the guideline or [Shin et al. (2012)](https://aclanthology.org/Y12-1019/).

1. tag_id
This tag_id is unique ID for each tag in the whole KOSAC data.
The ID may not be continuous since some tags are deleted in annotation process.

2. sent_id
The sent_id refers to which sentence the tag belongs to.
Because the sentence ID is unique for each sentence, it helps to gather all 
tags that belong to it.

3. tag type
The tag type shows if the tag is a sentence level tag, subjective or objective, 
or an under-sentence level tag, seed tag.

4. morphemes
This column contains expressions on which tags are anchored. Only seed tags 
have anchored expressions on this column. Anchors of objective and subjective 
tags can be found on sentence-morph column. The format of each morpheme is 
expression/part_of_speech#id, as “사랑/NNG#57926”. The id can be used to 
match the expression in the whole sentence.

5. expressive-type
The expressive-type column contains how the expression is delivered by a writer 
of the sentence. The values of the column are direct-explicit, direct-speech, 
direct-action, indirect, and writing-device.

6. subjectivity-type
The subjectivity-type attribute indicates what kind of sentiment the archored 
expression belongs to. The categories are Judgment, Argument, Intention, 
Agreement, Speculation, Emotion, Others.

7. subjectivity-polarity
The subjectivity-polarity has positive, negative, complex, and neutral. This 
value composes one united value with subjectivity-type value, for instance, 
judgment-pos, intention-pos. This value does not refer to the usual polarity 
sense of expressions. For more details, refer to the documents above.

8. polarity
The polarity attribute indicates the polarity sense of the anchored expression.

9. intensity
The intensity column shows the how strong the subjective expression is.

10. nested-source
This column shows the source of the expression and the path of the delivering 
subjectivity via sources. The left most source is always writer, though it is 
omitted. The format is source1-source2-source3. It is supposed that it is less 
likely to be the case that the sources of a subjective expression are more than 
four.

11. target
The target column contains the target expressions to which the direction of 
sentiment towards. The format is target1-target2-target3, indicating that 
multiple targets are possible for a sentiment expression.

12. comment
This column is for an annotator to leave a comment on a tag.

13. confident
This confident column is to leave a marker indicating how confident an 
annotator is about the tag.

14. raw-sentence
The raw-sentence column contains the original sentence that the tag belongs to.

15. sentence-morph
The raw-sentence column contains the original sentence with morphemes that the 
tag belongs to.

### Corpus Files
The two files are different for the subjectivity values of direct quote sentences.
`kosac-corpus-130808.csv` is the modified version for a sentence subjectivity recognition task.

<br>

### About Lexicon
Korean Sentiment Lexicon

This vocabulary list aims to provide sentiment characteristics at the morpheme level to enable broad use of KOSAC data in Korean sentiment analysis research. It is based on the assumption that the sentiment properties of a vocabulary item can be derived from the sentiment properties of the core subjective expression (hereafter referred to as the Seed) that contains the item. Morpheme N-grams extracted from the Seed were used as the vocabulary entries. However, when one Seed includes another, the higher-level Seed may cite, negate, or emphasize the lower-level Seed, potentially altering its sentiment values. Therefore, to ensure consistent sentiment values, only morphemes from the lowest-level Seeds that do not overlap with others were used. All possible morpheme N-grams were extracted, except those containing non-Hangul characters or punctuation marks.

The six CSV files included in lexicon.zip each correspond to one semantic feature and contain the distribution of semantic feature values for 16,362 morpheme N-gram headwords (3,476 unigrams, 6,579 bigrams, and 6,307 trigrams) obtained using the method described above. Each row in a file represents the sentiment characteristics of one N-gram. The meanings of the column values, in order, are as follows.

- ngram: Morphemes that make up the N-gram headword
- freq: Number of Seeds that contain the given N-gram
- (semantic feature value): Proportion of Seeds containing the N-gram that have this value
- max.value: Name of the value with the highest proportion
- max.prop: Numerical value of the highest proportion


<br>

## Citation
If you use these dataset, please cite the following paper(s):
```
@article{kosaccorpus,
    title={KOSAC(Korean Sentiment Analysis Corpus): 한국어 감정 및 의견 분석 코퍼스},
    author={김문형, 장하연, 조유미, 신효필},
    year={2013},
    journal={Information and Compuation},
  }

@article{kosactool,
    title={Morpheme-based Annotation Tool for Korean Text},
    author={Andrew Cattle, Munhyong Kim, and Hyopil Shin},
    year={2013},
    journal={Proceedings of the American Association for Corpus Linguistics},
  }

@article{kosacguideline,
    title={Annotation Scheme for Constructing Sentiment Corpus in Korean},
    author={Hyopil Shin, Munhyong Kim, Yu-Mi Jo, Hayeon Jang, and Andrew Cattle},
    year={2012},
    journal={Proceedings of the 26th Pacific Asia Conference on Language},
  }
```

# Modelling of Turkish Verbs
 This project includes the morphophonological modelling of Turkish verbs using Foma ([Hulden, 2009](https://fomafst.github.io/)).
 ## Basic Morphological Structure of Turkish Verbs
 As an agglutinating language, Turkish has a complex morphological structure. There are six different person suffix, which vary according to many tense and mood suffixes. Besides, the tense and mood suffixes in Turkish can be combined with each other in certain situations, which creates compound tenses. Turkish verbs can also be passivized and negated with passive suffixes and negation suffixes. When these suffixes are added to the root of the verbs, they effect the morphology and phonology of the following tense and indirectly person suffixes. The basic order of the suffixes are given below.
 
> Verb+Tense/Mood+Person\
yap+tı+m\
do+Past+1pSg\
I did/have done.

 If the verb is passivized or negated, and has a compound tense, the order is as followed.
 
> Verb+Passive+Negation+Tense/Mood+CompoundTense+Person\
gör+ül+mü+yor+du+nuz\
see+Pass+Not+Cont+Past+2pPl\
You (all) were not being seen.

When designing this model, the order stated above is used, and the lexicons for each category are designed for the possible combinations. For example, When the verb is negated, the aorist tense suffix changes. Therefore, there are two different lexicons for positive and negative verbs. 
 ## Tense, Aspect and Mood
 ### Compound Tenses
 ## Voice
 ## Person
 ## Negation
 ## Phonological Changes in Turkish
 ## Abstractions
 ## Testing
 ## Further Development

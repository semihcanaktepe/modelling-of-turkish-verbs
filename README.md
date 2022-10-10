# Morpho-phonological Modelling of Turkish Verbs in FOMA
This project is intended to model the morphophonological structure of Turkish verbs using _Foma_ ([Hulden, 2009](https://fomafst.github.io/)). This project is still in **beta**, it needs revision. 
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
In Turkish, the basic tense, aspect, mood suffixes are aorist _(-Hr or -Z)_, continuous _(-Hyor_ or _-mAktA)_, past _(-DH)_, past perfect _(-mHş)_, future, _(-AcAk)_, must _(-mAlI)_, desire _(-YA)_, condition _(-sA)_, possibility/ability _(-Abil)_ and imperative _(0)_ suffixes. You may ask what the capital letters are. Obviously, there is no capital letter in the words; they are abstractions of the possible sounds varying accordingly _(These abstractions are explained in the section, Phonological Changes in Turkish)_.  
### Compound Tenses
 Sometimes, the suffixes above can create compound tenses in certain combinations such as continuity in the past _(-Hyor-dH)_ and condition in the future _(-AcAk-sA)_. Not every suffix create such compound structures. Therefore, they are classified in four categories as to which suffixes can be attached to them. 
## Voice
Turkish verbs may have four different voices: active, passive, causative and reciprocal. Some of the verbs cannot be passivized. These are are intransitive verbs. However, some verbs in Turkish can be passivized although they are intransitive. The passive suffixes are _-Hl_ and _-Hn_, the causative suffix is _-DHr_, and the reciprocal suffix is _-Hş_. _(In this project, causative and reciprocal voices are not included because they change the verbs categories.)_ 
## Person
Person suffixes in Turkish vary according to the tense, aspect and mood suffixes. In this project, there are four different person suffix classes for different tense groups. These groups are given below with the changes in each.
```
First Class		Second Class		Third Class		Fourth Class

1person:Hm		1person:m		1person:m		2person:0
2person:SHn		2person:SIn		2person:n		2personPl:YHn
3person:0		3person:0		3person:0		2personPl:YHnHz
1personPl:YHz		1personPl:Iz		1personPl:k		3person:sHn
2personPl:SHnHz		2personPl:sInIz		2personPl:HnHz		3personPl:sHnlAr
3personPl:0		3personPl:0		3personPl:0
3personPl:lAr		3personPl:lAr		3personPl:lAr
```
The first class includes the generic person suffixes, second class is for aorist tense, third class is for past, condition and desire suffixes, and the fourth class is intended for imperative mood. 
## Negation
Turkish verbs are simply negated by the use of _-mA_ suffix. It changes the realization of aorist tense.
## Phonological Changes in Turkish
In Turkish, when some suffixes are attached to the words, they sometimes assimilate their sound structure, which creates phonological changes. As mentioned above, the ones subject to such changes are abstracted using capital letters. To realize these morphophonological changes, some set of rules must be defined according to Turkish phonology. Some of the rules are given below. _"^"_ marks the morpheme boundaries.

```
Vowel Harmony: To handle H abstraction.
define HRule  		H -> %+HIGH & %+ROUND & %+BACK || [%+BACK & %+ROUND] \V* _ ,,
         		H -> %+HIGH & %+ROUND & %-BACK || [%-BACK & %+ROUND] \V* _ ,,
          		H -> %+HIGH & %-ROUND & %+BACK || [%+BACK & %-ROUND] \V* _ ,,
          		H -> %+HIGH & %-ROUND & %-BACK || [%-BACK & %-ROUND] \V* _ ;

ARule: To handle a/e variation.
define ARule  		A -> %-HIGH & %-ROUND & %+BACK || %+BACK \V* _ ,,
			A -> %-HIGH & %-ROUND & %-BACK || %-BACK \V* _ ;

DRule: To handle d/t variation, D is assimilated after voiceless consonants.
define DRule        	D -> t || %-VOICE "^" _ ,, D -> d || \%-VOICE "^" _ ;

IRule: To handle ı/i variation.
define IRule    	I -> ı || a \V* _ ,, I -> i || e \V* _ ;

SRule: To reduce S in some positions.
define SRule   		S -> 0 || H "^" _ ,, S -> s || \H "^" _ ;

YRule: To handle Y in ağlaYınız or yapsaYdın etc.
define YRule    	Y -> y || V "^" _ [V|H] ,, Y -> 0 || C "^" _ ;

Consonant Change: To handle consonant assimilation in some cases*. 
define ConsChange   	k -> ğ || _ "^" V ;

ZClear: To eliminate negative aorist gelme(z)m conflict.
define Zclear   	Z -> 0 || _ "^" [m|y] ,, Z -> z || _ "^" \[m|y] ;

Clearup: To get rid of the morpheme boundary symbols "^".
define Cleanup		"^" -> 0;
```
*Please refer to [Oflazer et al. (1994)](https://pdfs.semanticscholar.org/ec7f/c4cc14757addef6ba1cec3902bddb6e983a6.pdf)
for more information.

## Testing the Model
You can find the necessary files of the model under this repository. This model, as the mechanics of _Foma_ suggest, has two-way system, which consists of the surface form of the verbs _(up)_ and their underlying morphological structure _(down)_. The model can be test with the possible combinations. When the _up_ form of the verb is given, the _down_ form must be present or vice versa. To detect the possible problems, a down test is provided. 
### Further Development
As you can see, when down test is applied, some of the forms are not realized properly. The possible reason is the morphology of Turkish is so complex that it always has unpredictable instances. Therefore, the rules and their application order cannot handle everything. However, these problems can be overcome with the future development of this system. You can contact me if you have any suggestions to develop this system, _secanakt [dot] gmail [dot] com_.

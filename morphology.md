---
layout: guidelines
title: CAMeL Guidelines | Morphology
camelpos: CAMEL POS
---
CAMEL POS Schema and Guidelines
===


## Motivation and Goals:
{{ page.camelpos }} is inspired by the ARZATB tagset and guidelines (Maamouri et al., 2012) 
which is  based on the PATB guidelines (Maamouri et al., 2009). The {{ page.camelpos }} 
is designed as single tagset for both MSA and the dialects with the following goals in 
mind: 

-  Facilitating research on adaptation between MSA and the dialects, 
and among the dialects.
-  Supporting backward compatibility with previously annotated resources.
-  Enforcing a functional morphology analysis that is deeper and more compatible
with Arabic morphosyntactic rules than form based 
analysis (Alkuhlani and Habash, 2011).

## Overview
The {{ page.camelpos }} tags and features are the union of those in MSA and the dialects. 
Features are available to use when needed. 
For example case and state features are used more often in MSA; but on 
the other hand, dialects tend to have many more clitics than MSA, including 
non-MSA ones. 

One main property of {{ page.camelpos }} tagset that sets it apart from ARZATB is that 
the morphological features of both gender and number of nominals are annotated 
functionally (i.e. semantically) (Alkuhlani and Habash, 2011; Smrž, 2007). 
This decision allows us to assign the features to the baseword without the need to 
specify the surface form affixes that mark form gender and number. 
This is not the case in ARZATB, where broken (irregular) plural nouns are tagged 
as singular because they do not use the sound plural affixes. 

Another property is that in {{ page.camelpos }} tagest we omit case and state 
features for nominals, and voice and mood for verbs when annotating dialecta 
Arabic as the dialects have almost lost them completely, except for some high 
frequency fossilized MSA forms, such as <span dir="rtl">طبعاً</span> 
<span class="caphi">/t. a b 3 a n/</span>[^1] ‘of course’ which retains an indefinite ending.

The main part of the word, that is the baseword, is tagged in the following 
format: `POS.features`, where `POS` is the core POS tag and `features` is the 
possible feature combination that goes with the POS tag, a `.` separates the POS 
from the feature combination. Proclitics, however, get only a `POS` tag since 
they have no features. However, pronominal enclitics get a similar tag format 
as the baseword (i.e.`PRON.features`).

## Schema details

### Core POS
The following table shows the list of `POS` tagset used in this schema compared 
with the ones used ARZATB. The tagset is divided into three categories according 
to the D3 tokenization scheme (Habash et al, 2010): proclitics (14 tags), enclitics
(2 tags) and baseword (39 tags). Together with the features, {{ page.camelpos }} tagset
maps to ARZATB and retains backward compatibility. It also offers an intuitive 
Arabic scheme that is suitable to use for annotation.
{% include pos_table.html %}

### Features
{{ page.camelpos }} provides full array of features: 

- **A**spect with the values **P**erfective, **I**mperfective and **C**ommand.
- **P**erson with the values **1**st, **2**nd, **3**rd.
- **G**ender with values **M**asculine and **F**eminine. 
- **N**umber with values **S**imgular, **D**ual and **P**lural.
- **S**tate with values **D**efinite, **I**ndefinite and **C**onstruct. 
- **C**ase with values **N**ominative, **G**enitive and **A**ccusative. 
- **V**oice with values **A**ctive and **P**assive.
- **M**ood with values **S**ubjunctive, **I**ndicative and **J**ussive. 

Not all the features mentioned are necessarily relevant to the dialects. In the
full POS tag, the specified values of the different features
will appear in the following order:

`<POS>.<A><P><G><N>.<S><C><V><M>`
{: style="text-align: center;"}


For a subset of `POS` tags in the baseword category, each tag has a limited 
number of possible feature combinations that is paired with it. Below is the 
list of the `POS` tags that take features and their possible ordered combination.
Note that the below combinations are for the dialects, in the case of MSA, 
nominals take **C**ase and **S**tate, and verbs take **V**oice and
**M**ood in addition to the listed feature combinations.

- **NOUN**, __NOUN\_\*__, **ADJ**, __ADJ_*__ All nominals take the combination 
of **G**ender, **N**umber. For example جالس /y aa l i s/ ‘sitting’ is tagged 
`ADJ.MS` ; In the occasional uses of **S**tate, such as <span dir="rtl">طبعاً</span> 
<span class="caphi">/t. a b 3 a n/</span> ‘of course’ the tag would be `NOUN.MS.I`. 

- **VERB** All verbs take the combination of **A**spect, **P**erson, **G**ender 
and **N**umber. For example <span dir="rtl">يقطع</span> <span class="caphi">/y i g t. a 3/</span> ‘cut’ is tagged as `VERB.I3MS`

- **PRON** All pronouns take the combination of **P**erson, **G**ender and 
**N**umber. For example <span dir="rtl">انتي</span> <span class="caphi">/2 i n t y/</span> ‘you \[fs\]’
is tagged as `PRON.2FS`

- **PRON_DEM** All demonstrative pronouns take the combination of **G**ender 
and **N**umber. For example <span dir="rtl">هاذا</span> <span class="caphi">/h aa dh a/</span> ‘this’ is tagged as `PRON_DEM.3MS`

In cases where a feature is not present, such as gender in verbs of first person 
inflections, the gender feature is simply dropped and does not require a 
placeholder since the possible feature values are ordered and unique. For example
the imperfective 1st person verb <span dir="rtl">أقول</span> <span class="caphi">/2 a g uu l/</span> ‘I say’ will be
tagged as `VERB.I1S`

## Detailed annotation guideliens
Morphological annotation using {{ page.camelpos }} assumes that each word is 
tokenized using the D3 tokenization scheme. Therefore, each token gets at least a `POS` tag according to the table above.
In a large-scale full morphological annotation task, additional annotations are usually provided, such as lemmatization, English gloss, amd dialect identification.
In this section we provide detailed guidelines in the context of a comperhensive annotation task.

<details>

<summary markdown="block"> 
### Tokenization
</summary>

The tokenization scheme recommended when annotating using {{ page.cameltools}} is D3.
: **D3** tokenizes all clitics: question particle, conjunctions, particles, prepositions, articles, and pronominal enclitics.

- In the tokenization task, all tokens must be orthographically normalized, that is undoing all of the morphophonemic and orthographic rewrite rules. For example, the word <span dir="rtl">مكتبتها</span> should be tokenized as <span dir="rtl">مكتبة +ها</span> NOT <span dir="rtl">مكتبت +ها</span>
- Remember that clitics are optional to word formation and they include particles and pronouns.

| Tokenization Phenomenon 	| Arabic Word 	| Tokenization   	| English Gloss               	| Dialect 	|
|-------------------------	|-------------	|----------------	|-----------------------------	|---------	|
| Definite Article        	| للمكتب      	| ل+ ال+ مكتب    	| for the office              	| GLF,EGY 	|
| Ta Marbuta              	| مكتبتنا     	| مكتبة +نا      	| our library                 	| GLF,EGY 	|
| Ta Marbuta              	| كاتباها     	| كاتبة +ها      	| she wrote it (deverbal)     	| GLF,EGY 	|
| Alif Maqsura            	| حكاها       	| حكى +ها        	| he recounted it             	| GLF,EGY 	|
| Hamza Form              	| بهاءه       	| بهاء +ه        	| his glory                   	| GLF,EGY 	|
| Waw-of-Plurality        	| قالوها      	| قالوا +ها      	| They said it                	| GLF,EGY 	|
| Various clitics         	| وهتجننني    	| و+ ه+ تجنن +ني 	| and she will drive me crazy 	| EGY     	|
| Various clitics         	| وبتجننني    	| و+ ب+ تجنن +ني 	| and she will drive me crazy 	| GLF     	|

</details>


<details>
<summary markdown="block"> 
### Lemmatization
</summary>

The lemma is the citation form of the word.
Across all our guidelines, we follow the lemma specification in 
(Graff et al, 2009), where:
- The lemma of all **nominals** is the masculine singular form of the word or 
the feminine singular form if no masculine form exists.
- The lemma of a **verb** is the perfective 3rd person masculine singular form.
- For all others (i.e. particles, adverbs, ... etc) the lemma is the same 
form of the baseword.

**Notes**:
- For some nominal cases such as <span dir="rtl">اسم الوحدة</span> ‘collective plurals’ which are also 
uncountable nouns, the lemma is the same as the noun. See examples in the 
following table.
- The diacritization of the lemma include adding all the short vowel diacritics 
except for the sukun ‘absence of a vowel’.
- Cases to look out for are the <span class="caphi">/oo/</span> and <span class="caphi">/ee/</span> long vowels. The vowel <span class="caphi">/oo/</span> is marked as <span dir="rtl">ـَو</span>, <span class="caphi">/ee/</span> is marked either as <span dir="rtl">ـَي</span> or <span dir="rtl">ـِا</span>.
- In the case of long vowels <span class="caphi">/aa/</span>, <span class="caphi">/uu/</span>, and <span class="caphi">/ii/</span> a short vowel marker of the same kind precedes the long vowel (i.e. <span dir="rtl">ـَا</span>, <span dir="rtl">ـُو</span>, and <span dir="rtl">ـِي</span>).

| Arabic Word 	| Lemma 	| POS       	| English        	| Comments/Examples/Diaclect   	|
|-------------	|-------	|-----------	|----------------	|------------------------------	|
| كتب         	| كِتاب  	| NOUN.MP   	| books          	| GLF,EGY                      	|
| كتبوا       	| كَتَب   	| VERB.P3MP 	| They wrote     	| GLF,EGY                      	|
| تفاح        	| تُفَّاح  	| NOUN.MS   	| apples         	| GLF,EGY , collective plurals 	|
| تفاحة       	| تُفَّاحَة 	| NOUN.FS   	| apple          	| GLF,EGY                      	|
| تفاحات      	| تُفَّاحَة 	| NOUN.FP   	| apples         	| GLF,EGY                      	|
| تمر         	| تَمر   	| NOUN.MS   	| dates (fruit)  	| GLF,EGY , collective plurals 	|
| تمور        	| تَمر   	| NOUN.MP   	| dates (fruit)  	| GLF,EGY                      	|
| تمرة        	| تَمرَة  	| NOUN.FS   	| date (fruit)   	| GLF,EGY                      	|
| تمرات       	| تَمرَة  	| NOUN.FP   	| dates (fruit)  	| GLF,EGY                      	|
| ناس         	| نَاس   	| NOUN.MP   	| people, humans 	| GLF,EGY , collective plurals 	|

</details>

<details>
<summary markdown="block"> 
### Gloss
</summary>

The English gloss refers to the semantic translation of the Arabic lemma.
- For nominals the gloss is the singular form of the word.
- For verbs the gloss infinitive form.

| Lemma 	| Arabic Word 	| POS.      	| English Gloss 	| Comments/Examples/Diaclect 	|
|-------	|-------------	|-----------	|---------------	|----------------------------	|
| كِتاب  	| كتب         	| NOUN.MP   	| book          	| GLF,EGY                    	|
| كَتَب   	| كتبوا       	| VERB.P3MP 	| write         	|                            	|

</details>


[^1]: Refer to the [phonology guidelines]({% link phonology.md %}) for the complete CAPHI reference.
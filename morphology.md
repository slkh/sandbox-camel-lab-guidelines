---
layout: guidelines
title: CAMeL Guidelines | Morphology
camelpos: CAMEL POS
moreExamples: Annotation examples
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

### Morphologican Annotation

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

### Clitics
Clitics are syntactically independent morphems that are orthographically attached to the baseword. They can be in a number of parts of speech.

**Notes**:

- Clitics may interact with the spelling of the baseword. See the notes above on Tokenization and the [CODA general rules]({% link orthography.md %}).
- Although writers -in dialectal Arabic mostly- tend to attach what is considered as a direct object clitic with the baseword (verbs, adjectives that are active participles), in the CODA convention they should be separate. For example <span dir="rtl">اجيبلك</span> should be <span dir="rtl">اجيب لك</span>, and <span dir="rtl">جايبلها</span> should be <span dir="rtl">جايب لها</span>. For the list of clitics, please refer to the CODA seed lexicon page: https://sites.google.com/a/nyu.edu/coda/dialect-specific <!--TODO: link to the new location of the seed lexicon-->
</details>

<details>
<summary markdown="block">
### Features
</summary>
Features refer to specific morphosyntactic aspects of the word that are abstracted away in the lemma form. For example, the word <span dir="rtl">أميرات</span> 'princesses' has the lemma <span dir="rtl">أمير</span> 'prince' with the features gender: feminine and number: plural.

**Notes**

-  Features may not necessarily match the form of the word: e.g. <span dir="rtl">حامل</span> 'pregnant' is gender: feminine even though it has no 'Ta marbuta'[^2] ending; and <span dir="rtl">خليفة</span>  'Khalifa (name); caliph' is gender: masculine and number: singular even though it ends with 'Ta marbuta'.
- Some words have plurality to their meaning, but morphosyntactically are singular (collectable plurals). For example, <span dir="rtl">شجر</span> 'trees' is singular because we say <span dir="rtl">شجر طويل</span> 'tall trees' similar to <span dir="rtl">رجل طويل</span> 'a tall man'.
- The assignment of the features are in context (sentence and document) and depends on the morpho-syntactic agreement at all times.
- For specific examples and cases, refer to the notes section of the different parts-of-speech.
- Features include gender, number, person, and aspect. Each feature has a number of possible values.
- Features are represented in combinations in our system. The examples in the section are some feature-value pairs.

| Features 	| الخصائص  	| POS 	| قسم الكلام 	| Description/الوصف                                                               	|
|----------	|----------	|-----	|------------	|---------------------------------------------------------------------------------	|
| .P3MS    	| ماضي.هو  	| فعل 	| VERB       	| Aspect:(P);Person:(3);Gender:(M);Number:(S) الزمن:ماضي؛الضمير:مفرد مذكر غائب    	|
| .P1P     	| ماضي.أنا 	| فعل 	| VERB       	| Aspect:(P);Person:(1);Gender:unspecified;Number:(S) الزمن:ماضي؛الضمير:جمع متكلم 	|
| .MS      	| هو       	| اسم 	| NOUN       	| Gender:(M);Number:(S) الجنس:مذكر؛العدد:مفرد                                     	|


</details>

### CAMEL POS tagset

<details>
<summary markdown="block">
### NOUN - <span dir="rtl">اسم</span>
</summary>

**Common Nouns**
: Common nouns refer to entities and concepts that have a more general reference than proper nouns. Common nouns inflect for prefixes and suffixes of person, gender, number.

- Some nouns, such as prepositional nouns (<span dir="rtl">عند، بين، أمام</span> ... etc) don't necessarily have clear features.
To assign features for those cases, use a syntactic test for a nonsensical semantic context[^3]. For example, the word <span dir="rtl">أمام</span> can be in a nonsensical construction where you might say <span dir="rtl">الأمام الأول والأمام الثاني للبيت</span>. According to the morphosyntactic agreement this makes the features for <span dir="rtl">أمام</span> to be gender: M and number:S
- For gender ambiguous cases, such as <span dir="rtl">طريق</span>, where <span dir="rtl">طريق</span> could be both masculine and feminine depending on the usage (<span dir="rtl">طريق طويل</span> and <span dir="rtl">طريق طويلة</span>). To assign the gender feature, resolve using the context if such is impossible assign it the form based gender.
- Common nouns include derived such as <span dir="rtl">دباديب</span> and non-derived nouns such as <span dir="rtl">ام</span>.
- Titles are also annotated as common nouns.
- Common nouns also include a set of borrowed nouns.
- In the context of dialectal text annotation, only nouns that appear to have a case ending such as <span dir="rtl">غصبٍ</span> will have state and case feature annotated. The 'case' feature in this situation is not the real case but rather a remnant from the MSA.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| Tag     	| العلامة 	| Arabic Word 	| English Gloss       	| Dialect 	|
|---------	|---------	|-------------	|---------------------	|---------	|
| NOUN.FP 	| اسم.هن  	| حرمات       	| women               	| GLF     	|
| NOUN.FP 	| اسم.هن  	| حريم        	| women               	| GLF     	|
| NOUN.FP 	| اسم.هن  	| نسوان       	| women               	| GLF     	|
| NOUN.FS 	| اسم.هي  	| خالوه       	| aunt! (maternal)    	| GLF     	|
| NOUN.FS 	| اسم.هي  	| عموه        	| aunt! (paternal)    	| GLF     	|
| NOUN.FS 	| اسم.هي  	| حجرة        	| room                	| GLF     	|
| NOUN.FS 	| اسم.هي  	| ميز         	| table               	| GLF     	|
| NOUN.FS 	| اسم.هي  	| بكرة        	| tomorrow            	| GLF     	|
| NOUN.FS 	| اسم.هي  	| شيشة        	| waterpipe           	| GLF     	|
| NOUN.FS 	| اسم.هي  	| حرمة        	| woman               	| GLF     	|
| NOUN.FS 	| اسم.هي  	| مرة         	| woman               	| GLF     	|
| NOUN.MP 	| اسم.هم  	| بزران       	| child               	| GLF     	|
| NOUN.MP 	| اسم.هم  	| عيال        	| child               	| GLF     	|
| NOUN.MP 	| اسم.هم  	| رجّال        	| men                 	| GLF     	|
| NOUN.MP 	| اسم.هم  	| رجاجيل      	| men                 	| GLF     	|
| NOUN.MS 	| اسم.هو  	| حق          	| for the benefit of  	| GLF     	|
| NOUN.MS 	| اسم.هو  	| خلاص        	| enough              	| GLF     	|
| NOUN.MS 	| اسم.هو  	| سكين        	| knife               	| GLF     	|
| NOUN.MS 	| اسم.هو  	| مكتوب       	| letter              	| GLF     	|
| NOUN.MS 	| اسم.هو  	| مثل         	| like                	| GLF     	|
| NOUN.MS 	| اسم.هو  	| حلق         	| mouth               	| GLF     	|
| NOUN.MS 	| اسم.هو  	| خشم         	| nose                	| GLF     	|
| NOUN.MS 	| اسم.هو  	| مال         	| of                  	| GLF     	|
| NOUN.MS 	| اسم.هو  	| حقّ          	| of, belongs to      	| GLF     	|
| NOUN.MS 	| اسم.هو  	| برع         	| outside, outside of 	| GLF     	|
| NOUN.MS 	| اسم.هو  	| حد          	| somebody, someone   	| GLF     	|
| NOUN.MS 	| اسم.هو  	| باكر        	| tomorrow            	| GLF     	|
| NOUN.MS 	| اسم.هو  	| امس         	| yesterday           	| GLF     	|
| NOUN.MS 	| اسم.هو  	| كذي         	| like this, as this  	| GLF     	|

</details>
</details>

<details>
<summary markdown="block">
### NOUN_PROP - <span dir="rtl">اسم_علم</span>
</summary>

**Proper Nouns**
: Proper nouns are nouns that have a unique referential meaning in context that is mutually exclusive with other entities.

- Proper nouns refer to names of people, geographical entities, months and acronyms.
- Proper nouns with more than one part such as <span dir="rtl">محمد علي</span> should have both words annotated as proper nouns.
- Names such as <span dir="rtl">عبد الله</span> and <span dir="rtl">علاء الدين</span> should be split, both words annotated as proper nouns.
- Titles of newspapers, magazines, and news agencies, sports teams are annotated as proper nouns, as well as names of political parties, etc.
- Proper nouns might exhibit a different kind of ambiguity where the word as a NOUN have features that fails the morpho-syntactic agreement when used as a proper noun. For example the proper noun <span dir="rtl">احلام</span> as a female given name behaves as a FS hence will be given NOUN_PROP.FS as a tag. The same applies to other proper nouns such as the newspaper name <span dir="rtl">الاهرام</span>, see examples below.
- : Proper nouns can be confused with common nouns. A case in point is the word <span dir="rtl">جَنُوب إِفرِيقيا</span>, the two parts of the word are considered as proper nouns when it refers to the country, South Africa.
- The lemma of a proper noun does not include Al but it includes the 'Ta Marbuta'. The proper noun <span dir="rtl">القاهرة</span> has the lemma <span dir="rtl">قاهرة</span>.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص               	| Arabic Example 	| English Gloss                  	|    Comments/Examples/Diaclect                 	|
|--------------	|----------------------------------	|---------------	|----------------------------	|---------------------------------------------------	|
| NOUN_PROP.MS 	| اسم علم.هو                       	| خليفة         	| Khalifa                    	| GLF,EGY , name of person                          	|
| NOUN_PROP.MS 	| اسم علم.هو                       	| عبد الله      	| Abdullah                   	| GLF,EGY , both words get the same POS tag         	|
| NOUN_PROP.FS 	| اسم علم.هي                       	| امريكا        	| America                    	| GLF,EGY , geographical entity                     	|
| NOUN_PROP.FS 	| اسم علم.هي                       	| هند           	| Hind                       	| GLF,EGY                                           	|
| NOUN_PROP.MS 	| اسم علم.هو                       	| ناتو          	| NATO                       	| GLF,EGY , acronym                                 	|
| NOUN_PROP.MS 	| اسم علم.هو                       	| امشير         	| Meshir                     	| GLF,EGY , امشير شهر الرياح والزعابيب ;month       	|
| NOUN_PROP.FS 	| اسم علم.هي                       	| الاهرام       	| Al Ahram                   	| GLF,EGY , نشرت الاهرام التقرير النهائي ;newspaper 	|
| NOUN_PROP.MS 	| اسم علم.هو                       	| الاهرام       	| Al Ahram                   	| GLF,EGY , تلقى الاهرام اتصالا هاتفيا ;newspaper   	|
| NOUN_PROP.FS 	| اسم علم.هي                       	| الاخوان       	| The Muslim Brotherhood     	| GLF,EGY , تلقت الإخوان تمويلاً ;newspaper          	|

</details>
</details>

<details>
<summary markdown="block">
### NOUN_QUANT - <span dir="rtl">اسم_كم</span>
</summary>

Noun quantifiers
: Noun quantifiers express either quantity or approximation.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features  	| قسم الكلام.الخصائص 	| Arabic Example 	| English Gloss 	| Comments/Examples/Diaclect 	|
|---------------	|--------------------	|----------------	|---------------	|----------------------------	|
| NOUN_QUANT.MS 	| اسم كم.هو          	| نص             	| half          	| GLF,EGY , نص ساعة          	|

</details>
</details>

<details>
<summary markdown="block">
### NOUN_NUM - <span dir="rtl">اسم_عدد</span>
</summary>

**Cardinal numbers**
: Cardinal numbers quantify rather than rank. They answer the question “How many?”

- Compound numerals (from 21 to infinite) that are coordinated with the conjunction wa- follow the POS tag of the first element. If the first element is a cardinal number, the second element should be annotated as such.
- Cardinal numbers can occur in pre-nominal and post-nominal positions without any agreement with the noun they occur with. They are invariable.
<!--TODO discuss the MSA inverse agreement-->

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص 	| Arabic Example 	| English Gloss      	| Comments/Examples/Diaclect 	|
|--------------	|--------------------	|----------------	|--------------------	|----------------------------	|
| NOUN_NUM.MS  	| اسم عدد.هو         	| صفر            	| 0, zero            	| GLF                        	|
| NOUN_NUM.MS  	| اسم عدد.هو         	| واحد           	| 1, one             	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| عشر            	| 10, ten            	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| عشرة           	| 10, ten            	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| امية           	| 100, one hundred   	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| مية            	| 100, one hundred   	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| الف            	| 1000, one thousand 	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| آلاف           	| 1000, thousands    	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| احدعش          	| 11, eleven         	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| اثنعش          	| 12, twelve         	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثلتعش          	| 13, thirteen       	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| اربعتعش        	| 14, fourteen       	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| خمستعش         	| 15, fifteen        	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ستعش           	| 16, sixteen        	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| سبعتعش         	| 17, seventeen      	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثمنتعش         	| 18, eighteen       	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| تسعتعش         	| 19, nineteen       	| GLF                        	|
| NOUN_NUM.MD  	| اسم عدد.هما♂       	| اثنين          	| 2, two             	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| عشرين          	| 20, twenty         	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ميتين          	| 200, two hundred   	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثلاث           	| 3, three           	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ثلاثة          	| 3, three           	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثلاثين         	| 30, thirty         	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ثلاثمية        	| 300, three hundred 	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| اربع           	| 4, four            	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| اربعة          	| 4, four            	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| اربعين         	| 40, fourty         	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| اربعمية        	| 400, four hundred  	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| خمس            	| 5, five            	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| خمسة           	| 5, five            	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| خمسين          	| 50, fifty          	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| خمسمية         	| 500, five hundred  	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ست             	| 6, six             	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ستة            	| 6, six             	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ستين           	| 60, sixty          	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ستمية          	| 600, six hundred   	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| سبع            	| 7, seven           	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| سبعة           	| 7, seven           	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| سبعين          	| 70, seventy        	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| سبعمية         	| 700, seven hundred 	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثمان           	| 8, eight           	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ثمانية         	| 8, eight           	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| ثمانين         	| 80, eighty         	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| ثمانمية        	| 800, eight hundred 	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| تسع            	| 9, nine            	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| تسعة           	| 9, nine            	| GLF                        	|
| NOUN_NUM.MP  	| اسم عدد.هم         	| تسعين          	| 90, ninety         	| GLF                        	|
| NOUN_NUM.FP  	| اسم عدد.هن         	| تسعمية         	| 900, nine hundred  	| GLF                        	|

</details>
</details>

<details>
<summary markdown="block">
### PRON - <span dir="rtl">ضمير</span>
</summary>

**Bound pronouns** - <span dir="rtl">**الضمائر المتصلة**</span>
: Bound pronouns are morphemes that cannot occur independently of another morpheme. They are related to other words called their hosts.

These pronouns bind to verbs to mark direct object, to nouns to mark possession, and to prepositions.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص                	| Arabic Example                	| English Gloss     	| Comments/Examples/Diaclect 	|
|:--------------	|-----------------------------------:	|-------------------------------:	|:-------------------	|:----------------------------	|
| PRON.1P      	| <span dir="rtl">ضمير.نحن</span>     	| <span dir="rtl">+نا</span>      	| our, us           	| GLF                        	|
| PRON.1S      	| <span dir="rtl">ضمير.انا</span>     	| <span dir="rtl">+ني</span>      	| me                	| GLF                        	|
| PRON.1S      	| <span dir="rtl">ضمير.انا</span>     	| <span dir="rtl">+ي</span>      	| me, my            	| GLF                        	|
| PRON.2FP     	| <span dir="rtl">ضمير.انتن</span>    	| <span dir="rtl">+كن</span>      	| you, your         	| GLF                        	|
| PRON.2FS     	| <span dir="rtl">ضمير.انت♀</span>    	| <span dir="rtl">+ج</span>      	| you, your         	| GLF                        	|
| PRON.2FS     	| <span dir="rtl">ضمير.انت♀</span>    	| <span dir="rtl">+ك</span>      	| you, your         	| GLF                        	|
| PRON.2MP     	| <span dir="rtl">ضمير.انتم</span>    	| <span dir="rtl">+كم</span>      	| you, your         	| GLF                        	|
| PRON.2MS     	| <span dir="rtl">ضمير.انت♂</span>    	| <span dir="rtl">+ك</span>      	| you, your         	| GLF                        	|
| PRON.3FP     	| <span dir="rtl">ضمير.هن</span>      	| <span dir="rtl">+هن</span>      	| their, them       	| GLF                        	|
| PRON.3FS     	| <span dir="rtl">ضمير.هي</span>      	| <span dir="rtl">+ها</span>      	| her, it, its      	| GLF                        	|
| PRON.3MP     	| <span dir="rtl">ضمير.هم♂</span>     	| <span dir="rtl">+هم</span>      	| their, them       	| GLF                        	|
| PRON.3MS     	| <span dir="rtl">ضمير.هو</span>      	| <span dir="rtl">+ه</span>      	| him, his, it, its 	| GLF                        	|

</details>

* * *

**Unbound pronouns** - <span dir="rtl">**الضمائر المنفصلة**</span>
: Unbound pronouns are free morphemes that occur as separate words.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص                	| Arabic Example                        	| English Gloss 	| Comments/Examples/Diaclect 	|
|--------------	|-----------------------------------:	|---------------------------------------:	|---------------	|----------------------------	|
| PRON.1P      	| <span dir="rtl">ضمير.نحن</span>   	| <span dir="rtl">احن</span>            	| we            	| GLF                        	|
| PRON.1P      	| <span dir="rtl">ضمير.نحن</span>   	| <span dir="rtl">احنا</span>           	| we            	| GLF                        	|
| PRON.1P      	| <span dir="rtl">ضمير.نحن</span>   	| <span dir="rtl">حنّا</span>            	| we            	| GLF                        	|
| PRON.1P      	| <span dir="rtl">ضمير.نحن</span>   	| <span dir="rtl">نحن</span>            	| we            	| GLF                        	|
| PRON.1S      	| <span dir="rtl">ضمير.انا</span>   	| <span dir="rtl">انا</span>            	| I             	| GLF                        	|
| PRON.2FS     	| <span dir="rtl">ضمير.انت♀</span>   	| <span dir="rtl">انتي</span>           	| you           	| GLF                        	|
| PRON.2MS     	| <span dir="rtl">ضمير.انت♂</span>   	| <span dir="rtl">انت</span>            	| you           	| GLF                        	|
| PRON.2P      	| <span dir="rtl">ضمير.انتم⚥</span>   	| <span dir="rtl">انتو</span>           	| you           	| GLF                        	|
| PRON.3FS     	| <span dir="rtl">ضمير.هي</span>    	| <span dir="rtl">هي</span>             	| she is        	| GLF                        	|
| PRON.3MS     	| <span dir="rtl">ضمير.هو</span>    	| <span dir="rtl">هو</span>             	| he, it        	| GLF                        	|
| PRON.3P      	| <span dir="rtl">ضمير.هم⚥</span>   	| <span dir="rtl">هم</span>             	| they          	| GLF                        	|

</details>
</details>

<details>
<summary markdown="block">
### PRON_DEM - <span dir="rtl">ضمير_إشارة</span>

</summary>

**Demonstrative pronouns**
: Demonstrative pronouns are pronouns used for proximal or distal reference.

- Demonstrative Pronouns can be basewords and/or proclitics, some baseword pronouns take no fetures, see examples below.
- The relationship between proximity and distance which does not seem to exist in Egyptian Arabic.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص                         	| Arabic Example                	| English Gloss 	| Comments/Examples/Diaclect 	|
|--------------	|-------------------------------------------:	|-------------------------------:	|---------------	|----------------------------	|
| PRON_DEM     	| <span dir="rtl">ضمير_إشارة    </span>     	| <span dir="rtl">ا+  </span>   	|               	| EGY, أهو                   	|
| PRON_DEM.MS  	| <span dir="rtl">ضمير_إشارة.هو </span>     	| <span dir="rtl">هاذا</span>   	| this/that     	| GLF                        	|
| PRON_DEM.P   	| <span dir="rtl">ضمير_إشارة.هم⚥</span>     	| <span dir="rtl">ذول </span>   	| these/those   	| GLF                        	|

</details>
</details>

<details>
<summary markdown="block">
### PRON_INTERROG - <span dir="rtl">ضمير_استفهام</span>

</summary>

**Interrogative Pronouns**
: Interrogative Pronouns are independent words that used to form direct questions.

- Interrogative pronouns don't take features

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features  	| قسم الكلام.الخصائص                    	| Arabic Example               	| English Gloss 	| Comments/Examples/Diaclect 	|
|---------------	|--------------------------------------:	|--------------------------:	|---------------	|----------------------------	|
| PRON_INTERROG 	| <span dir="rtl">ضمير_استفهام</span>   	| <span dir="rtl">كم</span>   	| how many      	| GLF                        	|
| PRON_INTERROG 	| <span dir="rtl">ضمير_استفهام</span>   	| <span dir="rtl">كمن</span>   	| how many      	| GLF                        	|
| PRON_INTERROG 	| <span dir="rtl">ضمير_استفهام</span>   	| <span dir="rtl">شقد</span>   	| how much      	| GLF                        	|
| PRON_INTERROG 	| <span dir="rtl">ضمير_استفهام</span>   	| <span dir="rtl">ايش</span>   	| what          	| GLF                        	|
| PRON_INTERROG 	| <span dir="rtl">ضمير_استفهام</span>   	| <span dir="rtl">شو</span>   	| what          	| GLF                        	|

</details>
</details>


<details>
<summary markdown="block">
### PRON_REL - <span dir="rtl">ضمير_موصول</span>

</summary>

**Relative pronouns**
: Relative pronouns introduce relative clauses

- Relative pronouns don't take any features

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features  	| قسم الكلام.الخصائص                   	| Arabic Example                    	| English Gloss        	| Comments/Examples/Diaclect 	|
|---------------	|-------------------------------------:	|------------------------------:	|-----------------------	|----------------------------	|
| PRON_REL      	| <span dir="rtl">ضمير_موصول</span>   	| <span dir="rtl">اللي</span>   	| who, which, whom      	| GLF                        	|

</details>
</details>

<details>
<summary markdown="block">
### PRON_EXCLAM - <span dir="rtl">ضمير_تعجب</span>

</summary>

**Exclamative Pronouns**
: Exclamative Pronouns introduces exclamative structure

- Exclamative Pronouns don't take any features

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص            	| Arabic Example                	| English Gloss 	| Comments/Examples/Diaclect 	|
|--------------	|-------------------------------	|-------------------------------	|---------------	|----------------------------	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">واجد</span>    	| a lot, very   	| GLF                        	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">سيّئ</span>    	| bad           	| GLF                        	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">زين</span>    	| good          	| GLF                        	|

| POS.Features  	| قسم الكلام.الخصائص                   	| Arabic Example               	| English Gloss    	| Comments/Examples/Diaclect 	|
|---------------	|-------------------------------------:	|-----------------------------:	|------------------	|---------------------------	|
| PRON_EXCLAM      	| <span dir="rtl">ضمير_تعجب</span>   	| <span dir="rtl">ما</span>   	| what          	| GLF, الله ما أكبر غلاك       	|

</details>
</details>


<details>
<summary markdown="block">
### ADJ - <span dir="rtl">صفة</span>

</summary>

**Adjectives**
: Adjectives are nominals that describe or clarify a noun

- Adjectives must inflect for gender and number according to the agreement rule with nouns.
- The agreement rule states that adjectives must agree with the noun that they modify in gender and number. EXCEPT for plural irrational (<span dir="rtl">غير عاقل</span>) nouns, which always take feminine singular adjectives.
For example of agreement: the word <span dir="rtl">مهم</span> inflects in agreement with the noun in the case of <span dir="rtl">امرأة مهمة</span> and <span dir="rtl">نساء مهمات</span>. It also agrees in the case of <span dir="rtl">كتاب مهم</span> but not <span dir="rtl">كتب مهمة</span>. Because the word <span dir="rtl">كتاب</span> is an irrational noun, hence the plural <span dir="rtl">كتب</span> takes a singular feminine adjective.
- In the case where there is no noun in the sentence, the word will be tagged as an adjective if a specific noun can be recovered directly from the context. Otherwise, the word will be tagged as a noun.
For example, the word <span dir="rtl">عرب</span> 'Arabs' could be a noun or an adjective. <span dir="rtl">عرب</span> as in <span dir="rtl">جاء الرجال العرب</span> 'The Arab men came' is tagged as an adjective, whereas in <span dir="rtl">معجم لسان العرب</span> 'Lisan Al Arab dictionary' <span dir="rtl">عرب</span> is tagged as a noun.
- Although adjective must inflict in agreement with the noun, the features of the adjectives are annotated independently. In the example <span dir="rtl">كتب مهمة</span> the adjective <span dir="rtl">مهمة</span> is annotated with features feminine singular and NOT masculine plural.

<details><summary markdown='span'>{{ page.moreExamples }}</summary>

| POS.Features 	| قسم الكلام.الخصائص            	| Arabic Example                	| English Gloss 	| Comments/Examples/Diaclect 	|
|--------------	|-------------------------------	|-------------------------------	|---------------	|----------------------------	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">واجد</span>    	| a lot, very   	| GLF                        	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">سيّئ</span>    	| bad           	| GLF                        	|
| ADJ.MS       	| <span dir="rtl">صفة.هو</span>   	| <span dir="rtl">زين</span>    	| good          	| GLF                        	|

</details>
</details>









* * *

### Aditional Annotation Tasks

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

<details>
<summary markdown="block">
### Dialect Identification
</summary>
Dialect identification (DID) is the task of tagging a certain context with a given dialect tag.

Deciding the dialect tag depends on the context of the sentence and/or the document. As dialects may share the same words within themselves or with MSA, the dialect is inferred from the sentence structure and word order of that specific dialect.

Although all words belonging to the same sentence may get the same dialect tag, in some cases two different dialectal structure could occur in the same sentence, hence we tag per word
</details>


[^1]: Refer to the [phonology guidelines]({% link phonology.md %}) for the complete CAPHI reference.
[^2]: 'Ta Marbuta' suffix is usually used to mark the feminine gender.
[^3]: https://en.wikipedia.org/wiki/Colorless_green_ideas_sleep_furiously
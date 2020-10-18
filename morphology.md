---
layout: guidelines
title: CAMeL Guidelines | Morphology
---
CAMEL POS Schema and Guidelines
===


## Motivation and Goals:
CAMEL POS is inspired by the ARZATB tagset and guidelines (Maamouri et al., 2012) 
which is  based on the PATB guidelines (Maamouri et al., 2009). The CAMEL POS 
is designed as single tagset for both MSA and the dialects with the following goals in 
mind: 

-  Facilitating research on adaptation between MSA and the dialects, 
and among the dialects.
-  Supporting backward compatibility with previously annotated resources.
-  Enforcing a functional morphology analysis that is deeper and more compatible
with Arabic morphosyntactic rules than form based 
analysis (Alkuhlani and Habash, 2011).

## Overview
The CAMEL POS tags and features are the union of those in MSA and the dialects. 
Features are available to use when needed. 
For example case and state features are used more often in MSA; but on 
the other hand, dialects tend to have many more clitics than MSA, including 
non-MSA ones. 

One main property of CAMEL POS tagset that sets it apart from ARZATB is that 
the morphological features of both gender and number of nominals are annotated 
functionally (i.e. semantically) (Alkuhlani and Habash, 2011; Smrž, 2007). 
This decision allows us to assign the features to the baseword without the need to 
specify the surface form affixes that mark form gender and number. 
This is not the case in ARZATB, where broken (irregular) plural nouns are tagged 
as singular because they do not use the sound plural affixes. 

Another property is that in CAMEL POS tagest we omit case and state 
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
(2 tags) and baseword (39 tags). Together with the features, CAMEL POS tagset
maps to ARZATB and retains backward compatibility. It also offers an intuitive 
Arabic scheme that is suitable to use for annotation.
{% include pos_table.html %}

### Features
CAMEL POS provides full array of features: 

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


[^1]: Refer to the [phonology guidelines]({% link phonology.md %}) for the complete CAPHI reference.
---
layout: guidelines
title: CAMeL Guidelines | Orthography

---
CODA*: Conventional Orthography for Dialectal Arabic
===

### CODA* Mission
* Dialectal Arabic (DA) refers to the day-to-day vernaculars spoken in the Arab world. DA lives side-by-side with the official language, Modern Standard Arabic (MSA). DA differs from MSA on all levels of linguistic representation, from phonology and morphology to lexicon and syntax. Unlike MSA, DA has no standard orthography since there are no Arabic dialect academies, nor is there a large edited body of dialectal literature that follows the same spelling standard.
* CODA* (pronounced CODA Star, as in, for any dialect) is a conventional orthography for dialectal Arabic. It is designed primarily for the purpose of developing computational models of Arabic dialects.

### CODA* Goals & Intentions
1. CODA* is an internally consistent and coherent convention for writing DA.
2. CODA* is created for computational purposes.
3. CODA* uses the Arabic script.
4. CODA* is a unified framework for writing all DAs.
5. CODA* aims to strike an optimal balance by maintaining a level of dialectal uniqueness yet establish conventions based on MSA-DA similarities.
6. CODA* strives to be easily learnable and readable.

### CODA Design Principles
1. CODA* is an ad hoc convention. There are numerous decisions that could have been made differently especially when it comes to the phonology/orthography interface. These principles make CODA* comparable to English spelling (a bit phonological, a bit historical, with some exceptions). In some cases, we followed decisions that have been made by previously published efforts.
2. CODA* uses only the inventory of Arabic script characters including the diacritics used for writing MSA. CODA* does not use extended Arabic characters, e.g. from Persian or Urdu. CODA* can be written undiacritized or diacritized.
3. Each DA word has a unique orthographic form in CODA that represents its phonology, morphology, and lexical semantics [meaning].
4. As a general rule, CODA* uses MSA-like orthographic decisions (rules, exceptions and ad hoc choices), e.g., cliticizing single letter particles, using Shadda for phonological gemination, using Ta-Marbuta, Alif Maqsura, silent Alif in Waw-Alif of plurality, and spelling the definite article Al morphemically. 
5. CODA* generally preserves the phonological form of dialectal words given the unique phonological rules of each dialect (e.g., vowel shortening), and the limitations of Arabic script (e.g., using a diacritic and a glide consonant to write a long vowel). Two important ad hoc exceptions pertain to specific root radical letters that happen to be highly variant across dialects, e.g. ق، ث، ذ، ظ، ج , etc. and to long pattern vowels that can be shortened deterministically in the dialects, e.g., the pattern 1awA2iy3 فواعيل. For these cases, the word is written using the MSA cognate root radicals or pattern.
6. CODA* preserves dialectal morphology (e.g., dialectal clitics حتقول instead of ستقول). The only exception here is separating the negation and indirect object pronouns although they are part of the word: e.g. (Cairo): ما قلت لهاش /m a # 2 u l t # i l h aa sh/ ‘I did not tell her’.
7. CODA* preserves dialectal syntax, i.e. there is no change in word order.
8. CODA* aims to be easy to learn and write, encouraging high inter-annotator agreement; the more CODA* looks like what a dialect speaker may write, the better.
9. CODA* rules are dialect independent.  (note that dialect-specific exception lists from previous CODA versions have been redesigned and unified into dialect independent sets of specific rules).
10. CODA* specific rules override general rules and apply to certain pre-defined classes of words – roughly corresponding to closed class or highly marking frequent words. The aim is to preserve important morphological information, maintain dialect integrity, and ensure overall readability.

### CODA* Rules

#### Introduction

CODA* (pronounced CODA Star, as in, for any dialect) is a conventional orthography for dialectal Arabic. It is designed primarily for the purpose of developing computational models of Arabic dialects. See CODA* Main Page for a description of CODA* mission statement and design guidelines.

Some sections of these guidelines are continously researched and updated as more dialectal data is incorporated.

(CODA* version: 0.43)



#### Basic Terminology

##### Sounds - Letters - Diacritics

The term sounds is used in the context of pronunciation (phonology), while letters and diacritics are used in the context of writing (orthography). Sounds can be consonants or vowels, and they are represented using the CAPHI representation (see Phonology Reference) and are bounded by forward slashes when necessary. Letters and diacritics are symbols used in the Arabic script to write words. Letters in the Arabic language are always required to be written; while diacritics are optional.

The space for consonants and vowels is shared by letters and diacritics, neither of which is exclusive to either category of symbols. To understand this shared space, keep in mind the following:

***

Letters can be used to write:
 * Consonants - /b/, written "ب"; /y/, written "ي", i.e: /b aa b/, باب, 'door'; or /y i k t u b/, يكتب, 'he writes'
 * Vowels - /i/, written "ي", i.e: /k i t aa b i/, كتابي, 'my book'

***

Diacritics can be used to specify:
* No vowel - “ ْ ” (Sukuun), i.e: /k a l b/, كلْب, 'dog'
* Double consonants - “ ّ ”ّ, (Shadda), i.e: /k a s s a r/, كسّر, 'he broke'
* Vowels - “ َ ” (Fatha), i.e: /k a t a b/, كَتَب, 'he wrote'
* Vowels+consonants - “ ً ”, /a n/, (Nunation), i.e: /f i 3 l a n/, فعلاً, 'verily'

#### Basic Terminology

##### Patterns - Other Morphemes

Arabic’s templatic morphology makes common reference to the concept of the root, a typically tri-consonantal abstraction capturing a general meaning about the word. For example, the root ك.ت.ب 'writing-related' appears in words like مكتب 'office' and كتاب 'book'. Each sound in the root is referred to as a radical. The general complement of the root is the pattern, which in the examples above are ma12a3 and 1i2A3 (here, 1, 2, 3 are slots for the root radicals). In addition to the root and pattern templatic morphemes, Arabic uses numerous other concatenative morphemes.

#### Basic Terminology

##### Words - Base Words - Clitics


We define an Arabic base word to consist of a stem and the minimal number of concatenative affixes needed to specify the obligatory features for its part of speech (POS). A stem can be non-templatic or it can be composed from the interdigitation of a root and a pattern. The pattern may specify the features fully, as in broken plurals. Base words are as such the smallest fully formed words. Examples include: كتابين 'two books' and يكتبون 'they write'. Clitics are syntactically independent but phonologically dependent morphemes that are attached to the word phonologically. Words can be base words or base words with added clitics. We use the term word to refer to the phonological utterance or the orthographic string, and we specify as needed. In CODA, phonological words typically map one-to-one to orthographic words; but there are many exceptions, pertaining mostly to clitics that are spelled as separate orthographic words.


![words basewords clitics](assets/images/orthography/words_basewords_clitics_1.png)

***

![words basewords clitics](assets/images/orthography/words_basewords_clitics_2.png)



#### General

##### Basic Phonology to Orthography Mapping

###### Hamza Rules


Hamza (Glottal Stop) spelling follows from the same rules as those of MSA and is unchanged from previous CODA versions. 

(For a detailed explanation of Hamza spelling rules in MSA, you can refer to chapter 7 of the [QALB annotation guidelines](http://nlp.qatar.cmu.edu/qalb/QALB-guidelines_0.90.pdf))

***

Note on **base word initial Hamza**: In previous versions of CODA, and in MSA spelling, base word initial Hamza have complex spelling rules. The rule is now simplified to normalize and not spell base word initial Hamzas, though the option remains to considers the Hamzation (أ, إ) at the beginning of a word as optional

***

Note on **word initial Madda**: any word that starts with a long vowel of the quality /2 aa/ is spelled with a Madda آ

***

Note on **DA divergence from MSA cognates**: Hamza spelling matches the sound. In other words, dialectal words that have MSA cognates containing Hamza but do not contain an /2/ in their phonology are spelled without the Hamza.

| CODA      | CAPHI                | Gloss                    | MSA Cognate     | Examples; Comments                                                                                       | e.g Dialect | 
|-----------|----------------------|--------------------------|-----------------|----------------------------------------------------------------------------------------------------------|-------------| 
| الف       | 2_a_l_f              | thousand                 | ألف             | Base word initial Hamza is normalized (not written)                                                      | Sanaa       | 
| مألوف     | m_a_2_l_uu_f         | familiar                 | مألوف           |                                                                                                          | Sanaa       | 
| لا مؤاخذة | l_a_#_m_u_2_a_kh_z_a | excuse me                | لا مؤاخذة       |                                                                                                          | Cairo       | 
| فئة       | f_i_2_e              | denomination             | فئة             |                                                                                                          | Sanaa       | 
| يأنتر     | y_i_2_a_n_t_i_r      | he is using the internet | يستعمل الإنترنت |                                                                                                          | Sanaa       | 
| بريء      | b_a_r_ii_2           | innocent                 | بريء            |                                                                                                          | Sanaa       | 
| بير       | b_ii_r               | well                     | بئر             | Spelling follows dialect phonology: Hamza is dropped                                                     | Sanaa       | 
| سما       | s_a_m_e              | sky                      | سماء            | Hamza is dropped from dialect, but final vowel spelling maintains the Alif taking etymology into account | Sanaa       | 
| ما        | m_aa                 | water                    | ماء             | Hamza is dropped from, but final vowel spelling maintains the Alif taking etymology into account         | ِAlgiers    | 
| آسف       | 2_aa_s_i_f           | sorry                    | آسف             | Madda rule                                                                                               | Sanaa       | 
| تأمين     | t_e_2_m_ii_n         | insurance                | تأمين           |                                                                                                          | Beirut      | 


#### General

##### Basic Phonology to Orthography Mapping

###### Diacritics


While Arabic diacritics are optional in general, they can be crucial for disambiguation in certain contexts. Arabic diacritics are primarily used for representing short vowels, or absence of vowels. However, the Shadda diacritic is used to represent consonantal gemination, e.g. كَتَّب /k a t t a b/ ‘he dictated’. As such, the Shadda interacts with the number of letters in a word. The Shadda general rule states that it is used within the base word (including suffixes and prefixes), but not across word-clitic boundaries. Any exceptions must be specified in the specific rules (see specific rule: "The Definite Article" for an example of where the general Shadda rule is overriden.

| CODA      | CAPHI                  | Gloss                  | Tokenized CODA | NON-CODA examples; Comments                                                                                  | 
|-----------|------------------------|------------------------|----------------|--------------------------------------------------------------------------------------------------------------| 
| جنَّنَاهم | g_a_n_n_a_n_n_aa_h_u_m | we made them crazy     | جنننا+هم       | Note that this نا  is an obligatory suffix referring to the verbal feature [1p] and is part of the base word | 
| جنَّنَنا  | g_a_n_n_a_n_n_a        | he/it mad us crazy     | جنَن+نا        |                                                                                                              | 
| يبارككم   | b_aa_r_i_k_k_u_m       | [he] congratulates you | يبارك+كم       |                                                                                                              | 
| واحشيننا  | w_aa_7_sh_i_n_n_a      | we miss you            | واحشين+نا      |                                                                                                              | 


#### General

##### Basic Phonology to Orthography Mapping

###### Long/Short Vowel Spelling

In many dialects, base word long vowels may be shortened in certain contexts. Generally, the rule is to prefer the long letter-based spelling over the shortened diacritic spelling.

| CODA     | CAPHI          | Gloss         | MSA Cognate | Examples; Comments                                                                                  | e.g Dialect | 
|----------|----------------|---------------|-------------|-----------------------------------------------------------------------------------------------------|-------------| 
| قانون    | 2_a_n_uu_n     | law           | قانون       | So long as the vowel is the same quality as the MSA, we can keep the MSA spelling                   | Cairo       | 
| قولوا له | 2_u_l_uu_#_l_u | tell him [2p] | قولوا له    | this is because قول is not always short in Cairene and can be pronounced long in different contexts | Cairo       | 

#### General

##### Basic Phonology to Orthography Mapping

###### Root Radical Spelling

Dialectal word root radicals which have MSA cognates will be spelled using the MSA cognate radical if the dialectal radical sound and the MSA radical sounds are paired according to a specific set of common sound changes.

Our list of allowed pairings is presented in the table below:

| CODA | Dialectal Sound Variant(s) | MSA Sound | 
|------|----------------------------|-----------| 
| ت    | t., d, d.                  | t         | 
| ث    | t, t., s                   | th        | 
| ج    | j, tsh, gy, y              | dj, g     | 
| د    | t., d.                     | d         | 
| ذ    | d, dh., z                  | dh        | 
| ر    | gh                         | r         | 
| ز    | s, s.                      | z         | 
| س    | s., z                      | s         | 
| ش    | tsh                        | sh        | 
| ص    | s, z                       | s.        | 
| ض    | d, dh., z.                 | d.        | 
| ط    | t                          | t.        | 
| ظ    | d., z.                     | dh.       | 
| ق    | j, dz, dj, k, g, qh, 2     | q         | 
| ك    | ts, tsh, g                 | k         | 
| ن    | m                          | n         | 


***
<!--     
<details><summary>
  more examples
  </summary> -->



  | CODA   | CAPHI            | Gloss           | CODA Letter | Dialectal Sound | MSA Sound | NON-CODA examples;  Comments                                                                                                                                                                                       | e.g Dialect  | 
  |--------|------------------|-----------------|-------------|-----------------|-----------  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------  -----------------------------------------|--------------| 
  | برتقان | b_u_r_t_u_2_aa_n | orange          | ق           | 2               | q         | برتئان، برتقال; only the sound-letter pairs that are in the list of  permitted changes are changed                                                                                                                | Jeddah       | 
  | ثامن   | t_aa_m_i_n       | eighth          | ث           | t               | th        |  تامن                                                                                                                                                                                                              | Jeddah       | 
  | فستان  | f_u_s_t._aa_n    | dress           | ت           | t.              | t         | فسطان،  فصطان                                                                                                                                                                                                      | Amman        | 
  | ذيل    | d_ee_l           | tail            | ذ           | d               | dh        |  ديل                                                                                                                                                                                                               | Beirut       | 
  | ضحك    | d_i_7_i_k        | he laughed      | ض           | d               | d.        |  دحك                                                                                                                                                                                                               | Cairo        | 
  | ضفدعة  | d._u_f_d._a_3_a  | frog            | د           | d.              | d         |  ضفضعة                                                                                                                                                                                                             | Cairo        | 
  | ظهرية  | d._u_h_r_i_y_y_a | shaddow         | ظ           | d.              | dh.       |  ضهرية                                                                                                                                                                                                             | Jeddah       | 
  | ذوق    | dh._oo_g         | tasting         | ذ           | dh.             | dh        |  ظوق                                                                                                                                                                                                               | Baghdad      | 
  | ضغط    | dh._a_gh_a_t.    | he pressed      | ض           | dh.             | d.        |  ظغط                                                                                                                                                                                                               | Jerusalem    | 
  | ثورة   | s_a_w_r_a        | revolution      | ث           | s               | th        |  سورة                                                                                                                                                                                                              | Cairo        | 
  | الزعيم | 2_a_s_s_e_3_ii_m | the boss        | ز           | s               | z         |  السعيم                                                                                                                                                                                                            | Sana’a       | 
  | صايغ   | s_aa_y_e_gh      | jeweler         | ص           | s               | s.        |  سايغ                                                                                                                                                                                                              | Cairo        | 
  | سلطة   | s._a_l._a_t._a   | salad           | س           | s.              | s         |  صلطة                                                                                                                                                                                                              | Khartoum     | 
  | ذبيحة  | z_a_b_ii_7_a     | meat            | ذ           | z               | dh        |  زبيحة                                                                                                                                                                                                             | Muscat       | 
  | اسبوع  | 2_i_z_b_uu_3     | week            | س           | z               | s         |  ازبوع                                                                                                                                                                                                             | Khartoum     | 
  | صغير   | z_gh_ii_r        | small           | ص           | z               | s.        |  زغير                                                                                                                                                                                                              | Beirut       | 
  | مضبوط  | m_a_z._b_uu_t.   | correct         | ض           | z.              | d.        |  مزبوط                                                                                                                                                                                                             | Jeddah       | 
  | عظيم   | 3_a_z._ii_m      | great           | ظ           | z.              | dh.       |  عزيم                                                                                                                                                                                                              | Damascus     | 
  | طريق   | t._a_r_ii_j      | road            | ق           | j               | q         |  طريج                                                                                                                                                                                                              | Baghdad      | 
  | سمك    | s_i_m_a_ts       | fish            | ك           | ts              | k         |  سمتس                                                                                                                                                                                                              | Riyadh(B)    | 
  | كتابج  | k_i_t_aa_b_i_ts  | your [2fs] book | ج           | ts              | dj, g     | كتابتس، كتابك; Remember that root radicals only apply to the root of the  base word, and that clitics such as the possessive pronoun ج+ may have their own rules (see specification tables)                       | Riyadh(B)    | 
  | جزاير  | dz_aa_y_i_r      | Algeria         | ج           | dz              | dj, g     |  دزاير                                                                                                                                                                                                             | Algiers      | 
  | طريق   | t._a_r_ii_dz     | road            | ق           | dz              | q         |  طريدز                                                                                                                                                                                                             | Baghdad      | 
  | عيونج  | 3_y_uu_n_i_tsh   | your eyes [2fs] | ج           | tsh             | dj, g     | عيونش، عيونتس; Remember that root radicals only apply to the root of the  base word, and that clitics such as the possessive pronoun ج+ may have their own rules (see specification tables)                       | Doha         | 
  | شاف    | tsh_aa_f         | he saw          | ش           | tsh             | sh        |  تشاف                                                                                                                                                                                                              | Doha         | 
  | سمك    | s_i_m_a_tsh      | fish            | ك           | tsh             | k         | سمج،  سمتش                                                                                                                                                                                                         | Riyadh(B)    | 
  | طريق   | t._i_r_ii_dj     | road            | ق           | dj              | q         |  طريج                                                                                                                                                                                                              | Baghdad      | 
  | رقم    | r_a_k_a_m        | number          | ق           | k               | q         |  ركم                                                                                                                                                                                                               | Jerusalem(R) | 
  | قال    | g_aa_l           | he said         | ق           | g               | q         | جال،  كال                                                                                                                                                                                                          | Aswan        | 
  | بنك    | b._a_n_g         | bank            | ك           | g               | k         | بنج،  بنق                                                                                                                                                                                                          | Baghdad      | 
  | رقم    | r_a_qh_a_m       | number          | ق           | qh              | q         | رغم،  رجم                                                                                                                                                                                                          | Jerusalem(R) | 
  | غسالة  | kh_a_s_s_ee_l_a  | washer          | غ           | kh              | gh        | خسالة; while there is no /kh/ to غ mapping in the root radical cognate  table, this switch is allowed in this particualr case because Tunisian use of /kh a s s ee l a/ and /gh a s s ee l a/ is in free variance | Tunis        | 
  | اريد   | 2_a_gh_ii_d      | I want          | ر           | gh              | r         |  اغيد                                                                                                                                                                                                              | Mosul        | 
  | طريق   | t._a_r_ii_2      | road            | ق           | 2               | q         |  طريء                                                                                                                                                                                                              | Baghdad      | 
  | جنب    | j_a_m_b          | besides         | ن           | m               | n         |  جمب                                                                                                                                                                                                               | Jeddah       | 
  | جلس    | y_a_l_a_s        | he sat down     | ج           | y               | dj, g     |  يلس                                                                                                                                                                                                               | Abu Dhabi    | 


  <!-- </details> -->




#### General

##### Base Word Spelling

###### Pattern Spelling


Dialectal words with patterns that are cognates of MSA patterns will retain the spelling choice of the MSA pattern if the difference in pronunciation can be expressed using diacritics (for vowel change or absence), or if the pronunciation is a shortened form of the MSA pattern vowels.

| Example in CODA | Example in CAPHI    | Gloss          | CODA Letter | Dialectal Sound | MSA Sound | NON-CODA examples; Comments | e.g Dialect | 
|-----------------|---------------------|----------------|-------------|-----------------|-----------|-----------------------------|-------------| 
| اتضرب           | 2_i_d._d._a_r_a_b   | he got hit     | ت           | d.              | t         | ادضرب، اضّرب                | Cairo       | 
| اتدشدش          | 2_i_d_d_a_sh_d_a_sh | he got smashed | ت           | d               | t         | ادّشدش                      | Cairo       | 


#### General

##### Base Word Spelling

###### Alif Maqsura

The MSA rules for spelling the Alif-Maqsura (ى), which are sometimes based on roots and sometimes on patterns, apply in CODA*.

| CODA | CAPHI      | Gloss      | NON-CODA examples; Comments | e.g Dialect | 
|------|------------|------------|-----------------------------|-------------| 
| اعطى | 2_a_3_t._a | give [3ms] | اعطا                        | Abu Dhabi   | 
| بغى  | b_gh_a     | want [3ms] | بغا                         | Rabat       | 
| حكى  | 7_a_k_e    | chat [3ms] | حكي                         | Beirut      | 


#### General

##### Base Word Spelling

###### Clitic Spelling

The general rule on phonological clitic spelling is that clitics that are mapped into single letters (with possible diacritics) will be spelled attached to the word, and will not interact with the spelling of the word. (For examples of specifc rules that override this rule, see "The Definite Article" and "Nominative Pronouns")

| CODA        | CAPHI                          | Gloss                 | Tokenized CODA | /Comments                                                                                      | e.g Dialect | 
|-------------|--------------------------------|-----------------------|----------------|------------------------------------------------------------------------------------------------|-------------| 
| ولحد ما يجي | w_l_a_7_a_d_d_#_m_a_#_y_ii_g_i | and until he/it comes | و+ل+حد ما يجي  | notice how و and ل -- single letter clitics -- attach to adjacent morphemes while ما does not. | Cairo       | 


#### Specific Rules

##### The Definite Article


The Arabic definite article is always written as a proclitic ال+ـ, regardless of how it is pronounced (keep in mind that in DA, lunar/solar letters are not always the same as in MSA). As with MSA spelling, general cliticization rules apply except when following the proclitic ل+ـ, where the article is spelled without its ا. The general Shadda rule is overridden in the specific context of ل+ ال+ـ followed by an ل-initial base word.


| CODA    | CAPHI             | Gloss             | Tokenized CODA | Examples; Comments                                                                                             | e.g Dialect | 
|---------|-------------------|-------------------|----------------|----------------------------------------------------------------------------------------------------------------|-------------| 
| القمر   | 2_i_l_2_a_m_a_r   | the moon          | ال+قمر         |                                                                                                                | Cairo       | 
| الشمس   | 2_i_sh_sh_a_m_e_s | the sun           | ال+شمس         |                                                                                                                | Jerusalem   | 
| الكتاب  | 2_i_k_k_i_t_aa_b  | the book          | ال+كتاب        | Note how Cairene sometimes treats /k/ as a solar letter                                                        | Cairo       | 
| البيت   | l_b_ee_t          | the house         | ال+بيت         |                                                                                                                | Jerusalem   | 
| البيوت  | l_e_b_y_uu_t      | the houses        | ال+بيوت        |                                                                                                                | Jerusalem   | 
| بالبيت  | b_e_l_b_ee_t      | at home           | ب+ال+بيت       |                                                                                                                | Jerusalem   | 
| بالبيوت | b_l_e_b_y_uu_t    | at the houses     | ب+ال+بيوت      |                                                                                                                | Jerusalem   | 
| للبيت   | l_a_l_b_ee_t      | for the house     | ل+ال+بيت       |                                                                                                                | Jerusalem   | 
| للبيوت  | l_a_l_e_b_y_uu_t  | for the houses    | ل+ال+بيوت      |                                                                                                                | Jerusalem   | 
| للشمس   | l_a_sh_sh_a_m_e_s | to the sun        | ل+ال+شمس       |                                                                                                                | Jerusalem   | 
| للشموس  | l_a_l_e_sh_m_uu_s | to the suns       | ل+ال+شومس      |                                                                                                                | Jerusalem   | 
| اللجنة  | 2_e_l_l_a_g_n_a   | the committee     | ال+لجنة        |                                                                                                                | Cairo       | 
| للجنة   | l_e_l_l_a_g_n_a   | for the committee | ل+ال+لجنة      | Note how it is not spelled لللجنة and the general shadda rules are overriden (see general "Diacritics" rules). | Cairo       | 


#### Specific Rules

##### The Ta-Marbuta


The Ta-Marbuta (ة) is a secondary letter of the Arabic alphabet used to represent a particular suffix morpheme that is often (but not exclusively) associated with the feminine-singular feature (Alkuhlani and Habash, 2011). This morpheme has a number of allomorphs with differing pronunciations. Most notably, it appears as a vowel at the end of nominals, and changes to a ∼ /t/ when followed by possessive pronominal enclitics. The Ta-Marbuta should be written as ة in word-final positions, regardless of its pronunciation, and following general CODA rules in non-word-final positions.

| CODA        | CAPHI                         | Gloss               | Examples; Comments | e.g Dialect | 
|-------------|-------------------------------|---------------------|--------------------|-------------| 
| حاجة        | 7_aa_g_a                      | something           |                    | Cairo       | 
| حاجتي       | 7_aa_g_t_i_                   | my thing            |                    | Cairo       | 
| حاجتها      | 7_aa_g_i_t_h_a                | her thing           |                    | Cairo       | 
| طاولة       | t._aa_w_l_e                   | table               |                    | Jerusalem   | 
| غزالة       | gh_a_z_ee_l_i                 | gazelle             |                    | Beirut      | 
| معلمة مدرسة | m_3_a_l_m_i_t_#_m_a_d_r_a_s_e | school teacher      |                    | Jerusalem   | 
| معلمة مدرسة | m_3_a_l_m_e_#_m_a_d_r_a_s_e   | she taught a school |                    | Jerusalem   | 
| معلمتهم     | m_3_a_l_m_i_t_h_u_m           | their teacher       |                    | Jerusalem   | 
| معلماهم     | m_3_a_l_m_aa_h_u_m            | she taught them     |                    | Jerusalem   | 

#### Specific Rules

##### The Plural Waw


Verbal suffixes that indicate the feature plural subject [2p] & [3p] and end with the sounds (/u/, /uu/, /o/, /oo/, and /aw/) will represent those sounds as وا+ (‘Waw of Plurality’ واو الجماعة) in word-final positions, and also when followed by other attached clitics. This rule is similar to the MSA rule, except for expanding the phonetic definition.

| CODA     | CAPHI             | Gloss            | Examples; Comments | e.g Dialect | 
|----------|-------------------|------------------|--------------------|-------------| 
| قالوا    | 2_aa_l_u          | they said        |                    | Cairo       | 
| بيقولوا  | b_i_y_2_uu_l_u    | they say         |                    | Cairo       | 
| نقولوا   | n_q_uu_l_u        | we say           |                    | Tunis       | 
| قالوا    | g_aa_l_a_w        | they said        |                    | Abu Dhabi   | 
| قالوها   | 2_a_l_uu_h_a      | they said it     |                    | Cairo       | 
| ما قالوش | m_a_#_2_a_l_uu_sh | they did not say |                    | Cairo       | 
| قالوا له | 2_a_l_uu_#_l_u    | they said to him |                    | Cairo       | 


### CODA* Seed Lexicon
A large and growing database containing verified examples of CODA* spelling for dialectal words, including affixes and clitics, is available here.


<details><summary>
  Markdown between html tags works when there's an empty line before it.
  </summary>
  here ```it doesn't work```

  here ```it works```

</details>
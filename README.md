# Uzbek Morphological Parser
Uzbek Morphological Parser using FST Toolkit `foma`.

## Structure
For now I set temprorary names:
- `nouns.lexc` - Lexicon script which defines the basic rules for appending affixes.
- `main.foma` - `foma` script that parses `noun.lexc`, saves it, and defines intermediate rules.
- `words.txt` - Current output of FST in lower (surface level).

## Suffixes

https://github.com/Mukhammadsaid19/uz-morph/wiki/Noun-Suffixes-Declaration


## Vocabulary

I have parsed only Uzbek entries from uz.wiktionary.org dump file through regexes. I will try to categorize the data by nouns, adjectives, verbs, pronouns, conjunctions, etc.

## Lexc Hacks (from _Finite State Morphology_ book)

There are several recipes for writing coherent code in Lexicon Compiler.

### Iteration for Lexicon

```
LEXICON MEGA
mega    MEGA ;
        SomeOtherLexicon ;
```
MEGA Lexicon branches into one or more "mega-" prefixes or to SomeOtherLexicon.

### Optional Morpheme in Lexicon

```
LEXICON GE
ge      NounRoots ;
        NounRoots ;
```
This will make the morpheme (in this case suffix -ge-) optional.

### Umbrella Lexicon
```
LEXICON Nouns
        CommonNouns ;
        SingularNouns ;
        PluralNouns ;
```

### DRY
Suppose you want some affix be available for certain nouns, while disallow it for others. Instead of duplicating the code, like this:
```
LEXICON Nouns
kirit   CaseEnd ;
faarum  CaseEnd ;
wadil   CaseEnd ;
wup     NomAcc ; ! This is our exception

LEXICON CaseEnd
u       # ;
a       # ;
i       # ;

LEXICON NomAcc
u       # ;
a       # ;
```
which seems inefficient and leads to troubles in refactoring. Instead try this:

```
LEXICON CaseEnd
        NomAcc ;
i       # ;

LEXICON NomAcc
u       # ;
a       # ;
```

Here it's much cleaner and coherent. 

### How to Choose a Tag Name

As I'm not a linguist, I have some difficulties with _naming_ Uzbek morphemes. Some of them have Turkish counterparts, some of them don't. So, the book provides several noteworthy guidelenes:

1. Prime Directive - use tags that are appropriate given the differences of your language. Don't try to copy from other linguistically distant language.
2. Secondary Directive - same morphemes mean same tags; however, if they act differently, then name them accordingly.
3. Tertiary Directive - use tags from related languages, unless it violates the first and the second principles.


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

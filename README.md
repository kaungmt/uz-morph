# Uzbek Morphological Parser
Uzbek Morphological Parsing using FST Toolkit foma.

# Structure
For now I set temprorary names:
- `nouns.lexc` - Lexicon script which defines the basic rules for appending affixes.
- `main.foma` - `foma` script that parses `noun.lexc`, saves it, and defines intermediate rules.
- `words.txt` - Current output of FST in lower (surface level).

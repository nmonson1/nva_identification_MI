# nva_identification_MI

Tiny_stories_nouns is kind of a mess, but includes training (noun/verb/adjective) vectors

TinyStories_NVA_ID is cleaner, and uses those vectors. I demonstrate how to change an LLMs interpretation of part of speech using them.

EG, Given the string "For breakfast, I ate an orange" the LLM will default to a next token of " cake" (treating orange as an adjective). If we subtract off the adjective vector and add in the noun vector, it will give a next token of "."

This has had at least partial success on every example I've tried. 

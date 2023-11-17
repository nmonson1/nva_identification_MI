# nva_identification_MI

Tiny_stories_nouns is kind of a mess, but includes training (noun/verb/adjective) vectors

TinyStories_NVA_ID is a bit cleaner, and uses those vectors. I demonstrate how to change an LLMs interpretation of part of speech using them.

“For breakfast, Tommy ate an orange” can complete to either “.” (the fruit, noun) or “ cake/ pie/ [other food]” (color/flavor, adjective). TinyStories defaults to “ cake”. Projecting off the adjective vector, and adding in the same amount of the noun vector changes it to “.” suggestive of noun (!) (if done before layers 0,1,2,3,6). The effect is strongest before layer 0, which is the only one where “ cake” is knocked out of the top three, and “ and” is a contender (also implying noun).

For “The old man”, I intervened on both “ old” (+noun-adjective) and “ man” (+verb-noun). Prior to activation patching, “The old” was followed by “ man”. Post-patch, it is followed by “ was” or “,” on all but one layer, which are both suggestive of noun. The final intervention was less clearly successful, leaving “ came”, “ comes”, or “ was” highest for 5 layers (all of which are still compatible with man-as-noun). However, the other 3 layers gave “ the”, “ie” and ”ly”. “ the” is suggestive of man-as-verb, and alternate endings are something that attach commonly to verbs–especially “ly” to make an adverb!

“Open” is an interesting case–it was the only word that (before I eliminated duplicates) showed up as potentially all three. TinyStories defaults to “Open it”, which seems clearly verb-like. Adding noun and subtracting verb changes it to “ was” (before layer 2) or “ and” (before layers 3,4,5) both of which are suggestive of nouns. Adding adjective instead gives “,” priority before layers 2 and 3, or “ and” and “ up” priority for layers 4 and 5, respectively–both compatible with adjective.

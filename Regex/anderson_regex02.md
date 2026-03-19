# Regex 2 Sonnet

1. Starting with removing stray ampersands and symbols not written in XML Format. Finding and replacing the strays with suitable formats.
1. Removing large spaces between paragraphs. Finding and replacing the spaces with nothing to keep everything condensed. With \n+, it would only be applied to new lines rather than the spaces in the whole document.
1. Just to make the reading easier and more accurate to the clean XML, I removed the beginning and end paragraphs mentioning copyright infringment.
1. Starting to actually make it look like the XML file, I made all the double spaced sentences into new lines since those are the starts to the line elements. {2,} to \n.
1. Roman Numerals were next to be wrapped and this worked for all but the first one when replacing with sonnet number="$1". My guess is maybe it got confused with me manually typing it earlier when I was deleting some text.
1. Getting the line elements using the (?! element sonnet="square bracket^"square bracket+"element end). Allows for everything after the sonnet elements to be wrapped in individual lines, like using (.+), \s, *, and $.
1. Closing the sonnet elements by using (?m) before the sonnet element calling and ^ and + for all to be called, then adding the closing sonnet before each new sonnet element.
1. Finishing by making sure all text is wrapped in the sonnet element with no attributes to make it so the whole thing now is a eligible XML file.
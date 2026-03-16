# Regex 1
- Started by converting any ampersands into the "&amp;" to make it readable in a XML File.
- Followed with more conversions of "<" and ">" by doing "&lt;" and "&gt;"
- New lines moved around to just one if there were more, with \n\n+ going to just \n
- Using ^.+$ showed 55 items
- No external links with ^.+\http
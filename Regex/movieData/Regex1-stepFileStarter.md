# Regex Steps for Converting Movie Data From a tab-separated text file to XML
;*Before beginning, think about how to do these assignments. It might be helpful to run a separate (free) Markdown editor to keep
your step recording in a different software window than oXygen, where you'll be writing your Find and Replace operations.
You want to be able to copy and paste your expressions into your markdown file to record them. 
I'm going to use Macdown (a nice markdown editor for Mac). Windows has Typora or reMarkable, etc.*
;First step is ALWAYS to search for characters that will disrupt XML encoding: 
`&amp;amp;amp`, `&lt;`, `&gt;`. 
XML is not allowed to contain raw ampersand characters `&amp;amp;`. 
So I needed to find:
;**Find:**
;```
&amp;amp;
```
**Replace:**
;and replace with the special escape characters for ampersands:
```
&amp;amp;amp;
```
I searched for `&lt;` and `&gt;` and did not find them. 
;Moving on, we can begin the "autotagging" find and replace process.
I wanted to wrap elements around whole lines. 
;I used the following expression to find. 
I made sure that *dot matches all* was NOT set so that
the dot matches on any character but only inside each line. 
This expression matches on the beginning of each line, 
and *one ore more characters on that line*.
;```
^.+
```
I set this to replace:
```
&lt;movie&gt;\0&lt;/movie&gt;
```
;Second step I matched this and set capturing groups so I could tag the titles:
;Find: 
```
(&lt;movie&gt;)(.+?)(\t)
```
;I set this to replace, so I could keep the first tag, and then add a new pair of tags for the title elements:
```
\1&lt;title&gt;\2&lt;/title&gt;
```
At the very end of class, I manually set a root element around the entire document 
```
&lt;xml&gt;
   &lt;movie&gt;...&lt;/movie&gt;
   &lt;movie&gt;....&lt;/movie&gt;
    &lt;!--yada yada yada more code --&gt;   
&lt;/xml&gt;
```
;And I saved the file as movieData.xml.
And I closed it.
And I opened my new movieData.xml and saw that I had a green square in oXygen, indicating 
that the document is well-formed. Yay!
;I can continue doing more regex find and replace operations to tag the dates, locations, and time durations inside each of these movie elements. 

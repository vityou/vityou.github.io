---
layout: post
title:  "A Basic Guide on the Usage of Regular Expressions"
date:   2018-08-31
categories: regex 
comments: true
---
This guide aims to teach you a little bit about regular expressions (usually calles "regex"s or "regexp"s for short).  In order to do so, we will be using regular expressions to change all of the presidents on [https://www.whitehouse.gov/about-the-white-house/presidents/](https://www.whitehouse.gov/about-the-white-house/presidents/) into Barack Obama.  Because lets be honest, he's immortal and has probably been pulling the strings since before America was created.  Now, let's get started.

Many people know that if you right-click and select `Inspect Element` on a webpage in chrome, it shows you an editable nicely formatted version of the webpage's source code.  Let's do that for [https://www.whitehouse.gov/about-the-white-house/presidents/](https://www.whitehouse.gov/about-the-white-house/presidents/)  Now, we want to find the section where it lists all of the presidents.  If you are proficient in the art of chrome right-click menus, you know that you can right-click on a link, select inpect element, and be directed to the section in the inspect element page where the link is.  So, either do that, or manually navigate to George Washington's name.  You'll notice that the list of names is enclosed in an HTML tag called `<ol>`, which stands for ordered list.  Right-click on the `<ol>` tag, and select `Edit as HTML`.  This gives us an editable version of everything from `<ol>` to `</ol>` on the page.  Go ahead and change "George Washington" to anything you like, and click out of the editor (**don't** refresh the page).  You'll see that "George Washington" was changed on the actual page as well.

So, we have a way to access the page source, now lets use regular expressions to change every president's name to Obama's.  There are several websites that alow you to create and edit regular expressions.  Just [look up "regex editor" on google](https://www.google.com/search?q=regex+editor).  I personally like [this one](https://regex101.com/).  Make sure you are using an editor that uses javascript syntax for their regular expressions.  If you're using the one above, select javascript in the "Flavor" section.  Now, go back to the presidents website, and copy the html text of the `<ol>` tag into the text part of your regex matcher.  The field is usually called something like "test string" or "text".  Above the text field you just copied into, there should be another one where you can enter your regular expression.  

What a regular expression does is match text according to certain rules or patterns.  You've probably matched text before too.  If you've ever pressed `ctrl-f` in a browser to search for the word "dog", you are using a pattern to match the word "dog".  The pattern in this case is just the literal sequence of charachters "dog".  You can do the same thing in regular expressions as well.  The difference between regular expressions and your browser's `crtl-f` is that regular expressions can do more than just match literal sequences of charachters.  For example, what if you wanted to match either the word "dog", or the word "puppy".  Using your browser's `ctrl-f`, you would need to do each one seperately.  Using regular expressions, however, you could match them at the same time.  To match both the words "dog" and "puppy", you would use the regular expression `dog|puppy`.  The `|` charachter means "or", and tells the regex searcher to look for either "dog" or "puppy".  What if you wanted to match either "tom" or "tim"?  You would use the regex `t[oi]m`.  This time we're using `[]`, to denote a set of charachters to match.  `[io]` tells the regex seracher to match either the charachter "i" or the cahrachter "o".  So `t[io]m` means "match t, then either i or o, then m".  There are many rules like this that make up regular expressions, and I wont cover them all.  Instead, lets take a look at the regex we will be using.

In oreder to replace the president's names with "Barack Obama", we will be using the regular expression `(<li><a href=[^>]+>)([^<]+)(.+)`.  Let's break down each part of the expression, starting with `(<li><a href=[^>]+>)`.  The parentheses denote something called a "group", in our case, they don't change how text is matched, but are useful when replacing text, which we'll get to later.  For now, just know that `asdf1(23)456` matches the same things as `asdf123456`.  If you look at the beggining of each line, you'll notice that they all start with "<li><a href=".  We can use this to our advantage and just tell the regex to match the literal sequence of charachters "<li><a href=".  None of those charachters have special meaning in regular expressions, they just match their literal selves.  The next piece is `[^>]+`.  The brackets denote a set of charachters to match.  However, `[^>]` doesn't mean match either "^" or ">", because "^" has a special meaning inside brackets.  It tells the charachter sequence to match any charachter **except** the ones inside the brackets.  So, `a[^asdf]c` would match things like "acc" and "aec", but not things like "aac" or "adc".  That means `[^>]` means match any charachter that isn't ">".  The `+` in `[^>]+` means that there must be 1 or more of the preceding charachter or charachter sequence.  `ad+` would match "ad", "addddd", and "add".  So, `[^>]+` means match one or more charachter that isn't ">".  We do this because we want to stop matching at the ">" and put what's next in another group.

Note that you can use things like `+` after groups to mean a group can be repeated one or more times. `a(bc)+` matches "abc", "abcbc", and "abcbcbc".  It doesn't just mean the last charachter can be repeated 1 or more times, so it wouldn't match the last 2 "c"s in "abccc".

The next part of the regex is `([^<]+)`.  If you look at what comes after the "<li><a href=...>" part, you will see that it is the president's name.  We want to match his name and store it in a group, so we tell the regex to match 1 or more charachters that aren't "<".  "<" is the first charachter that comes after every president's name, and we don't want it to be part of the group, so we exclude it from the charachter set using `^`.


The last part of the regex is `(.+)`.  The `.` stands for the set of every charachter, so it will match any cahrachter.  The `+` tells the regex to match one or more charachter of any kind.  Keep in mind that a newline isn't a charachter, so `.+` doesn't continue to match after a newline.  We can use this to our advantage because inspect element seperate all the list items with a newline.  However, if we weren't able to rely on newlines, we could use `<\/a><\/li>` instead of `(.+)`. The charachter "/" is a special charachter in javascript regexes, so we need to "escape" it with `\` to tell the regex interpreter that we want to match a literal "/".

If you look at the president list text you entered, it should all be hilighted, maybe in different colors or shades or colors depending on the regex editor you used.  This is good, it means the regex matched all of the list items.  It's time to replace the president's names with "Barack Obama".  Now we can make use of the groups we created when we made the regex.  In the "replace" or "substitution" section of your editor, enter `$1Barack Obama$3`.  Let's take a look at what this does.  When we created the regular expression, we made sure the wrap certain parts of it in parentheses.  Specifically the part before the president's name, the president's name, and the part after.  This doesn't mean that the regex matches 3 seperate things though.  What it means is that we can reference each of the three groups when we go to replace what the **entire** regex matched.  So, to list out what `$1Barack Obama$3` is doing:

1. Take one of the matches, let's say for example the match:
   `<li><a href="https://www.whitehouse.gov/about-the-white-house/presidents/george-washington/">George Washington</a></li>`
2. Realize that the match has three groups
    * Group 1: `<li><a href="https://www.whitehouse.gov/about-the-white-house/presidents/george-washington/">`
    * Group 2: `George Washington`
    * Group 3: `</a></li>`
3. Alow the user to reference these groups when replacing the whole thing
4. See that the user is referencing group one, since he used `$1`
5. Replace `$1` with the actual content of group 1
6. Add the text "Barack Obama" to the replacement, after group 1
7. Replace the `$3` with the actual content of group 3 and add it to the replacement (after "Barack Obama")
8. Replace the matched text with the replacement, which results in:
   `<li><a href="https://www.whitehouse.gov/about-the-white-house/presidents/george-washington/">Barack Obama</a></li>`
9. Repeat steps 1-8 for the rest of the matches

We are pretty much done now. Copy the new text resulting from the substitution and replace the presidents list on the website with it.  You should see this:

<img src="/assets/obama-regex.png" alt="obama is the only president picture" height="400" style="border:1px solid #000000" />

If you want to do more, you can try to make every link go to obama's link as well, but that is all for now.

Some useful resources:

- [a good overall guide](https://www.regular-expressions.info/)
- [the wikipedia page](https://en.wikipedia.org/wiki/Regular_expression)
- [more on the javascript syntax we used](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
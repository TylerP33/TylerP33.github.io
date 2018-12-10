---
layout: post
title:      "Final Blog - Let's talk about what Draft.JS is"
date:       2018-12-10 12:28:51 -0500
permalink:  final_blog_-_lets_talk_about_what_draft_js_is
---


I just finished my final project, and I am pretty proud of how it came out.  It fulfilled all the necessary requirements to pass but in concept, it is slightly different than your basic CRUD application.  I am a hobbyist writer, albeit a very whimsical and lazy one.  Regardless, I do enjoy writing and it's incredibly satisfying to me.   So, as a person who likes to write and as a person who recently learned how to build things on a computer, I always thought it would be really cool to construct a basic word processor.

Well, after I got super excited about the idea of putting these two activities together through our final project, I quickly became deflated when I found out building a real-life, feature filled word processor, or even a basic rich text editor, can be a large, large task.  So, discouraged and upset, I toiled with a bunch of different ideas that did not peek my interest at all, especially compared to my original idea.  I thought all was lost, and that I was going to be stuck building something that I had zero interest in... that was until I stumbled upon a nifty little framework called Draft.JS.

Draft.JS is a rich text editor framework that was developed by Facebook in 2016.  It's a framework that is perfect for building something as simple as an editor with a few inline text styles supported (thats what I have done so far) or building a complex text editor for composing long-form articless (what I will continue to work on as a side project).  And do you want to know what the best part about Draft.JS is?  The fact it was built by Facebook should be a big hint as to why it works perfect for our React project.  Facebook created React!  And Facebook created Draft.JS to handle a lot of the functionality that is seen in Facebook.  Essentially, they designed Draft.JS to replace the intended functionality of `contentEditable`, which from what I have read, has a ton of bugs too it, especially in relation to cross-browser isssues.

So, my final project is a simple Word Processor with a few InlineStyles, as well as a few text search features that help make the program fun and interactive.  I am super proud of it and I am excited that I can continue to add on features and maybe one day, it'll be a pretty nifty little online text-editor/word processor (that will depend on which direction I take it).

# Technical Snippet
Now, before I sign off, it wouldn't be right not to show you something cool from Draft.JS, as far as how it works on a technical level.  Read this:

> Draft.js is a framework for building rich text editors in React, powered by an immutable model and abstracting over cross-browser differences.
> 
Straight from the homepage itself!

Draft.JS uses immutable objects to keep a constant "snapshot" of the built in `<EditorState />` component that you physically type into while working with Draft.JS.  That means the object isn't just tracking the text aspect of the editor.  It is tracking where the cursor last was, what kind of styling and indentation was used and what the ranges were for those specific styles, and even what type of media files are within the editor.  And those are just a few examples!  The immutable model that Draft.JS has is truly incredible.  When you start to work with it, it slowly keeps impressing you and when you realize it's full potential, you start to see the genius behind the whole setup.

Let me show you a simple example of what that Object looks after it is converted into raw JSON (another part of the Draft.JS framework that is done by a built in method called `convertToRaw()`).

```
"{"blocks"=>[{"key"=>"5p965", "text"=>"blank check here - chxeck it out. Blank check it out. Blank check it out. Blank check it out! Blank check it out! ", "type"=>"unstyled", "depth"=>0, "inlineStyleRanges"=>[{"offset"=>0, "length"=>9, "style"=>"ITALIC"}, {"offset"=>0, "length"=>118, "style"=>"BOLD"}, {"offset"=>0, "length"=>118, "style"=>"CODE"}], "entityRanges"=>[], "data"=>{}}, {"key"=>"bpt2r", "text"=>"",
```

Here it is!

It's a record of exactly what was going on in the editor.  The text property contains all the text and then following, you get individual nested style objects.  The one contains color, italic, bold and code like so:

```
 {"offset"=>0, "length"=>9, "style"=>"ITALIC"}
 
 {"offset"=>0, "length"=>118, "style"=>"BOLD"}
 
 {"offset"=>0, "length"=>118, "style"=>"CODE"}
```

That length is the range of characters where the inline styling was applied.  So, when that same text is put back on the screen, it will save all those changes and display them accordingly.

All these changes are stored in one nested array called inlineStyleRanges:

`"inlineStyleRanges"=>[{"offset"=>0, "length"=>9, "style"=>"ITALIC"}, {"offset"=>0, "length"=>118, "style"=>"BOLD"}, {"offset"=>0, "length"=>118, "style"=>"CODE"}]`

I haven't really dove into all that this framework is capable of, largely because I needed to actually finish my project sometime in the next 100 years.  But, like I said earlier, I am so happy to have a good foundation on a project that I am really passionate about.  I am going to keep on building!


 
 





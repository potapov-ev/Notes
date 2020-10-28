## Comments

>Nothing can be quite so helpful as a well-placed comment. Nothing can clutter >up a module more than frivolous dogmatic comments. Nothing can be quite so >damaging as an old crufty comment that propagates lies and misinformation.

Commentary is a necessary evil

Comments are always failures. We must have them because we cannot always figure out how to express ourselves without them, but their use is not a cause for celebration. The ideal situation is when your code doesn't need comments. We must strive for this.

However, some comments are necessary or beneficial. Keep in mind, that the only truly good comment is the comment you found a way not to write.

### Good comments
* Legal comments

```javascript
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```

Comments like this should not be contracts or legal tomes. Where possible, refer to a standard license or other external document rather than putting all the terms and conditions into the comment

* Informative comments

```javascript
// format matched kk:mm:ss EEE, MMM dd, yyyy
const timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```

In this case the comment lets us know that the regular expression is intended to match a time and date. Still, it might have been better, and clearer, if this code had been moved to a special class that converted the formats of dates and times. Then the comment would likely have been superfluous.

* Expression of intent

```C++
//This is our best attempt to get a race condition 
//by creating large number of threads. 
for (int i = 0; i < 25000; i++) { 
  WidgetBuilderThread widgetBuilderThread = new WidgetBuilderThread(widgetBuilder, text, parent, failFlag); 
  Thread thread = new Thread(widgetBuilderThread); 
  thread.start(); 
}
```

You might not agree with the programmer’s solution to the problem, but at least you know what he was trying to do.

* Warning of consequences

```javascript
// Don't run unless you
// have some time to kill.
function _testWithReallyBigFile() {
  res.send(reallyBigFile);
}
```

* TODO comments

### Bad comments
List of bad comments may be to long. Just know that if you still had to write a comment, it should not be:

* Mumbling

```javascript
function loadProperties() {
  try {
    const propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
    const properties = readFileSync(propertiesPath);
    loadedProperties.load(properties);
  } catch(er) {
    // No properties files means all defaults are loaded
  }
}
```

What does that comment in the catch block mean? Clearly it meant something to the author, but the meaning does not come through all that well. Apparently, if we get an IOException, it means that there was no properties file; and in that case all the defaults are loaded. But who loads all the defaults? Were they loaded before the call to
loadProperties.load?
Our only recourse is to examine the code in other parts of the system to find out what’s going on. Any comment that forces you to look in another module for the meaning of that comment has failed to communicate to you and is not worth the bits it consumes. 

**You should be clear in your comments**

* Redundant comments

```java
// Utility method that returns when this.closed is true. Throws an exception
// if the timeout is reached.
public synchronized void waitForClose(final long timeoutMillis)
  throws Exception
{
  if(!closed) {
    wait(timeoutMillis);
    if(!closed) throw new Exception("MockResponseSender could not be closed");
  }
}
```

What purpose does this comment serve? It’s certainly not more informative than the code. It does not justify the code, or provide intent or rationale. It is not easier to read than the code.

**No need to duplicate code in your comments**

* Misleading comments

Sometimes, with all the best intentions, a programmer makes a statement in his comments that isn’t precise enough to be accurate. Consider for another moment the badly redundant but also subtly misleading comment we saw in previous example.

The method does not return when this.closed becomes true. It returns if this.closed is true; otherwise, it waits for a blind time-out and then throws an exception if this.closed is still not true.

This subtle bit of misinformation, couched in a comment that is harder to read than the body of the code, could cause another programmer to blithely call this function in the expectation that it will return as soon as this.closed becomes true. That poor programmer would then find himself in a debugging session trying to figure out why his code executed so slowly.

**Don't mislead others with your comments**

* Mandated comments (like "function must have a javadoc")

It is just plain silly to have a rule that says that every function must have a javadoc, or every variable must have a comment. Comments like this just clutter up the code, propagate lies, and lend to general confusion and disorganization. 

```javascript
/**
 *
 * @param title The title of the CD
 * @param author The author of the CD
 * @param tracks The number of tracks on the CD
 * @param durationInMinutes The duration of the CD in minutes
 */
 function addCD(title, author, tracks, durationInMinutes) {
   const cd = new CD();
   cd.title = title;
   cd.author = author;
   cd.tracks = tracks;
   cd.duration = duration;
   cdList.add(cd);
 }
```

**This clutter adds nothing and serves only to obfuscate the code and create the potential for lies and misdirection.**

* Position markers

Sometimes programmers like to mark a particular position in a source file. 
```javascript
// Actions //////////////////////////////////
```

There are rare times when it makes sense to gather certain functions together beneath a banner like this. But in general they are clutter that should be eliminated—especially the noisy train of slashes at the end.
Think of it this way. A banner is startling and obvious if you don’t see banners very often. So use them very sparingly, and only when the benefit is significant. If you overuse banners, they’ll fall into the background noise and be ignored.

**Use regions in these cases**

* Closing brace comments 

```javascript
    while (!line) {
      lineCount++;
      charCount += line.length();
      const words = line.split(" ");
      wordCount += words.length;
    } //while
    System.out.println("wordCount = " + wordCount);
    System.out.println("lineCount = " + lineCount);
    System.out.println("charCount = " + charCount);
  } // try
  catch (er) {
  console.log("Error:" + er);
  } //catch
} //function
```

**Use IDE extensions for syntax highlighting**
 
* and such bullshit

**Make clean, self-documenting code**

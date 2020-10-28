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
  }
  catch(er) {
    // No properties files means all defaults are loaded
  }
}
```

What does that comment in the catch block mean? Clearly it meant something to the author, but the meaning does not come through all that well. Apparently, if we get an IOException, it means that there was no properties file; and in that case all the defaults are loaded. But who loads all the defaults? Were they loaded before the call to
loadProperties.load?
Our only recourse is to examine the code in other parts of the system to find out what’s going on. Any comment that forces you to look in another module for the meaning of that comment has failed to communicate to you and is not worth the bits it consumes. 

**You should be clear in your comments**

* Redundant comments
* Misleading comments
* Mandated comments (like "function must have a javadoc")
* Position markers
* Closing brace comments 
* and such bullshit

**Make clean, self-documenting code**

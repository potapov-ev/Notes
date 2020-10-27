## Comments

>Nothing can be quite so helpful as a well-placed comment. Nothing can clutter >up a module more than frivolous dogmatic comments. Nothing can be quite so >damaging as an old crufty comment that propagates lies and misinformation.

Commentary is a necessary evil

Comments are always failures. We must have them because we cannot always figure out how to express ourselves without them, but their use is not a cause for celebration. The ideal situation is when your code doesn't need comments. We must strive for this.

However, some comments are necessary or beneficial. Keep in mind, that the only truly good comment is the comment you found a way not to write.

# Good comments
* Legal comments

    // Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
    // Released under the terms of the GNU General Public License version 2 or later.

  Comments like this should not be contracts or legal tomes. Where possible, refer to a standard license or other external document rather than putting all the terms and conditions into the comment

* Informative comments

  // format matched kk:mm:ss EEE, MMM dd, yyyy
  Pattern timeMatcher = Pattern.compile(
  "\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");

  In this case the comment lets us know that the regular expression is intended to match a time and date. Still, it might have been better, and clearer, if this code had been moved to a special class that converted the formats of dates and times. Then the comment would likely have been superfluous.

* Expression of intent

---
layout: post
title: Don't use -- as a comment in SQL
subtitle:
categories: scripts
tags: [script, sql]
---

Writing a quick comment in a SQL script can be achieved by a -- followed by the comment. This is useful for explaining scripts as seen below.

``` sql
delete from tablename
 -- now make sure we delete the correct rows
 where columnname = 'delete-this-row';
```

...but if any external system, a command logger for example, renders the script into one line you can end up with a problem. Although this will probably never get executed if anyone were to copy and paste this script it could end up being a bad day.

``` sql
delete from tablename -- now make sure we delete the correct rows where columnname = 'TO_DELETE';
```

A better way is to use /* and */ to place a comment as seen below.

``` sql
delete from tablename
 /* now make sure we delete the correct rows */
 where columnname = 'delete-this-row';
```

...even if this is rendered into one line the comment is contained and the where clause is still functional.

``` sql
delete from tablename /* now make sure we delete the correct rows */ where columnname = 'TO_DELETE';
```

Although the chances of this situation happening is slim it is a possibility and rather mitigate it than hope for the best.
---
layout: post
title: Drop DB Link in another Schema
subtitle: a workaround
categories: scripts
tags: [script, oracle]
---

While scripting some jobs for our on-premise to AWS RDS migration I wanted to consolidate some old DB Links during testing but as you know you cannot delete a DB Link in another schema.

## Restriction on Dropping Database Links

You cannot drop a database link in another user's schema, and you cannot qualify dblink with the name of a schema, because periods are permitted in names of database links. Therefore, Oracle Database interprets the entire name, such as ```SCOTT.SALESDBLINK```, as the name of a database link in your schema rather than as a database link named ```SALESDBLINK``` in the schema ```SCOTT```.

## Problem

Creating a script to automate this becomes a challenge if you have to keep jumping  in and out of other SCHEMAs to drop the DB Links.

There must be a simpler way.

## Solution

You can create a procedure in the SCHEMA you want to remove the DB Link from and then execute this procedure. After the procedure has finished you can then simply drop it.

Here is an example: -

```sql
create procedure scott.drop_db_link as
begin
  execute immediate 'drop database link SALESDBLINK';
end;

exec scott.drop_db_link;

drop procedure scott.drop_db_link;
```

This can be scripted quite easily and you don't have to keep jumping in and out of different SCHEMAs to drop database links if needed.

Happy codin'

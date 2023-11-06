# Reading Lists upgrade

If you have a FeedLand installation prior to v0.6.0, released on October 14, 2023, you'll need to make some changes to the database before installing the new software. 

There are changes to the subscriptions table, and two new tables, readinglists and readinglistsubscriptions.

The new software supports Reading Lists, user-level docs to come.

### Notes on <i>subscriptions</i> table changes

We had to change the lengths of <i>listName</i> and <i>feedUrl</i> to create space for adding <i>urlReadingList</i> to the primary key in the <i>subscriptions</i> table. 

This created problems for us, and possibly will for you. Some feedUrl's may not fit in 256 characters. In feedland.org's database, there were only three records, out of tens of thousands. I solved the problem by deleting the subscriptions. Far from an ideal solution, but the other alternative was to reorganize this table and the code that runs it, and the cost for that was too high. I'm still learning about SQL databases, and I apologize if you hit similar problems in this change, if so -- please post a note in <a href="https://github.com/scripting/feedlandInstall/issues/40#issue-1943334716">this thread</a>.

### Database changes

```SQL

### Installing new software

After making the database changes, install the new versions of feedland and feedlanddatabase with ``npm update``

### Problems, questions, suggestions, kudos

I started a <a href="https://github.com/scripting/feedlandInstall/issues/40#issue-1943334716">thread</a> in the Issues section. 

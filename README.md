# Rollback Scavenger Hunt

Objective: In this repository, you will learn how to use the power of **Git** to _undo_ any changes you've made.

This will be in the form of a scavenger hunt.  Better than knowing _what to type_ is knowing **where to look** for _what to type_.

### How to begin

1. Fork and clone this repository.
2. Open `rollback.md` and use that file for all of the following directions.

## Undo edits
Go ahead and make some changes to `rollback.md`.  Whatever you want.  It doesn't matter.  Add some text, delete some, change some, etc.

Great! Now you've made some edits, but let's say you want to undo that.  Here's your hint: type `git status`.  Notice that `git` is giving you two hints:

```
On branch master
Changes not staged for commit:
  (use "%%%%%%%%%%%%" to update what will be committed)
  (use "%%%%%%%%%%%%" to discard changes in working directory)

        modified:   rollback.md
```
Yes, the commands have been replaced with `%%%%%%%%%%%%`.  You need to **type the command that will discard your changes.**  NOTE: you do NOT need to type the `...`

Now you know how to undo edits!

#### When would you use this?
This is one of the most frequently used "rollback" commands.  Suppose you're working on a repo with someone else, and you accidentally started editing a file that you shouldn't have (because you know you're going to get a merge conflict, and you'd rather avoid it altogether than have to deal with it). Instead of doing `edit > undo` a whole bunch of times, using this command will reset that file (or multiple files) back to the last commit to ensure it's exactly how it was before you started editing.

## Undo `add`
Go ahead and make some changes to `rollback.md` again, but this time go ahead and **`add` the file to the stage**.  Now `rollback.md` is green, yah?  Well the only way you would know that is if you **type `git status`**.  Since you did, notice what it says above the green filename.  **Go ahead and type that.**

**Doing `git status` again** should bring the file back to red.  Hooray!  We unstaged it.

#### When would you use this?
Let's say you edit two files, and you accidentally did `git add .` (which adds both files to the stage), but you only meant to add one of the files (the other one is still broken).  You would want to remove the broken file from the stage with this command.

## Undo `commit`
Where we just left off, `rollback.md` is red, which means it has changes but isn't on the stage.  Go ahead and **`add` it to the stage and `commit` it.**

Whoops! Let's say we didn't mean to take that snapshot.  How do we undo it?  Unfortunately, `git status` won't help you this time.  You'll have to rely on your next best friend: Google.

**Do a search for `git undo commit`**.  The first result points to _Stackoverflow_, a great coding forum where people ask and answer questions.  The best part is that common questions get "upvoted", and so do the best answers.  Notice how many times this question has been upvoted: about 12000 times.  Also notice how many times the "best" answer has been upvoted: also about 12000 times (you'll see a little :white_check_mark:).

While the most upvoted answer is usually the first place to look, it never hurts to look beyond it (just like looking at more than just the first search result when using Google).  In this case, the second-most upvoted answer is what we want (the one with almost 8000 votes).  It has a pretty good explanation of how to do exactly what we want.

Read the first couple of paragraphs, but pay careful attention to this part (note: index means staging area)

> For the lightest touch, you can even undo your commit but leave your files and your index
>

**Type the command that will do that.**

Yay! You just un-commited.  **Using `git status`** shows us the green file which means we're right back to where we were before we made the commit.

#### When would you use this?
If you want to leave the files in the staging area, that means you don't need to make any edits.  So this only really applies to changing your commit message.  All it will do is undo typing `git commit -m "blah blah blah"`.

## Undo `commit` and `add`

Where we just left off, we "un-commited", so our file is still green which means it still has the edits and it's on the stage, ready to be committed.

Let's go ahead and **commit it again**, then we're going to destroy the commit.  Look at the same post on _Stackoverflow_ for this:

> You want to **undo the commit but keep your changes** for a bit of editing before you do a better commit.
>

Go ahead and **do that**.

Sweet! You just undid both the `commit` and the `add`, so a `git status` should show you the file in red.

#### When would you use this?
This would probably be helpful if you spotted a small typo right after you commit, or wanted to include something else in this snapshot, so you need to undo the commit and reset the staging area.

## Undo `commit` and `add` AND edits

Where we just left off, we "un-commited" and "un-added", so a `git status` shows that our file is red which means it still has the edits but it's not on the stage.

Let's go ahead and **add and commit it again**. We're about to destroy the `commit`, the `add`, and the edits (taking us all the way back to our last commit).  Looking back at the same post on _Stackoverflow_, do you see how you can completely destroy your last commit?

> You want to **nuke commit C and never see it again.**
>

**Nuke it**.

#### When would you use this?
This is a very dangerous command, so use it sparingly.  It's much safer to rollback to a previous commit.

## Revert to a previous commit
Alas, the moment has come to learn how to revert.  It's time to modify our Google search. Try this: **git rollback to previous commit**. The first two resources are great:

1) Atlassian Git Tutorial
2) Yet again, _Stackoverflow_.  Become best friends with _Stackoverflow_.

Read the first one.

Then read the second one on Stackoverflow, but this time, the most upvoted answer (with the green checkmark) is the one we want.

Let's remove the training wheels completely. Do your best to understand `git revert`, and if you want, `git reset` (both with the proper syntax).  Try things, mess them up, and make sure you read for understanding.  You may get merge conflicts with yourself.  Remember, `git status` is your best friend. You got this. :thumbsup:
# Cloning repos, sharing code

## Goals

We'll now see how you can collaborate in code with a classmate. Our goals are this:

* To pick a partner
* To clone their repo to your machine.
* To edit the file and use the git cycle to commit the changes.
* To go to your own repo and pull the changes made by your partner.
* We'll then introduce a code conflict and learn how to resolve it.

## Clone a repo

* In your browser, go to your partner's Github profile and click on Repositories if necessary, then on their repo.
* Look for the button **Clone or download**. You want to copy the URL for cloning, like this:

![clone](../../images/github-clone-repo.png)

* Go into your regular Terminal app and cd into `~/Documents/code`.
* Do `git clone {URL}` but paste the URL you copied. This is the same as you did with your own repo, but now you have downloaded your partner's repo.

If you wanted the repo to be a different name on your computer, you would add the name you want after the url. I tend to keep the same name unless there is a good reason not to.

* `cd` into the folder you have downloaded and then do `$ code ./`, which will open a new VS Code window with all the files in that repo. You are ready to work.

## Make your edits

* Use the VS Code Explorer on the left to find your partner's named file and open it.
* Add a new sentence praising your partner's command of git and Github thus far. Save and close the file.
* Add a new file to the repo called `newfile.md`. You can use the **File > New file** menu or the little buttons in the Explorer.
* Add a title and a paragraph of text, using proper Markdown syntax. Save and close your work. (Depending on time, we might talk about and load the Markdown Syntax Linter.)
* Open the Integrated Terminal and go through the steps to check status, add files, commit files (with message), and push to origin master.

## Pull your partner's edits

* Go back to the VS Code window that is your own repo.
* Use the Integrated Terminal to do `$ git pull origin master`, which will download the changes made by your partner. Yes, `pull` is the opposite of `push`.

## Dealing with conflicts

You might ask yourself ... what's to keep two people from changing the same line of code? Well, they can, and you will. It creates a **code conflict** that must then be resolved.

We're going to create such a conflict so you can see that this looks like.

### Your original change

* Find your VS Code window with your own repo and make a change within the first sentence.
* Add, commit and push your changes to Github.

So now, in your partner's copy of your repo, there is a change that they do not have.

### Change your partner's repo

* Go back into your partner's repo in VS Code and change that same first sentence, but do it in some different way.
* Add, commit and try to push your changes. When you try to push, you won't be able do. You'll get a message something like this:

``` bash
$ git push origin master
To github.com:critmcdonald/myproject-christian.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'github.com:critmcdonald/myproject-christian.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
(base) ✘-1 ~/Documents/code/myproject-christian [master ↓·1↑·1|✔] 
```

You can see from the hints in the error message, that there are changes on the remote repo that you don't have. Git won't let you push new changes unless you have the current remote copy from the server. That keeps you from screwing up something that is already there (which is kinda what we are doing).

So, you have to pull the remote changes first.

* Do `$ git pull origin master` to update your repo. It will work, but you'll get message about the conflict.

``` bash
$ git pull origin master
From github.com:critmcdonald/myproject-christian.git
 * branch            master     -> FETCH_HEAD
Auto-merging newfile.md
CONFLICT (content): Merge conflict in newfile.md
Automatic merge failed; fix conflicts and then commit the result.
(base) ✘-1 ~/Documents/code/myproject-christian [master|MERGING ↓·1↑·1|✖ 1] 
```

Now look at the file in VS Code, and it will look pretty crazy. Here is mine:

![clone](../../images/conflict-screen.png)

Let's break this down:

* The highlighted line with `HEAD` is the beginning of the conflict.
* The other highlighted line is the end of the conflict.
* It's up to you to choose what should be inbetween those notes. You would of course want to discuss this with your collaborator and come to an agreement on what this should be. Fix up the file the way you have agreed and then remove all the notes and the line between the two pieces.
* Once you have it the way you like it, save, add, commit and push.

### Get your own repo right

* Go back to your own repo in VS Code and do `git pull origin master`. Depending on how you resolved the conflict together, you might have to go through the process again. You might go look at the repo on Github and copy/paste the line to ensure you have it the same. Add, commit and push as necessary.

## Good coding practices: Syntax

One tactic to being a good collaborator with code is to follow syntax, meaning you write code to a shared standard. Each programming language has its own standard, including how many spaces to indent, how you capitialize, etc.

We've been writing in Markdown, and here are two resources about that syntax:

* [Markdown tutorial](https://guides.github.com/features/mastering-markdown/)
* [Markdown syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax/)

------

Next: [Git branches](git-branch.md)
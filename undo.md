# Undo command 
## the different between git-revert and git-reset 
If you are beginner of Git version control software. You should confuse on git-revert and git-reset, Both of them are commands that help you modify thous wrong commit, but You also can use `checkout -- <file-name>`command, when you want to drop off changed file on stage.
Let's get our hands dirty.

## One First command --`checkout -- <file-name>`
Imaging that situation, You want to test some new features and change a file you should not to touch, If you don't fix this problem, It causes a few of conflicts with your co-workers.
Generally, If I was you, I don't push any codes to remote when I changed codes which is not belong to me. 
**If you were bearing this situation**. Don't panic, to type `checkout -- <file-name>`then every thing comes back for you.
By the way, this command has a lot of usages, that can change branch etc.
You also can use `git checkout -f HEAD` to clear working directory tree from all changes, however, there is a better way to do this `git stash`,this command can stash all the changes whenever you want to roll back. 
## Two `git-reset`command almost help you reset comment
Let's see synopsis of this command.
> git reset [-q] [<tree-ish>] [--] <paths>…​
git reset (--patch | -p) [<tree-ish>] [--] [<paths>…​]
git reset [--soft | --mixed [-N] | --hard | --merge | --keep] [-q] [<commit>] 

The common way about using this command is the third line.So we talk about the first two line first.

####first line of reset description
Both of the line one and two are the opposite of `git add <path>` which adds some change to stage (minor unit is patch). the `git reset <paths>`'s effects is same as command `git checkout -- <paths>`

####second line of reset description
This mean that `git reset -p` is the opposite of `git add -p`

####The MODE of git-reset
There are five modes in git-reset. You may use three of them usually. they are `--soft, --mixed, --hard`and `--merge --keep` are hardly to be used.

So, what is the different of all of threes.You may see the mean from them names.there are two kinds of opposite mode **soft** and **hard**. **mixed** is in the middle of them. I will explain them in regular way.
Firstly, let's talk about workflow on git. One day, you edited some file and ready to add to stage then you entered command `git add xxx.m` and now the file is recorded on work tree after that you commit it with "first commit" message. finally you looped those work flow three times.

Now we got three commits named "first commit", "second commit" and "third commit". 
Woops, you found that the second commit and third commit message were worry. you want to reset the index and working tree and any changes to tracked files in the working tree since <commit> are discarded. if you used `--hard` flag.

`--soft` flag means does not touch. the index file or the working tree at all. This leaves all your changed file "changes to be committed", as git status would put it.

`--mixed` 


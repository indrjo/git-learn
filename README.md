# Git Cheatsheet


## Preamble

The following ```README``` is a small cheatsheet for an usual *git* workflow. It is mainly for personal reference, but if you find it useful, I'm glad.


## Important tip: ```git status``` is your friend

It is not important to memorize every single *git* command. Who could? Fortunately the amount of commands to remember for a basic *git workflow* is quite small. Just in case, *git* is to help you always:
```
$ git status
```
tells you the status of the files in your working tree, but also provides you hints for the next step.

For example, if you have modified a file in you working tree, then
```
$ git status 
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md
```
is talling you that now you may consider to run ```git add <file>``` or ```git restore <file>```, both alternatives accompanied by a short description. If you get stuck for some reason, try to run ```git status``` first.


## Modified, staged, committed

*Yet to come...*


## Staging files

Elevate *modified* files to the status of *staged*.
```
$ git add FILE1 FILE2 ...
```

### Have you staged something you wouldn't have?

For example, say you have run:
```
$ git add this-file.txt
```
Do not worry, interrogate *git*:
```
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   this-file.txt
```

To brink a staged file back to the status of unstaged, just:
```
$ git restore --staged <file>
```


## Committing your changes

Take *staged* files (see the preceedeing section) to be *tracked* in ```.git```.
```
$ git commit -m 'commit message'
```

I you forget to insert another staged file in your commit, then you can do this
```
$ git commit --amend
```


## Removing files

```
$ git rm FILE
```

**(To change)** However, this command deletes ```FILE``` from your disk too. If you want a staged file to be removed from the status of stages and keep it in your working tree, then
```
$ git rm --cached FILE
```

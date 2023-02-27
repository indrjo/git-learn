# Basic git


## *git status* is your friend!

It is not important to memorize every single *git* command. Who could? Fortunately the amount of commands to remember for a basic *git workflow* is quite small. Just in case, *git* is to help you always:

```sh
$ git status
```

tells you the status of the files in your working tree, but also provides you hints for the next step.

For example, if you have modified a file in you working tree, then

```sh
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md
```

is telling you that now you may consider to run

```sh
$ git add <file>
```

or 

```sh
$ git restore <file>
```

Both possibilities here are accompanied by a short descriptions. If you get stuck for some reason or do not remember a command, try ```git status``` first.


## Modified, staged, committed

*Yet to come...*


## Staging files

Elevate *modified* files to the status of *staged*.

```sh
$ git add FILE1 FILE2 ...
```


## Have you staged something you shouldn't have?

For example, say you have run:

```sh
$ git add this-file.txt
```

Do not worry, ask *git* for help:

```sh
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   this-file.txt
```

To brink a staged file back to the status of *unstaged* it is suggested the following command:

```sh
$ git restore --staged <file>
```

Thus, in our case, it is sufficient to issue:

```sh
$ git restore --staged this-file.txt
```


## Committing your changes

Take *staged* files to be *tracked* in ```.git```.

```sh
$ git commit -m 'commit message'
```

If you have forgot to insert another staged file, say ```foo.txt```, in your commit, then you can do this:

```sh
$ git add foo.txt
$ git commit --amend
```

You will be prompted a *vim* display: if you want you can edit the commit text too. When finished, *just exit vim.*

If you do not want to mess with *vim* up, then you may prefer

```sh
$ git commit --amend -C main
```

With this command we are saying to git to reuse the previous commit text.


## Removing files

If you delete some tracked file, say ```baz.txt```, with

```sh
$ rm baz.txt
```

in ```.git``` it still exists and could be recovered (read below). If you want to get rid of it definitely from your disk and your ```.git```, then

```sh
$ git rm baz.txt
```

If you want a staged file to be removed from the status of staged and keep it in your working tree, then

```sh
$ git rm --cached baz.txt
```


## Undo a ```git push```

Assume you have just run

```sh
$ git push
```

but afterwards you notice there is a small problem with the commit you have pushed. You can correct this via

```sh
$ git revert <SHA>
```

The string to be put instead of ```<SHA>``` can be determined via

```sh
$ git log --oneline
```

You have to look at the recent commit and take just the initial string of seven alphanumeric characters. Example: if we have

```sh
$ git log --oneline
8cfd3ec (HEAD -> main, origin/main) added section "Undo a gith push"
e56a8c7 deleted LICENSE.txt
4fb4172 Corrected title of README.md
[...]
```

then copy ```8cfd3ec```.

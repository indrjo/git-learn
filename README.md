# Git Cheatsheet

## Important tip

It is not important to meorize every single command. IF you do good. Otherwsie,
```
git status
```
will give you some hint.


## Staging files

Elevate *modified* or *untracked* files to the status of *staged*.
```
git add FILE1 FILE2 ...
```


## Committing your changes

Take *staged* files (see the preceedeing section) to be *tracked* in ```.git```.
```
git commit -m 'commit message'
```

I you forgot to insert another staged file in your commit, then you can do this
```
git commit --amend
```

## Removing files

```
git rm FILE
```

**(To change)** However, this command deletes ```FILE``` from your disk too. If you want a staged file to be removed from the status of stages and keep it in your working tree, then
```
git rm --cached FILE
```


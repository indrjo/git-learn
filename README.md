# Git Cheatsheet

## Staging files

```
git add FILE1 FILE2 ...
```


## Committing your changes

```
git commit -m 'commit message'
```

I you forgot to insert another staged file in your commit, then you can do this

```
git commit --amend -C main
```

## Removing files

```
git rm FILE
```

However, this command deletes ```FILE``` from your disk too. If you want a staged file to be removed from the status of stages and keep it in your working tree, then

```
git rm --cached FILE
```


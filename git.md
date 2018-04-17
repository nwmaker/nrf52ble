# GIT 

## use the remote to overwrite local files
```
git fetch --all
git reset --hard origin/master
```

The fetch downloads the latest from the remote without trying to merge or rebase anything. Then reset reverts the master branch to what just fetched from the remote.




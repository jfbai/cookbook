# Git examples

## Push all tags to a remote

Push all tags on upstream remote to origin remote.

```
git fetch upstream
git push origin --tags
```

## Change tracking remote brach

Change upstream of a branch.

```
git branch branch_name --set-upstream-to your_new_remote/branch_name
```

# Pull Request Workflow

1. Find a project you want to contribute to
2. Fork it from default branch
3. Clone it to your local system

4. Add Remote Upstream
```
git remote add upstream git@github.com:viafoura/Viafoura-Front.git
git fetch upstream
git rebase upstream/main
git push origin main --no-verify
```

5. Make a New Branch
```
git checkout -b <branch>
```

6. Add and Commit Changes
```
git add .
git commit -m "<JIRA-ISSUE>: Title" -m "Description"
```

7. Before Pushing Update Main
```
git checkout main
git fetch && git rebase
git push origin main --no-verify
```

8. Push Branch
```
git checkout <branch>
git rebase -i main (peak 1st, squash others, then # comments)
git push origin <branch> --force-with-lease
--- If there are new commits to branch then
   git pull --rebase origin <branch>
```

9. Open github link
10. Click the Compare & pull request button
11. Click Create pull request to open a new pull request
12. After changes have been approved, update main branch
```
git fetch && git rebase
```

## Useful Commands

- Update remote braches locally
```
git remote update upstream --prune
```

- Verify parent
```
git show-branch | grep '*' | grep -v "$(git rev-parse --abbrev-ref HEAD)" | head -n1 | sed 's/.*\[\(.*\)\].*/\1/' | sed 's/[\^~].*//'
or
git log --first-parent
```

- Fetch a PR into a Fork
```
git fetch origin pull/ID/head:BRANCHNAME)
Example:
git fetch upstream pull/3247/head:CON-3000-topic-follows
```
- Update local branch with remote branch changes
```
(Error: failed to push some refs to remote)
git pull --rebase origin CON-3258-deeplinked-notifications-errors-on-page-load
git pull upstream pull/3247/head:CON-3000-topic-follows
```
- Merge main into branch
```
git merge main
```

- Create upstream branch from local branch
```
git checkout CON-3193-uns-temp-plus-api-generate
git push -u upstream CON-3193-uns-temp-plus-api-generate --no-verify
```

Removing the wrong commit instead of undoing changes with a revert commit.
```
1. git checkout my-pull-request-branch
2. git rebase -i HEAD~n // where n is the number of last commits you want to include in interactive rebase.
3. Replace pick with drop for commits you want to discard.
4. git push --force
```

## References
[Create Pull Requests](https://opensource.com/article/19/7/create-pull-request-github)

[Rebase Into a Fork](https://medium.com/@topspinj/how-to-git-rebase-into-a-forked-repo-c9f05e821c8a)

# Git Commands Tutorial

This tutorial covers git reset, revert, and stash commands using hands-on exercises.

## Initial Setup
- Clone or pull the teaching-python repository
- We'll be working with a text file to practice git commands
- Create a file called `practice.md` in the root directory

## git reset
*git reset moves the current branch pointer to a specified commit, allowing you to undo commits locally*

1. pull the `git-reset` branch from the teaching-python repo
2. run `git log --oneline`
3. you'll see this
```bash
0cf12af (HEAD -> git-reset) fourth commit
c173e58 third commit
4cbc74c second commit
599b4bf first git-reset commit
--- remaining commits
```
4. create a branch with your name `git-reset-gaku`, `git-reset-moik` or `git-reset-mariana`
5. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
6. add two lines to `practice.md` with the following text:
```
typescript nextjs
typescript vue
```
7. commit it with the message `frontend 1`
8. add two lines to `practice.md` with the following text:
```
javascript express
php laravel
bug 1
```
9. commit it with the message `backend 1`
10. add two lines to `practice.md` with the following text:
```
ruby on rails
c# .net
bug 2
```
11. commit it with the message `backend 2`
12. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`

### Solving bugs 1
13. there is a bug in the last commit, grab the hash from the `backend 1` commit message, run `git reset <hash>` with the hash
14. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
15. run `git status`, take a screenshot
16. the changes made should be `unstaged (in red)`, delete the line containing `bug 2`, and add a commit with the commit message `backend 2 no bug`
17. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`

### Solving bugs 2
18. there's another bug in the commit from `backend 1`, grab the hash from `frontend 1` and run `git reset <hash>` 
19. the changes will be `unstaged`, delete the lines containing `bug 1` and `bug 2`, and commit it with the message `backend 1 and 2 no bugs`
20. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`

These changes were made locally, so the branch is not in `github`, you can reset to any stage and change them without worrying about changing the commit history 

## git revert
*git revert creates new commits that undo previous commits, safe for shared repositories*

21. push your branch to the repo, now the commit history is in `github`, so we have to be careful when making changes, this is why we use git revert
22. add a line to `practice.md` with your favorite **bocchi the rock** character name, call the commit message `fav bocchi character`
23. push the change 
24. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
25. now we will reset the latest commit, grab the hash from the `backend 1 and 2 no bugs` message, run `git reset <hash>`
26. now run `git status` and take a screenshot, in this commit you will see that you are one commit behind, check github, and you will see the commit on your branch has the **bocchi the rock** character as well
26.5 pull from github to get the latest changes
27. grab the latest hash, and run `git revert <latest-hash>`, this will make another commit at the end of the commit history
28. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
29. now do a `git push`
30. grab the hash from `backend 1 and 2 no bugs` and the hash from `frontend 1` 
31. run `git revert <hash1> <hash2>`, this will revert them both, now run `git push` to put them on github
32. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
33. take a screenshot from github, all the commits should match now, from the revert as well


## git stash
*git stash temporarily saves uncommitted changes so you can switch branches or pull updates*
34. now grab the hash from the `fourth commit` message
35. run `git reset --soft <hash>`
36. run `git stash`, this will save your changes in a local stash stack
37. run `git status`, take a screenshot (should show clean working directory)
38. create a new branch called `fix-bug-1` with `git checkout -b fix-bug-1`
39. add the line `bug fixed` to `practice.md` and commit with message `bug fix applied`
40. run `git log --oneline`, take a screenshot from the last commit until the `first git-reset commit`
41. switch back to your git-reset branch with `git checkout git-reset-[yourname]`
42. run `git stash pop` to restore your stashed changes
43. run `git status`, take a screenshot showing the restored changes

Git stash allows you to temporarily save your uncommitted changes and restore them later, useful when switching branches or pulling updates.


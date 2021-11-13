# git-usage-example

## Resources
- https://docs.google.com/presentation/d/1iVMCaxGJJkq_V-yLiCQHfHWTDuCcNXso5dZswosVHWc/edit?usp=sharing <- presentation
- https://www.atlassian.com/git/tutorials/setting-up-a-repository <- user-friendly git docs
- https://docs.github.com/en <- github source of truth
- https://stackoverflow.com/questions/34519665/how-can-i-move-head-back-to-a-previous-location-detached-head-undo-commits <- useful commands / explanations

## What is Git and GitHub?
- Git : VCS software application
- GitHub : VCS cloud-based repository host, collaboration web application, CI/CD

### Not covering:
- GitHub CLI
- GitHub Desktop

## Authentication

### SSH (Secure Shell)
https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

### PAT (Personal Access Token)
https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token

# CLI

## Creating a new repo

### After creating repo on GitHub
`git init`

### Add README.md to staging
`git add README.md`

### Commit to local repo
`git commit -m "first commit"`

### Switch branch to main (master -> main)
`git branch -M main`

### Set origin to your github repo url
`git remote add origin https://github.com/<your-username>/<your-repo-name>.git`

### Push to repo
`git push -u origin main`

## Updating local master with remote changes from a different branch (origin/dev_frontend)
```
git checkout master
git fetch origin
# you should now have dev_frontend locally
# now we merge dev_frontend into master (our current branch)
git merge dev_frontend 
# assuming you already had the dev_frontend branch and you get merge conflicts
```

# Useful commands
### Check remote repo url
`git remote -v`

### Sets the base of the branch to another commit; useful for cleaning up commit tree in an organization
#### `-i`: interactive mode opens text editor for commit editting
`git rebase -i <commit>`
> EXTRA CARE MUST BE TAKEN WHEN USING THIS; POWERFUL BUT POTENTIALLY DANGEROUS 
> 
> Learn: https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase

### Force push a single branch
`git push origin +main`
> https://stackoverflow.com/questions/5667884/how-to-squash-commits-in-git-after-they-have-been-pushed

# Troubleshooting
### Issue
```
❯ git push origin main
To https://github.com/<username>/<repo>.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://<username>:<string>@github.com/<username>/<repo>.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
### Possible solution
```
# Force push only main to origin/main
❯ git push origin +main
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/<username>/<repo>.git
 + 81716ca...0969728 main -> main (forced update)
```

### Issue
```
❯ git add .
warning: adding embedded git repository: application/csc648-react-frontend
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint: 
hint:   git submodule add <url> application/csc648-react-frontend
hint: 
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint: 
hint:   git rm --cached application/csc648-react-frontend
hint: 
hint: See "git help submodule" for more information.
```

### Possible Solution
```
❯ git submodule add https://github.com/<username>/<repo>.git application/csc648-react-frontend
Adding existing repo at 'application/csc648-react-frontend' to the index
```
> https://git-scm.com/book/en/v2/Git-Tools-Submodules

### Issue
> If you are merging after fetching, but made a mistake with conflict resolution.

### Possible Solution
``` 
# TODO
git merge --abort
```

### Issue
> Need to push immediately in a new branch

### Possible Solution
```
git switch -c <branch-name>
git commit -am "wip <your issue>"
git push origin <branch-name>
```


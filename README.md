# git-usage-example

## What is Git and GitHub?
- Git : VCS software application
- GitHub : VCS cloud-based repository host, collaboration web application, CI/CD

## Create Remote Repository

### In Profile, click "Create Repo"

#### TODO

### Sample configuration
![image](https://user-images.githubusercontent.com/68071075/132845437-3ef32a09-c084-498b-a4f6-0230d2ff4cc7.png)

## Authentication

### SSH (Secure Shell)
https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

### PAT (Personal Access Token)
https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token

## CLI

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
❯ git push origin +main
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/<username>/<repo>.git
 + 81716ca...0969728 main -> main (forced update)
```

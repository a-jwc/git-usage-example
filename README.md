# git-usage-example

## Authentication

### SSH (Secure Shell)
https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

### PAT (Personal Access Token)
https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token

### CLI

## After creating repo
`echo "# csc648-react-frontend" >> README.md`
`git init`

## Add README.md to staging
`git add README.md`

## Commit to local repo
`git commit -m "first commit"`

## Switch branch to main (master -> main)
`git branch -M main`

## Set origin to your github repo url
`git remote add origin https://github.com/<your-username>/<your-repo-name>.git`

## Push to repo
`git push -u origin main`

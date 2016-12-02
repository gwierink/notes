# Notes on `git`
## Create a new repository
```bash
# Create a directory for the repository
mkdir myRepo
cd myRepo
# Initialise a git repository
git init
# Create an initial empty commit
git commit --allow-empty -m "Initial empty commit"
# Add the remote
git remote add origin <remote_address>
# Track branch and push
git push -u origin master
```
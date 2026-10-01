# TestRepo
Hello! this is a test repository made to test multi-user version control when the users share a machine and profile.

## This repo has been cloned to my device. Now I will attempt to push it. If this succeeds, this line will be visible on the github page. Fingers crossed~

## Looks like it succeeded!
- Now it may be possible to use this repo for some thoughts.

## Multiple IDs on one device!
- Typically, we(I) want to SSH with github to use git actions on a repo.
- For that SSH, I typically used `ssh -T git@github.com`, which picked up my personal SSH key (`ArjSheth`) instead of the work one. 
- As a result, even though I was authenticated, I could not push (`ArjSheth` does not have push permissions, `acsheth-ds` does, because the repo belongs only to the latter!)
- I created an SSH config file, where work and personal IDs were separated.
- I will attempt to use them to authenticate, and hope that the correct ID is used. To that end, we only need to change the SSH command to `ssh -T git@git-work`. Let us see if that works.
- This worked! But there is something else! When I decide on which repo is the "remote" one, I should tell git which profile I'm using!

# Final Workflow
- Here is the full set of commonds one should run to activate a repo using the work profile :

```
cd ~/Projects/TestRepo ## that's where my project is, and there's a .git file there, too!
ssh -T git@git-work ## this connects the work profile to github
git remote set-url git@git-work:acsheth-ds/TestRepo.git ## this tells git to use ssh (with the work profile!, see it is invoked here again!) to set the remote repo to acsheth-ds/TestRepo
git add . ## add all changes
git commit -m "hiiii" ## consider this a commit
git push ## push to remote.
```
- Done!

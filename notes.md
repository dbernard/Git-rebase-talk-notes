Basics / Getting Started
========================
* Save starting point
  - "git rev-parse HEAD" prints out the commit id that represents the tip of
  your current branch
  - "git rev-parse HEAD > starting-point.txt"
  - to find the starting point, "git reflog"
    * git keeps a log of changes/updates
  - Gitk is a useful graphical history record
    * pass --date-order to it

* To stop, fix rebase errors:
  - git rebase --abort
  - To reset: "git reset --hard STARTING_POINT_COMMIT_ID"

* Git defaults:
  - IMMEDIATELY update git's push with "git config --global push.default
  upstream"
    * if this isnt set up right you man end up rewinding a branch and losing
    someone's work.

Commit IDs
==========
* Nodes on the revision graph
* Is a SHA1 of various commit data

Ramifications of using SHA1s as IDs
-----------------------------------
* Most editing/fixing/cherry picking of commits changes the ID

Commit modifications
--------------------
* "git commit --amend" modifies HEAD commit with any staged changes
  - Can also be used to fix up a log message
* "git reset" resets current HEAD to the specified state
  - "git reset COMMIT_ID" only resets HEAD
  - "--soft" leaves the index alone
  - "--hard" will reset the working tree and index
    1. useful for dropping recent commits from history
    2. or resetting branch back to original state

Rebasing commits
----------------
* Rebase rewrites history
  - update branch against upstream without merging
  - fix up previous commits
* "git rebase -i" is the primary tool for these tasks
* rebase will use patch IDs to detect commits already on the source branch and
silently drop them
* WARNING: git rebase branch1 branch2 will rebase BRANCH2 onto BRANCH1

# git-topic
git revert | git reset | git restore magic

protecting you from accidental revert.
make your git tree|flow seem like nothign changed.

STATE 1
Let's say you have have a following git history:  
commit 1 -> commit 2 -> commit 3 (HEAD | branch:master)

STATE 2
Now you accidently revert to commit 3:
your git history will look something like this:
commit 1 -> commit 2 -> commit 3 -> commit 4 (revert commit 3) (HEAD | branch: master)

How do go back to STATE 1
One way to do that is add whatever was committed in commit 3 and commit it again which will look something like this:
commit 1 -> commit 2 -> commit 3 -> commit 4 (revert commit 3) -> commit 5 (undo revert commit 3) (HEAD | branch: master)

But a better approach would be the following
Let's go back to STATE 2
commit 1 -> commit 2 -> commit 3 -> commit 4 (revert commit 3) (HEAD | branch: master)
you just accidently reverted.
DON't PANIC add another commit to fix it.
INSTEAD!!
Do a git reset on HEAD^ on while on master branch
this will reset the master and HEAD to it parent commit which will look like
commit 1 -> commit 2 -> commit 3 ( Now you might say, well isn't that what it would do anyway)
Well the answer is yes and no.
It will reset but you had committed in commit 3 won't be committed.
That's when you do git restore.
This will restore all you changes as commited without affecting the branch tree which will look like STATE 1

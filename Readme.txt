git checkout -b <project-Name>-123
Merge Conflicts on Develop Branch
If you have not made changes on your develop branch then it should update and should not return with merge conflicts. If it does, abort the rebase and reset the head back a few commits.

Only run if you get conflicts. This is not a normal part of the workflow.

$ git reset --hard HEAD~4
Performing a Rebase
Now that you have completed work on your feature branch, it's likely new changes have been merged into Acquia's develop.
You'll want to rebase before submitting a PR in order to ensure there are no merge conflicts and that your code works as expected with any new code.

To rebase, simply run the following from your feature branch:

(This assumes the upstream remote is set to git@github.com:acquia-pso/<project-Name>.git)

$ composer export   # export your changed config

$ git add <files>   # add your work
$ git commit -m "<project-Name>-##: This is a proper commit message."   # commit your work

$ git pull -r upstream develop
Watch the console output as you will likely have merge conflicts. Only review the files that say [CONFLICT]. Fix the conflicts, then continue the rebase.

Note: when fixing conflicts, you do git add the files but you do not run a commit. That is done as part of the rebase. Run the commands here exactly as they are.

Assumes you are at the project root, outside of docroot/:

$ git add .
$ git rebase --continue
Continue this until the console output shows as being complete. You can run git status at any time to see if you are in the middle of a rebase.

Once the rebase finishes, run composer import to make sure all is well then you can push your branch to your origin. If you pushed it previously, you will need to force push it.

$ composer import
$ git push origin <project-Name>-123 [--force]
Once the rebase finishes, you can push your branch to your origin. If you pushed it previously, you will need to force push it.

Starting a New Ticket
Before starting a new ticket, checkout your develop branch and ensure it is up-to-date with Acquia's develop. (This assumes the upstream remote is set to git@github.com:git repo)

$ git checkout develop
$ git pull upstream develop
(If you get merge conflicts here, see the Merge Conflicts on Develop Branch section.)

Run composer import so all of your sites sync with the latest develop code.

$ composer import
Now that your codebase and sites are in sync with Acquia'd develop, you can checkout a new branch.

$ git checkout -b -123
Merge Conflicts on Develop Branch
If you have not made changes on your develop branch then it should update and should not return with merge conflicts. If it does, abort the rebase and reset the head back a few commits.

Only run if you get conflicts. This is not a normal part of the workflow.

$ git reset --hard HEAD~4
Performing a Rebase
Now that you have completed work on your feature branch, it's likely new changes have been merged into Acquia's develop. You'll want to rebase before submitting a PR in order to ensure there are no merge conflicts and that your code works as expected with any new code.

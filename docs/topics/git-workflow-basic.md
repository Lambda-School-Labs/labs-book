# Lambda Labs Git Workflow

We have some guidelines while you are working at Lambda Labs that will help
reduce the friction of working in teams. Git is one of our most valued tools
as developers. And as such we have put together the following guide regarding
a workflow that will help keep you organized as well as save your butt from
time to time.

## Objective

### Summary

We will walk through the basic steps of starting and finishing a feature or
task in git and github.com.

### Technologies

- git cli
- github.com Pull Requests

## Getting Started

So you're ready to start work on a new trello card, Lets get started

!!! Info
    Obviously you can't do anything with git until you’ve cloned the team repo.
    After that always make sure you start with a recent copy of the repo.

    ```
    > git checkout master
    > git pull origin master
    ```

So to get started on your first task let’s make a branch. Making sure you are
on the **master** branch, start a new branch with a name that matches or correlates
to the task you are about to begin. The trick here is to think beyond yourself
when naming the branch, stay aligned with your Trello board so you **AND** others
can easily make sense of it.

> git checkout -b [new_branch_name]

![Starting a new branch](/img/git-workflow-basic/git-checkout-1.png "start a new branch")

## Sharing Is Good

Now you have a branch to make all your awesome commits to. However, since you
just had your team in mind while naming the branch, let’s take a minute or two
to do something extra nice for them. Lets us the “Early Pull Strategy” to
allow team members to follow along but not be nagged by our on going commits.
This is done simply by pushing our new branch to the **origin** then create a draft
**PR** in github.

> git push -u origin ${git_current_branch}

or

> git push --set-upstream origin ${git_current_branch}

!!! Info
    The -u (--set-upstream) will save the tracking info for the remote branch
    to your git config. Yay. Now you can easily push your commits to the remote
    branch by git push. Easy.

![push new branch to remote](/img/git-workflow-basic/git-push-1.png "pushing new branch to remote")

The next step is to create a draft PR *(Pull Request)* **after you’ve created
your first commit**. Github created this mode so that notifications will be
turned off by default until you decide to turn off the draft and want to have
the team give you a code review. Back when we traveled uphill both ways we
called this a WIP, putting these initials at the beginning of the title and
we’d have to ignore notifications that had WIP in the title. 🤮 Now we have
it good.

Making sure to use the template to provide a professional description
(seriously copy the description from the trello card, right) summarizing the
actual work in the PR, let’s create a PR using the **staging** branch as the
**base**.

![github draft PR](/img/git-workflow-basic/github-draft-pr.gif "github draft PR")

## We have lift off

And just like that we’re ready to make some awesome software. Committing and
pushing our code regularly are the habits worth having. Before we know it,
we’ll be ready to take the PR out of draft mode.

!!! Tip
    Do your best to be a great team member by making commit messages as
    succinct as possible. They don’t have to be elaborate, just to the
    point.

### One small step

When you feel you’ve completed the task you’ve been working on it’s time to
update the description, take the PR out of draft mode and make it **“ready
for review”**.

![make PR ready for review](/img/git-workflow-basic/github-ready-pr.png "Make PR ready for review")

And just like that, the team will be notified of the PR and they can start
a review and it can be merged.

!!! Tip
    Follow the team policy regarding the number of reviewers required
    before Merging

It’s really good practice to take the time to make comments in the code, even
if they are positive notes on good work your teammate did.

## Using your stage before returning to master

Even though you branched off of master your PR was created using stage as
the base. If there are no conflicts to be resolved choose “Rebase and merge”
from the merge button and lets get our QA started.

![merge into master](/img/git-workflow-basic/github-merge.png "Rebase and merge into master")

If you find yourself with a merge conflict there are a number of ways to solve
it. The github tools are very handy or you can do it locally. When going down
the local path there is a good set of instructions at [https://help.github.
com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request
-merges](https://help.github.com/en/github/collaborating-with-issues-and-pull
-requests/about-pull-request-merges)

Deploy to your staging environment if you don’t have automatic deployment
setup. You and the team can now Qa the app walking through as many scenarios
as possible, making sure there aren’t any unintended reactions from the rest
of the code/system.

## Heading home

When QA has been successful, it’s time to merge to master and deploy. Given
that changes may have occurred due to hotfixes (or team members that have
committed directly on master, you have permission to slap them 🤬)
**rebase** master into your branch.

> git rebase master

Alternatively you can use --interactive if you have commits that you’d like
to **squash**.

> git checkout master
> 
> git merge staging
> 
> git push

And now your code changes are on the master branch, ready to wow users with
your updates. Deploy your code and be ready to support any issues that
arise.

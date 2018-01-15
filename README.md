# :octocat: Git branches

## Why do we need branches?

For a moment, pretend that you are working on a website for a small business. Your boss comes to see you. He asks you to redesign the navigation section of the website. You tell him it will take four days. He nods, trudges off and you begin coding.

At the end of your second day working on the redesign, you receive an email. It's from your boss and he has an urgent request. The business desperately needs to hire a new employee. Your boss wants a short job advertisement placed on the website's home page - right now!

If you had been working on the redesign without using branches, you now have a problem. The code in the website repository contains an uncompleted navigation section that is going to take you another two days to complete. 

How would you handle this situation? Would you carefully try to cut out the uncompleted navigation code and then add it back in later? Or did you make a backup copy of the files prior to working on the navigation section? Perhaps you consider stashing away your navigation commits and downloading a fresh copy of the files from an external repository?

All of these are messy, time consuming and reactive solutions. How could you have avoided getting into this situation in the first place? The answer, as I'm sure you've guessed, is branches.

One of the great benefits of branches is that it allows us as developers the ability to separate code that we are working on from code that is "complete" (or at the very least "currently in use"). Branches may at times seem unnecessary when working on a personal project, but they play a vital role when working with code that is used and accessed by others.

## How to use branches

For this demo we are going to need a new git repository. As a quick refresher, you can do this by creating a new folder, opening your terminal, navigating to that folder and then typing:

```
git init
```

Let's also add something to our repository. Create a text file in the repository, and on the first line of the text file write: 

```
print "Hello from the master branch"
```

Save the file and close it. Let's also commit this change by typing into the terminal:

```
git add -A
git commit -m 'added a new text file'
```

#### Viewing the current branch

We can see a list of all the available branches by typing:

```
git branch
```

You should see that the only branch currently available is the master branch. This is the default branch. The asterix indicates that this is the branch currently in use.

#### Creating a new branch

To create a new branch, simply type `git branch` and then the name of the branch. For our example that means:

```
git branch navigation
```

To switch to this new branch: 

```
git checkout navigation
```

You can complete these two steps in one line by taking advantage of the `-b` flag:

```
git checkout -b navigation
```

At this point we are now using the navigation branch. It is exactly the same as the master branch because we haven't yet added anything to it.

Let's run `git branch` again.

There are now two branches listed: master and navigation, and we are on the navigation branch.

#### Making a change to the navigation branch

Open up the text file and on the second line add:

```
print "Hello from the navigation branch"
```

Let's also commit this change to the navigation branch:

```
git add -A
git commit -m 'added hello from nav branch'
```

Now our navigation branch is ahead of our master branch by 1 commit. Until we tell git to merge our navigation branch back into the master branch, the code in the master branch remains unchanged. 

#### Swapping back to the master branch

We can swap back to the master branch by typing: 

`git checkout master`

At this point, reopen the text file. As expected, in the master branch we can only see the first line of the text file. This makes sense because only the first line was commited to the master branch. 

Close the text file.

#### Merging the master and navigation branches

Finally, let's see how we can merge the two branches together. We are currently in the master branch and we will merge the navigation branch into it.

```
git merge navigation
```

Reopen the text file. Now that the branches have been merged, both lines in the text file should be visible.

<div style="text-align:center">
<img src="images/branches.png?raw=true">
</div>

Congratulations, you now know how to create, swap and merge branches! :tada:
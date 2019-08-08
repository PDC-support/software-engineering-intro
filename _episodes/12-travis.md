---
layout: episode
title: "Exercise: Automatic testing with Travis CI"
teaching: 0
exercises: 20
questions:
  - "How can we implement automatic testing each time we push changes to the repository?"
objectives:
  - "Get comfortable with Travis."
keypoints:
  - "This example was using Python but you can achieve the same automation for Fortran or C or C++."
---

## Type-along: automatizing tests

In this exercise, we will push an example repository to Github and set up
automated testing for it in the cloud.  

We will simulate a collaborative workflow where you find
a bug in someone's repository, make an issue, fix the bug and make a pull
request. We will then see how the repository owner checks the 
automated tests on Github and merges the bugfix change.

### Step 1: Create a new repository on GitHub

- Create a new repository on GitHub with a new name, e.g. `example-testing`
- **Before** you create the repository, select **"Initialize this repository with a README"** (otherwise you try to clone an empty repo)

### Step 2: Enable this repository on [Travis CI](https://travis-ci.org)

On [Travis CI](https://travis-ci.org):

- Use "Sign in with GitHub"
- Enable the newly created repository for testing (you may need to "Sync account" if you do not see it there)


### Step 3: Clone the repository, add sources, commit, and push

Clone the repository.

Add a file `example.py` containing:

```python
def add(a, b):
    return a + b


def test_add():
    assert add(2, 3) == 5
    assert add('space', 'ship') == 'spaceship'


def subtract(a, b):
    return a + b  # <--- fix this in step 8


# uncomment the following test in step 5
#def test_subtract():
#    assert subtract(2, 3) == -1
```

Add a file `.travis.yml` (mind the "." at the beginning) containing:

```yaml
sudo: false

language:
  - python

python:
  - 2.7
  - 3.6

install:
  - pip install pytest

script:
  - pytest --verbose example.py

notifications:
  email: false
```

Test `example.py` with `pytest`.

Then `git add` the two files, commit, and push the changes to GitHub.


### Step 4: Verify that tests have been automatically run

After you have pushed, go to [https://travis-ci.org](https://travis-ci.org) and
verify that Travis automatically picked up the change to the repository and ran
the tests.  It should take less than 1 minute for the test set to run.  Also
click on one of the python versions on Travis to see the full output.

If you forgot to enable Travis before pushing, you may have to tell
Travis to run the test manually.

### Step 5: Add a test which reveals a problem

For this uncomment the code under "step 5", commit, and push.
Verify on Travis that the test suite now fails.


### Step 6: Open an issue on GitHub

Open a new issue about the broken test on GitHub. Issues
provide a very good mechanism to keep track of todo's 
and to communicate with colleagues on code projects.

The idea is now that your colleague will see the 
issue, figure out where the bug is and propose a fix
in a *pull request*, but we will be doing these steps on 
our own.

### Step 7: Create a new `bugfix` branch

Now you know the drill. A good practice is to name branches using your
name/username, e.g. `alice/bugfix`. 

If you want to fix issues in other people's repositories that you don't 
have write access to (or vice versa), you would instead start by 
**forking** the repository to your own GitHub namespace.

### Step 8: Fix the broken test

After you have fixed the code on the bugfix branch,
commit the following commit message "restore function subtract; fixes #1" (assuming that you try to fix issue number 1).

Once the pull request is accepted/merged, this will autoclose the issue since GitHub will recognize the "fixes #1" in the commit message, see also
[closing issues using keywords](https://help.github.com/articles/closing-issues-using-keywords/).

Then push your new branch..


### Step 9: File a pull request

You can do this either by clicking on the button that appears on 
github.com, or by going to the URL provided in the output after the 
`git push` command.

Then before accepting the pull request, observe
how Travis automatically tested the code.


### Step 10: Accept the pull request

Observe how accepting the pull request automatically closes the issue (provided
the commit message contained the correct issue number).

Discuss whether this is a useful feature. And if it is, why do you think is it useful?


### Step 11: Discussion

We discuss together about our experiences with this exercise.

---

## Where to go from here

- On Travis you can also test macOS builds: https://docs.travis-ci.com/user/reference/osx/
- On GitLab use [GitLab CI](https://about.gitlab.com/product/continuous-integration/)
- For Windows builds use [Appveyor](https://www.appveyor.com)

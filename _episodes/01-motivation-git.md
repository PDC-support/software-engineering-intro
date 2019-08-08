---
layout: episode
title: "Motivation for version control"
teaching: 15
exercises: 0
questions:
  - "Why do I need version control?"
  - "What does an online repository look like?"
objectives:
  - "Make sure everyone attending this lesson starts using some form of version control."
  - "See the big picture without going into command line details."
---

# Why version control? 

## The essence of version control

- System which **records snapshots** of a project
- Implements **branching**:
  - you can work on several feature branches and switch between them
  - different people can work on the same code/project without interfering
  - you can experiment with an idea and discard it if it turns out to be a bad idea
- Implements **merging**:
  - tool to merge development branches for you

---

## Why code becomes a disaster without version control

### What is the problem with this kind of "version control"?

Discuss the following directory listing:

```shell
mylib-1.2.4_18.3.07.tgz         somecode_CP_10.8.07.tgz
mylib-1.2.4_27.7.07.tgz         somecode_CP_17.5.07.tgz
mylib-1.2.4_29.4.08.tgz         somecode_CP_23.8.07_final.tgz
mylib-1.2.4_6.10.07.tgz         somecode_CP_24.5.07.tgz
mylib-1.2.5_23.4.08.tgz         somecode_CP_25.5.07.tgz
mylib-1.2.5_25.5.07.tgz         somecode_CP_29.5.07.tgz
mylib-1.2.5_6.6.07.tgz          somecode_CP_30.5.07.tgz
mylib-1.2.5_bexc.tgz            somecode_CP_6.10.07.tgz
mylib-1.2.5_d0.tgz              somecode_CP_6.6.07.tgz
mylib-1.3.0_4.4.08.tgz          somecode_CP_8.6.07.tgz
mylib-1.3.1_4.4.08.tgz          somecode_KT.tgz
mylib-1.3.2_22.4.08.tgz         somecode_PI1_2007.tgz
mylib-1.3.2_4.4.08.tgz          somecode_PI_2007.tgz
mylib-1.3.2_5.4.08.tgz          somecode_PI2_2007.tgz
mylib-1.3.3_1.5.08.tgz          somecode_PI_CP_18.3.07.tgz
mylib-1.3.3_20.5.08.tgz         somecode_11.5.08.tgz
mylib-1.3.3_tstrm_27.6.08.tgz   somecode_15.4.08.tgz
mylib-1.3.3_wk_10.8.08.tgz      somecode_17.6.09_unfinished.tgz
mylib-1.3.3_wk_11.8.08.tgz      somecode_19.7.09.tgz
mylib-1.3.3_wk_13.8.08.tgz      somecode-20.7.09.tgz
...
```

### Roll-back functionality

- Mistakes happen - without recorded snapshots you cannot easily undo mistakes and go back to a working version.


### Branching

- Often you need to work on several issues in one code - without branching this can be messy and confusing.
- You can simulate branching by copying the entire code to multiple places but also this will be messy and confusing.


### Collaboration

- *"I will just finish my work and then you can start with your changes."*.
- *"Can you please send me the latest version?"*.
- *"Where is the latest version?"*.
- *"Which version are you using?"*.
- *"Which version have the authors used in the paper I am trying to reproduce?"*.


### Reproducibility

- How do you indicate which version of your code you have used in your paper?
- When you find a bug, how do you know when precisely this bug was introduced
  (are published results affected? do you need to inform collaborators or users of your code?).

---

## We will use [Git](https://git-scm.com) to record snapshots of our work - why Git?

- Easy to set up - use even by yourself with no server needed.
- Very popular: chances are high you will need to contribute to somebody else's code which is tracked with Git.
- Distributed: good backup, no single point of failure, you can track and clean-up changes offline, simplifies collaboration model for open-source projects.
- Important platforms such as [GitHub](https://github.com), [GitLab](https://gitlab.com), and [Bitbucket](https://bitbucket.org)
  build on top of Git.
- Many platforms build on top of [GitHub](https://github.com).
- Sharing software and data is getting popular and required in research context
  and [GitHub](https://github.com) is a popular platform for sharing software.
- However, *"Git is a four-handle, dual boiler espresso machine, not instant coffee."* [citation needed].
  Git isn't the most user friendly and has its design quirks but deep design
  is great and is definitely the most popular and what you are most likely to
  need to know. So we teach it.

---

# In-browser session

- We will explore and visualize an **existing Git repository** on GitHub and make small changes to it.
- The goal of this episode is not to teach GitHub, but rather to get a glimpse of the wider picture.

---

## Why

- Often our first contact with Git is an existing repository, and it is
  relatively easy to contribute to them.
- The existing repository is often on GitHub (but this demonstration applies
  equally well to GitLab or Bitbucket).
- Most of the Git commands we are about to learn can be done in the browser,
  which is a more intuitive way to get started.
- It's good to see the social aspect to know what our end goal is.

---

## Do not worry

- If you are new to version control, don't focus on what we do. Focus on what comes out of it.
- When browsing a GitHub repository we are looking at **two layers**. Later we
  will explain what is in the Git layer and what is in the GitHub layer.

---

## Demo

We start with an
[existing repository](https://github.com/wikfeldt/example-project)
that contains a couple of commits and two
branches with some easy code.

The project contains several obvious issues (bug in code,
typo in documentation, missing license file, outdated usage example).

- History
  - Explore the [repository](https://github.com/wikfeldt/example-project).
  - Explore the [history](https://github.com/wikfeldt/example-project/commits/master).
  - Browse commit changesets.
  - Note that there are [branches](https://github.com/wikfeldt/example-project/network).
- Reproducibility
  - Find a bug in
    [example.py](https://github.com/wikfeldt/example-project/blob/master/example.py)
    and use annotation to check when precisely the bug got introduced.
  - Discuss the enormous value of the annotation feature.
- Collaboration
  - You can refer to [code portions](https://github.com/wikfeldt/example-project/blob/master/example.py#L18-L19)
    (so much simpler to send a link rather than describe which file to open and where to scroll to).
  - Identify other issues (bug in code, misleading comment, typo in
    documentation, missing license file, outdated usage example).
  - Instructors use the browser to create a branch and make a commit to an
    existing project: Instructors will make a change concurrently, one of them
    (the presenter) will do one change on the screen. Also experienced participants
    can already join.
  - Make a merge request (it's easy in browser, and shows cool stuff).
  - Browse the [network](https://github.com/wikfeldt/example-project/network).
  - See [contributors](https://github.com/wikfeldt/example-project/graphs/contributors).
- Releases
  - Explore the [history](https://github.com/wikfeldt/example-project/commits/master) again.
  - Create a [release](https://github.com/wikfeldt/example-project/releases).

While some of these are GitHub features, it all can be done on other sites, or
by yourself without GitHub at all.

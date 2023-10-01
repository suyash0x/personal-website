---
layout: ../../layouts/MarkdownLayout.astro
title: "How to delete multiple git branches?"
pubDate: 2022-07-01
description: "This is the first post of my new Astro blog."
author: "suyash0x"
tags: ["astro", "blogging", "learning in public"]
---

Efficient Git repository management involves not just creating but also cleaning up local branches. Over time, as developers create branches for various tasks, some become obsolete. Inactive branches clutter the repository, making it harder to navigate and potentially slowing down Git operations. Deleting these inactive branches streamlines the repository, improving its performance and maintainability. It's like decluttering your workspace for a more efficient and organized workflow.

## Problem : Time and Efforts

Manually deleting each inactive branch can be unproductive, especially when dealing with numerous branches. This can be a laborious and error-prone task, which often requires developers to allocate significant effort. Streamlining this process can save valuable time, allowing developers to focus on more critical tasks in the development workflow.

## Solution : CLI tools

1. `grep` : It is a powerful tool for finding and displaying lines of text that match a specified pattern or regular expression.

2. `xargs`: Another command-line utility commonly used in Unix and Unix-like operating systems. It is designed to take input from standard input (stdin) and use it as arguments for another command. xargs is particularly useful when you need to perform the same operation on multiple items or when you want to execute a command with arguments generated from input data.

In most linux distribution these tools are pre-installed.

Replace "pattern" with your current branch and run below command

```
git branch | grep -v "pattern" | xargs git branch -d


// If your current branch is main
git branch | grep -v "main" | xargs git branch -d


// You cam use -D flag to force delete the branch.
// Please pay attention as -D flag deletes the branches, even if they have unmerged changes

git branch | grep -v "main" | xargs git branch -D

```

Here's how it works:

1. `git branch` lists all local branches.

2. `grep -v "main"` uses the -v flag to invert the match, meaning it will exclude the "main" and all other branch names will be passed to `xargs` as standerd input

3. `xargs git branch -d` takes the list of branches from the previous command and deletes each branch with the -d flag, ensuring that only fully merged branches are deleted.

This command is an effective way to clean up your local repository by removing branches that are not needed

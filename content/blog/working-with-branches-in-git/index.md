---
title: "Working with remotes and branches in git"
date: "2020-05-05"
category: "general"
---

![](https://www.cloudsavvyit.com/thumbcache/0/0/5b8ff1fbf94a3ecddbaa8db6b389c09a/p/uploads/2019/10/xe713ed70-1.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.nMHcKVf_oU.png)


**Git** has been an essential tool for software development that offers speed and flexibility to the developers. In this post, I'll be talking a little about working with branches in a version control system like git, and how it helps you manage and track your code easily.

Here is what we are going to do:

* Create a repository in GitHub.
* Clone the repo in the local system.
* Create a branch.
* Merge the branch into master, and delete it.

<br />

This will give you a basic idea of how to deal with things like **merging** that often confuses the hell out of beginners.

So let's get started!

<br />


```js
git clone https://github.com/user/gitTest.git
```

I have cloned a repo named `gitTest` to the desktop that has a single file `index.html`.


Next up, if you type `git remote -v`, you'll see some details about the remote. But what's a remote?

> **remote** is a repository located somewhere over the internet that's-- in our case, on GitHub and `origin` is just the name of that repository. Note that origin is the default standard, and you can name it anything-- if you happen to create a remote by yourself.

> git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called) on the server you cloned from.

<br />


Now that we've cloned the repo, it's time for us to create a branch. Let's call it `feature1`.

```js
git checkout -b feature1
git add feature1.html
git commit -m "add feature1.html"
git push origin feature1
```

We just created another file titled `feature1.html`, added it to the staging area, and commit. After that, we pushed our `feature1` branch to the central git repository, so that we could see the changes on GitHub. Now, as you look under the dropdown on GitHub, you'll see a `feature1` branch besides `master`.


Now, our work is done on this branch, and we want to finally merge it to the master. You could either create a pull request for it to be merged or we can merge it locally. Pull requests are the standard for they are useful in code reviews. But let's merge it locally. For that to happen, we have to go to the branch where we want our local `feature1` branch to be merged into, which is- **master**.

```js
git checkout master
git merge feature1
git push origin master // to view the changes on GitHub
```

Cool! `feature1` has been merged, but we can't see the changes on GitHub yet. In order to achieve that, we have to use `git push origin master` again. Now, you'll see that we have `feature1.html` alongside `index.html` in master.

<br />

After the work is done, we'll delete our branch- both locally and remotely.

```js
git branch -d feature1
git push origin --delete feature1
```
> Note that you can not delete a branch while you're already on it. Make sure to check out.

<br />

Additionally, when multiple people are working in a team, it's important to stay up-to-date with the master. So, after a branch gets merged, it's advisable to use:

```js
git checkout master
git pull origin master
```


This will just update your local repo with the updated master branch.

<br><br>

**Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.**






















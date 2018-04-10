<center><img src="img/geotaster_git_banner.png" alt="banner"/></center>

# Introduction to Version Control and Git

## Aims

### <a href="#section1"> 1. Understand version control</a>

### <a href="#section2"> 2. Setup Git</a>

### <a href="#section3"> 3. Learn a basic Git workflow</a>

### <a href="#section4"> 4. Setup Github</a>

### <a href="#section5"> 5. Explore commit history</a>

### <a href="#section6"> 6. Learn to use multiple branches, merging, pull requests, forks</a>

### <a href="#section7"> 7. Explore the many Git GUIs</a>

### <a href="#section8"> 8. Explore extra services built around Github</a>

### <a href="#section9"> 9. Learn more advanced Git commands</a>

### <a href="#section10"> 10. Understand how to use Git for academic research</a>

This workshop will teach you about the basics of using the Git version control software. In particular it will focus on how it can be used to enrich your academic research, making collaborating with other researchers more efficient and organised.



<a name="section1"></a>

## 1. Understand version control


repository

<a name="section2"></a>

## 2. Setup Git 

You can either follow along through this workshop on a School of GeoSciences Windows machine, a School of GeoSciences remote Linux session, or a personal laptop running Windows, macOS or Linux. Once you are set up with Git, using one of the methods below, everything else in the workshop will be identical across the different operating systems.

### Setup Git with personal Windows

### Setup Git with personal macOS

### Setup Git with personal Linux 

### Setup Git with a GeoSciences Windows machine

### Setup Git with a GeoSciences remote Linux session



<a name="section4"></a>

## 4. Learn a basic Git workflow  


<a name="section3"></a>

## 3. Setup Github 

In order to demonstrate how to back up Git repositories to a remote server and all the advantages that brings, we will be using [Github](https://github.com) as our remote server host. There are many other Git compatible hosting services, such as [BitBucket](https://bitbucket.org), [GitLab](https://about.gitlab.com) and [Codebase](https://www.codebasehq.com), but Github is the most widely used, so we will stick to that for this demo.

Head to [Github](https://github.com) to get started. You should see a registration form on the front page. Pick a username, an email address and password, then sign up. You will then be sent a verification email to complete the registration process.

Once you are registered, head back to [Github](https://github.com) and sign in. Then go to your profile by clicking the dropdown on the right side of the page and clicking "Your profile", as in the image below.

![](img/new_repo.png)

You should then be able to click "Repositories" and the big green "New" button to create a repository to which we will back up the local Git repository we created earlier. Give the repository the same name as the local repository, which in this case is `geotaster_test` and click "Create repository".  

![](img/name_repo.png)

Now you will be able to find the link to the newly created respository, either as an SSH link or an HTTPS link. HTTPS links are more likely to work across all platforms, so copy that link.

![](img/https_link.png)

Then on the command line, navigate to your `geotaster_test` directory and type the following, replacing `<HTTPS_LINK>` with the link you just copied:

```shell
git remote add origin <HTTPS_LINK>
```

This will connect the remote repository on Github to the local repository.

Next, you can sync the master branch (the only branch for now) of the remote repository with the master branch of the local repository by typing:

```shell
git push -u origin master
```

This will backup any committed files in the local repository to the remote repository.

If you want to back up more commits, you can just type:

```shell
git push
```

You don't need to add `-u origin master` after the first time.

Now if you head back to Github, you should see that the `geotaster_test` repository now contains the files that were in the local repository.

<a name="section5"></a>

## 5. Explore commit history

Now we have made a few commits, pulled and then pushed, we can start to see how the Git log is growing. The Git log contains a potted history of all the commits in a repository, complete with the commit messages you wrote earlier on to describe the contents of the commit. To view the Git log, type:

```shell
git log
```

You should see something similar to this:


```shell
commit 99f9ca68788a2344b639bacbd08d0a9b55fa190d (HEAD -> master, origin/master)
Author: johngodlee <johngodlee@gmail.com>
Date:   Tue Apr 3 20:08:23 2018 +0100

    Added OPML file support

commit b57a3cf1cda73e83e8e390647c071d59b0bd939f
Merge: 1c67878 f1ae857
Author: johngodlee <johngodlee@gmail.com>
Date:   Tue Apr 3 20:05:31 2018 +0100

    Merge branch 'master' of github.com:johngodlee/pypodd
```

In this case there are two commits. Let's go through it line by line.

The first line of each commit contains the commit hash (`commit 99f9ca68788a2344b639bacbd08d0a9b55fa190d`), which is a string of numbers and letters which provides a unique identifier for each commit. You can use these commit hashes in more complicated Git commands to point to specific commits

The second line shows the author of that commit, simple enough.

The third line shows the date of the commit, as per the local time of the machine where the commit was made.

The indented line at the bottom contains the commit message written by the user describing the commit.

To see more information on a commit, add flags to the `git log` command, e.g.:

```shell
git log -p -n 2
```

This will show the most recent two commits (`-n 2`), and a breakdown of what has been changed in that commit compared to the previous one.

If you want to compare a specific commit to the most recent version of the respository, you can use the following, substituting the commit hash with your own:

```shell
git diff 1c6787895640eedfda3c1399f3e2171e0761e91 HEAD
```

`HEAD` refers to the most recent commit. 

<a name="section6"></a>

## 6. Learn to use multiple branches, merging, pull requests, forks


<a name="section7"></a>

## 7. Explore the many Git GUIs

Up to now we have done everything in the command line. But there are also many GUI interfaces for Git. Some notable ones include:

Github Desktop

![]({img/.jpg)

Sourcetree

![]({img/.jpg)

GitKraken

![]({img/.jpg)

All of them follow similar designs, but you could argue they make simple Git operations easier, such as visualising branch relationships. On the other hand, it is impossible to perform some of the more complex Git operations using these GUIs, and I maintain that once you get to learn the Git command line interface you will be much more efficient and quick than if you used a GUI.

For now we will stick with the command line, but this is just to let you know that GUI options do exist and you can expore them in your own time.



<a name="section8"></a>

## 8. Explore extra services built around Github 

The Github ecosystem encompasses more than just the basic remote repository server. Github has additional services and integrations that may be very useful for academic research. We won't go into great detail about these services, this is merely to let you know that they exist. Many more services can be found on the [Github marketplace](https://github.com/marketplace), though a good number of them require expensive subscriptions. Below are two integrations which are free an useful for academics.

### Host websites on Github

An increasing number of academics have some sort of professional webpage which they use to advertise projects and blog about their research and what their lab group is doing. Github offers a useful service for hosting webpages for free, called [Github-pages](https://pages.github.com). Github-pages can host HTML pages with CSS and Javascript elements stored in a Github repository. So you can edit your personal page on your local machine, then push it to Github, which triggers the page to be re-built automatically. Additionally, if you're not into writing lots of raw HTML, CSS, and Javascript, Github-pages integrates with a service called [Jekyll](https://jekyllrb.com). Jekyll is a static-site generator that takes a folder of plain text files and compiles them into a website for you, using a template design. The plain text files are written in [Markdown](https://en.wikipedia.org/wiki/Markdown), which is a very easy to read and write markup language. This website is even built using Jekyll! 

Here are some more examples of websites that are hosted using Jekyll and Github-pages:

* [https://ourcodingclub.github.io](https://ourcodingclub.github.io) 
* [https://seosaw.github.io](https://seosaw.github.io)

### Host documentation and books on Github

[Gitbooks](https://legacy.gitbook.com) are a great way of hosting the documentation for a product online, for free, using version control software. Gitbooks use Markdown, just like Github-pages, and link together many Markdown documents using a web interface that provides a table of contents as a way to easily navigate through nested sections. 

Here are a couple of examples of hosted gitbooks:

* [A personal recipe book](https://johngodlee.gitbooks.io/recipes/content/)
* [A guide to using the GeoSciences Linux servers](https://johngodlee.gitbooks.io/geosci_linux_intro_gitbook/content/)



<a name="section9"></a>

## 9. Learn more advanced Git commands 


<a name="section10"></a>

## 10. Understand how to use Git for academic research

Free private repositories for academics.



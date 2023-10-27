readme

The aim of this project is to test how to download data from the open science
framework (OSF) using R and embed that process into code that is kept on GitHub.

We use the R package {osfr} to download the data: https://github.com/ropensci/osfr

## Rather boring background context ##

Git and GitHub are great. But one problem is that large files (> 100mb) are not 
GitHub friendly. This means that our lab is often sticking code on GitHub and not 
tracking folders with big files, such as data, models and figures folders.

The solution to date in our lab involves a hybrid approach. We use version control 
for code and use gitignore to ignore folders with big files. When we're done, we 
stick everything on the OSF and then push the code to GitGub. You might say just 
use the OSF but git provides an essential version control function, so it seems 
smoother that way for many reasons, including most importantly your future self.
That is, when you return to a project, you know that the latest version is the 
latest git version.

At the moment, folks have a choice when they want to grab our code and data. 
1) Go to the OSF and get it all, or 
2) go to Git for most things and then go to 
the OSF for the raw data, model objects or figures (this assumes of course that they 
don't want to run the code locally themselves). 

We want to streamline this process so that folks could get the code from GitHub 
and then directly download the data from the OSF.

The obvious alternative to this workflow is git large file storage: https://git-lfs.com/. 
However, that's not always favourable in my (rather limited) experience because we don't 
really need to track the version history of big data files or big model files. 
So why bother with the headache and the tracking speed slowing down. We want to 
track the code and notes/text, but we only really want large file storage.


## Files and folders ##

**Files**

download_osf_data.Rmd

this file downloads data from one of Rich's OSF projects.

**Folders**

/renv/

I use renv for version control, hence the renv folder.

/data/

download location


## interim conclusion ##

The download script works nicely with osfr and you would only need to add one extra 
chunk of code into your script in order to download the data from the OSF. 
The same is true for downloading large model objects or anything else for that matter. 

So, as a modification to our workflow, it seems pretty trivial. e.g., run your code as
normal from a local folder. Then at the very end, once the raw data is on the
OSF, add a chunk with the relevant OSF download info., so that the raw data can
be downloaded by anyone fro the OSF after downloading your code from GitHub.

**Benefits of this workflow:**

- the code on GitHub is self-contained (or at least much more so than before),
such that there is no need for someone else to interface with the OSF website at all. 
- it keeps git for version control, which is what we want.
- there is minimal disruption to the usual lab workflow.

**Disadvantages of this workflow:**

- there is still reliance on using GitHub and OSF, rather than one or the other.
- it still requires posting large objects to the OSF. (but, given our typical workflow
this is trivial because it usually amounts to a handful of data files and model 
objects. But in other workflows, this could be a massive headache, due to an explosion
of raw data files or other stuff.)


**How does this workflow compare to other solutions, like git large file storage?**

(https://git-lfs.com/)

- of course, git-lfs is more streamlined because that's the whole point of it e.g.,
use git as normal but specify that big files have a special storage status.

- However, as I mention above, I rarely if ever, need to continually track the version 
history of the items that are large, such as raw data, figures and model objects.
So, in my everyday workflow, I just don't need the hassle of making commits with
massive files.


**Final comment** - I'm not a computer scientist or a data scientist so this is all 
most likely a garbled mess of horse sh!t. But it seems to fit our lab's rather 
narrow use-case fairly efficiently.




---
layout: default
---

<img src="https://upload.wikimedia.org/wikipedia/commons/4/4d/Bible_paper.jpg" alt="Photo" hspace="25" width="35%" align="center"/> 
Bible paper by Dave Bullock CC BY 2.0

## Introduction

Ellu took this Command-Line Course to learn more (and again) about working with command-line. 
This course is an introduction to command-line tools for linguists. 
It belongs to the bachelor level courses but was just fine also for Ellu, a language technology master student (nowadays the Linguistic Diversity in the Digital Age program in the Helsinki University).


[Week 1](#week-1) | [Week 2](#week-2) | [Week 3](#week-3) | [Week 4](#week-4) | [Week 5](#week-5) | [Week 6](#week-6) | [Week 7](#week-7) | [Recommendation](#recommendation)

## Week 1

In the first week we learned for example:

* to work in a Unix-like environment
* to use commands from a command-line
* to use text editors
* about binary files
* to make, copy, rename, move and delete files and directories
* to get data from the internet

Example code:

`touch FILENAME`	

where you can replace FILENAME with any file name you like.
If the target file doesn't exist, touch will create an empty file by the given name.
If the file does exist, the command won't change the contents of the file but 
it does update = "touch" the access time of the file which can be useful for example when building programs.

Ellu also needed to install Linux/Ubuntu to her Windows computer so from now on her work is done in Ubuntu-on-Windows. And it was fun! :)

## Week 2

In the second week we learned about users, processes and permissions. We talked about root (admin) user and system directories.
The important thing to learn was to know how to search for the location of the programs and files, for which you can use the `which` command. 
In general it is important to be able to search the exact path of files in your own system(s).

Another useful thing that we learned was to know how to get access (ssh) to remote servers and how to move files between your local computer and a remote server.

Example code:

`scp local_dir/local_file.txt username@taito.csc.fi:/homeappl/home/username`

This command copies your local file to your remote server home directory. After running the command the password for the remote server is required.

## Week 3

The third week's session was about redirecting standard streams, text processing commands and (the wonderful and annoying) regexp :)

Example code:

`cat book.txt | tr -s '\n\r\t ' '\n' | tr -dc "A-Za-z0-9\n'" | sort | uniq -c | sort -nr > book.freq`

With this command you can create a frequency list:

| Command              | Explanation    
| -------------        | -------------  
| cat book.txt         | takes the file
| `|`                  | pipeline (1)  
| tr -s '\n\r\t ' '\n' | puts word/line, no empty lines, -s removes following empty lines 
| tr -dc "A-Za-z0-9\n'"| deletes parts that do NOT include (like punctuation) 
| sort                 | sorts into alphabetical order 
| uniq -c              | counts all the identical lines
| sort -nr             | sorts inverse and numerical order
| > book.freq          | puts the output into a file

(1) "In Unix-like computer operating systems, a pipeline is a sequence of processes chained together by their standard streams, so that the output of each process (stdout) feeds directly as input (stdin) to the next one." (Source: [Wikipedia](https://en.wikipedia.org/wiki/Pipeline_(Unix)))


## Week 4

Week 4 was about environments, bash script files, bash configuration files, and finally we wrote our own .bashrc file and a useful bach script.

FYI: In the .bashrc file you can find prompt settings, PATHs, exports etc. 
Note that .rc files include the configurations of the command-line tools like the color syntax.


Example code:

>     if [ $# -ne 1 ]
>     then 
>        echo "Error! Wrong number of command-line arguments." 
>        echo "Usage: $0 file1"
>        exit 1 
>     fi

Inside a script (.sh) file this tells the user how many command-line parameters ie. files is needed to the script and prints an error code if not correct amount. 


## Week 5

During the fifth week we:

* handled the installations, locally vs. system wide,
* learned to use the command **make**, 
* studied about apt and brew packaging tools, 
* wrote commands to Makefile, 
* learned how to install packages and libraries, 
* learned the difference between compiling a program from source code and installing with a system-level package manager. 

We also learned the purposes of a configure script and how to use Python in Ubuntu shell. The benefits of using a virtual environment was good to learn, too.

And hey, we use **pip** to install **python** modules!

Example code:

>     clean:
>        rm -f results/* data/*no_md.txt

Target _clean_ in a Makefile cleans the interphase files which were in this case created with the make rule:

>     %.no_md.txt: %.txt
>        python3 src/remove_gutenberg_metadata.py $< $@

If the no_md files are wanted to be saved, they can be added to the _all_ target in Makefile.


## Week 6

During the week 6 we set up a GitHub repository and learned how to use git locally. Version control was the main word for this week.

[Setting up a GitHub repo](https://github.com/melaeli/cmdline-course)

We learned to perform various tasks in the repository like creating a remote repo in GitHub, cloning it to the local computer, adding content with git commands and making changes to the source code.

Example code:

1. `git add -A` (all) or `git add filename`

2. `git commit -m ”first commit”`

3. `git pull [repo master]`

4. `git push`

These are the main commands how to push changes from your local repo to GitHub. 
First you add a changed file into the staging area. Then you commit it making it permanent (locally).
Then you check if there are other changes in the GitHub repo by pulling and finally you push your changes to the remote repo in GitHub.

In addition, useful commands are:

| Command         | Explanation
| -------------   | -------------
| git status      | shows the tracked and untracked files
| git branch -a   | shows all branches, -a lists also the remote ones (2) 
| git reset HEAD^ | returns the files from staging area back to working branch
| git checkout    | gets you to the wanted working branch
| git log         | shows all the commits and their ID's
| git clone       | clones a git repository

(2) With the asterix sign * you see the branch on which you are currently working on. 




## Week 7

In the final week we made the final assignment which was...these web pages :) We learned what Jekyll is and how to create a template repository for your GitHub page.

Jekyll is a tool to view quickly the changes you make to your websites on your local computer. 
When you're happy with the result, you can push it to your remote Github repository to make it public.

New skills were learned, too, like writing code in Markdown style and learning to write LaTeX with Overleaf. 
And yes, LaTeX will be used in Ellu's thesis so very useful skill indeed.

Example code:

`[reference-style link][Ellu_s homepage]`

`[Ellu_s homepage]: https://melaeli.github.io/`

This is one of the Markdown ways to create link to a webpage. You can make a reference and use it in many places - and if you change the link address, it automatically corrects the link to all. Convenient!

#### Recommendation

The Command-Line Course was very useful and contained a lot of things.
Ellu can recommend the course to everyone who is even thinking about working with command-line tools or using version control.

[Back to the beginning](#introduction)


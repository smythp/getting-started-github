## Part I: Your first Git repository

So it looks like about half the class has starred the [class GitHub repository](https://github.com/mkgold/texttransform), and so you've probably seen the [tools and resources page)](https://github.com/mkgold/texttransform/blob/master/tools-resources.md). I just added some resource's for RegEx, Python, and NLTK, and I thought it would be useful to write a post that would serve as a quick intro to GitHub and the process of creating a pull request. That way, everyone will be able to edit the resources page, and we will all be able to share (and collaborate on) our work later in the class.

 I know that many of you are old hands at using version control and repositories, but I only started using GitHub relatively recently and so I remember clearly how confusing the platform can be at first. So I'll give the rundown that I would have found useful when I first started with Git.

<h3>Git vs. GitHub</h3>

So what's the difference between Git and GitHub? Git is a tool that is used on your local computer to track and back up files, especially code. It follows the various iterations of a project as "versions"—think of the version numbers of software as it is updated. GitHub, on the other hand, is a website that provides repositories and resources for storing code remotely. There are other version control systems (such as Mercurial) and hosting services (such as BitBucket), but Git and GitHub are currently the most popular. This post will focus mainly on Git (the command line tool), and I'll follow up with a Part II on GitHub (the hosting service).

Git uses its own special language to keep track of versions as they move around, split off, merge together, and so on. 

**commit** - A commit is your basic snapshot of a project and the "version" in "version control. It's used as both a noun and a verb: you commit your changes, or you write a message to go along with your commit. Think of it as a saved state of your project at a certain point in time.

**branch** - Often, when you're working on a new or experimental feature, it makes sense to split off a new copy of your project to work in. This branch functions as a sandbox in which you can work on the new feature without interfering with the main (or "master") branch of development. When you finish your feature, you can merge your branch with the master to have it be part of the main project. Branches are important for understanding pull requests, which will be covered in part II. 

**repository** - A repository is all the files associated with a project plus all the information about its various versions. The version-controlled container for your project. 

### Using Git

If you're on Linux, Git is usually already installed and ready for use in the command line. If you're on Windows, you can download an .exe to install Git [here](http://git-scm.com/download/win). The package for Mac is [here](http://git-scm.com/download/mac). 

The best way to use Git is from the command line. GitHub has created quite usable GUI applications for working with Git, but working with the command line is actually much less confusing in the long run. 

Once you have Git installed, open your terminal (or command prompt in Windows). On Mac, type "terminal" in the finder. On Windows, hit the Windows button and R and the same time and type *cmd* into the dialog box. 

Type *mkdir testrepo* to create a new colder called "testrepo." Now move to the folder by typing *cd testrepo*. Now that we have a folder for our repository, let's create a text file to track with version control. In Mac or Linux, enter this line to create a text file that contains the line "Hello world!"

*echo "Hello world!" > hello.txt*

"Echo" is the command to print text in the console. The ">" command pipes the text from echo into a new text file, hello.txt. If you're on Windows, this command won't work, so simply navigate tot the folder and create a text file using the graphical interface. 

Now that we have our folder and text file, Git is installed and we're ready to start tracking changes. Our folder, *testrepo*, will be our repository, and we will be tracking the changes made to hello.txt. 

### Git commands

Type *git init* from within your *testrepo* folder to start the repository. This creates a .git subfolder inside *testrepo* that will (eventually) keep track of the changes made in your testrepo folder. Don't worry if you don't see it...in most cases the .git subfolder is hidden from the user. 

Let's view the files in our repository. Type *git status* to get a list of the files that have been added to the repository. You should get something like this:

> On branch master
> 
> Initial commit
> 
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
> 
> 	hello.txt

> nothing added to commit but untracked files present (use "git add" to track)

We haven't created or moved to any new branches yet, so we're still on branch master. We've also not created any commits, so we're on our initial commit. Finally, we see that we haven't added our hello.txt to the repository yet. Let's do that. Type *git add .* (including the period) to add all files in the folder to the repository. (You could also type git add hello.txt to add just that file.)

Try *git status* again. Your *hello.txt* should have turned green to indicate that it's now part of the repository. Time to make our first commit.

Type *git commit -m "Added hello.txt"* to commit the files you've added to the repository. This will create a snapshot of our files (in this case, just hello.txt) that we can roll back to later or share with collaborators. Commits are always made with a message that describes what was updated and which can be used to identify that version later. The text after -m in our *git commit* command is that message. You can also just type *git commit* by itself and use the built-in text editor to enter your message.

Let's check out the commits we've made up to this point. Type *git log* to show the version history of the current project. You should see only the initial commit at this stage. 

Now put Git to the test. Make some changes to our hello.txt file, or create an entirely new text-based file (.txt, .py, .org, .md, etc). Go through the steps above to add your changes to the repository. Once again:

1. Make changes to the files in the folder.
2. Use *git add .* to add all files in the folder to the repository. 
3. Use *git status* to make sure that all files have been added correctly. (It's a good idea to use *git status* often to make sure everything is going as planned.)
4. Commit your changes with *git commit -m "Message goes here"*.
5. View your new commit with *git log*.

Finally, let's roll back whatever changes you just made, restoring the project to the state it was in when we made our first commit. (This is a lifesaver when something goes horribly wrong in your code base and you need to restore to a working state.) To return to the state your project was in earlier, first type *git log*. You should see something like this:

> commit cd14d3092db0637137a00c3278dbefee07f018ef
> Author: smythp <patricksmyth01@gmail.com>
> Date:   Sat Feb 7 16:08:44 2015 -0500
> 
>     Added goodbye
> 
> commit 3dfa37eab805905002c46fcb9807ce991b373b5f
> Author: smythp <patricksmyth01@gmail.com>
> Date:   Sat Feb 7 16:03:35 2015 -0500
> 
>     Initial commit

What we need is the commit ID, which is the long number after the word "commit" and before the author information. Copy that line (note that CTRL-C doesn't ususally work in the command line, so right click or use the third mouse button). Paste the ID intot he following command:

*git checkout ID*

Where ID is the commit's ID number. Your folder should now reflect the project's state at the time of the first commit. From this point, you can commit new changes or move back to a later commit using the same method. 

Now your're up and running with Git! But there's still the matter of using GitHub to store the changes you make locally with Git and to collaborate on other projects. In Part II, we'll learned how to push and pull your code to and from GitHub and how to create a pull request so that another user can make use of your changes to their project. 

More on Git:

[A Practical Git introduction](http://mrchlblng.me/2014/09/practical-git-introduction/)  
[Version Control by Example](http://ericsink.com/vcbe/)  
[Git Tutorial](http://www.vogella.com/tutorials/Git/article.html)  
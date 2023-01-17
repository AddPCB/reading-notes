# Version control and remote code  
  
### Git
  
We use a tool called [git](https://en.wikipedia.org/wiki/Git) to track changes in files we create and collaborate on.  
  
Our files need an original copy all versions are derived from, we call this original the 'origin'.  

### Github

One popular service for hosting the master copies of version controlled files is [GitHub](https://enwp.org/Github)  

## Repository  

The store of files linked to a project is called a Repository, we will be keeping our origin repository on Github.

Files, Repositories, GitHub, and Git can be understood as being roughly the same as Library books, Book-cases, The library, and the classification system the library uses to store books.  
  
i.e. We store library books in th right book-cases at the library using the book classification system.  
  
Can be understood as the equivalent to: We store files in the right repositories on GitHub using Git.
  
## Getting started  
  
A git repository can be started from scratch locally, or cloned from an original already on github. 
  
### Creating a local repository.  
  
First, switch to the local directory where your project will be stored:
  
> ```cd ~/projects/reading-notes```
  
Then run the git init command:  
  
> ```git init```
  
You have now generated a .git folder containing the basic classification system for your files.  
  
To begin tracking te contents of this folder for changes:  
  
  > ```git add *.c```
  > ```git add LICENSE```
  > ```git commit -m "initial commit for new project"

Now these files are being tracked.

### Cloning an existing repository.  
  
To copy a repository that is already hosted at GitHub:
  
> ```git clone https://github.com/AddPCB/reading-notes.git```

This makes local copies of all versions of all files for the project.
You can find the clone URL for a given project by clicking the green 'Code' button on your project's github page and copying the URL it displays.
  
## Saving changes and updating the origin.  



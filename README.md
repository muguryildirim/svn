# SVN - Subversion

Subversion is a free/open-source version control system. Subversion manages files and directories over time. A tree of files is placed into a central repository. The repository is much like an ordinary file server, except that it remembers every change ever made to your files and directories. This allows you to recover older versions of your code, or examine the history of how your code was changed. 

## SVN Working Copy 
SVN is a repository that holds all our versioned data, which is also called the SVN server. SVN client program which manages local reflections of portions of that versioned data which is called a working copy. SVN clients can access its repository across networks. Multiple users can access the repository at the same time.

## Installing SVN on Linux
### Debian or Ubuntu 
For Debian-based distributions, you can install SVN using the apt package manager. Open the terminal and run the following command:

`sudo apt install subversion`

### CentOS or Fedora
For RHEL-based distributions, you can install SVN using the yum or dnf package manager. Open the terminal and run the following commands:

`sudo dnf install subversion #For Fedora 22+`
`sudo yum install subversion # For CentOS and pre-Fedora 21 versions`

### Arch Linux
If you are using Arch Linux, you can install SVN with the pacman package manager. Open the terminal and run the following command:

`sudo pacman -S subversion`

Once the SVN installation is complete, you can start working using SVN commands. For example, you can use the svnadmin command to create an SVN repository or use the svn checkout command to check out an existing repository. To create a sample SVN repository:

`svnadmin create /path/to/repository`

To check out an example SVN repository:

`svn checkout URL_of_the_repository`

## SVN Checkout - Create Working Copy
Checkout command is used to download sources from SVN repository to a working copy. If you want to access files from the SVN server, checkout is the first operation you should perform. SVN checkout creates the working copy, from where you can edit, delete, or add content. You can checkout a file, directory, trunk, or whole project. To checkout you should know URL of the components you want to checkout.

`svn checkout/co URL PATH`

- If PATH is omitted, the basename of the URL will be used as the destination. If multiple URLs are given each will be checked out into a subdirectory of PATH, with the name of the subdirectory being the basename of the URL. The following example checks out the directory to the given target directory.

`svn co https://www.exampleurl.com/project/branches/release/data/home/muyildirim/workspace/java` or you can use checkout instead of co

`A    /home/muyildirim/workspace/java/Main.java` 

`A    /home/muyildirim/workspace/java/User.java`

Checked out revision 1.

When you do a checkout, it creates a hidden directory named .svn, which will have the repository details.

## SVN Commit - Save changes to the repository
Whenever you do changes to the working copy, it will not reflect in SVN server. To make the changes permanent, you need to do SVN commit.

`svn ci -m "Log Messages" ` or `svn commit -m "Log Messages"`

## SVN Add - Add a new file to SVN repository
When you want to add a new file (or directory) to the repository you need to use SVN add command. The repository will have the newly added file, only when you do SVN commit. 

- Add the file into SVN repository svn add filename will add the files into SVN repository

`A     svn add Main.java`

- Commit the added file, the added file will not be available in the repository.

`svn ci -m "Adding the file Main.java"`

## SVN Diff - Display the difference
SVN diff displays the differences between your working copy and the copy in the SVN repository. You can find the difference between two revisions and two paths etc.,

`svn diff filename`

`svn -r R1:R2 diff filename`

The example compares the filename@R1 and filename@R2.

`cat /home/muyildirim/workspace/Main.java`

`testing`

`svn diff Main.java`

`Index: Main.java`

`===============================================`

`---         Main.java    (revision 1)`

`+++         Main.java    (working copy)

`@@ -1 +1 @@`

`-testing`

`+tester`

## SVN Status - Status of the working copy
It displays whether the working copy is modified, or it has been added/deleted, or the file is not under revision control, etc.

`svn status PATH` or `svn st PATH`

`svn st /home/muyildirim/workspace`

`M      /home/muyildirim/workspace/Main.java`

- 'M' represents that the item has been modified.

## SVN Log - Display log message 
svn log command shows every committed message.

`svn log`

`r1 | muyildirim | 2023-10-10 20:38:08 +0300 (Date) | 1 line`

`Initial commit`

## SVN Update - Update the working copy
svn update command brings changes from the repository into your working copy. If no revision is specified, it brings your working copy up-to-date with the HEAD revision. Otherwise, it synchronizes the working copy to the revision given in the argument. 

Always before you start working on your working copy, update your working copy. So that all the changes available in the repository will be available in your working copy. i.e. latest changes.

`svn update .` or `svn up .` 

`Updating .`:

`At revision 2.`


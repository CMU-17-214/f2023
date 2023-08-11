# Lab 1: Git and Typescript Tooling

During this course, you will become familiar with several popular and industry-relevant software engineering tools, including an IDE, build systems, and automated style checkers for both Java and TypeScript. In this lab, you will set up your environment and explore some tools for getting started with TypeScript. If you encounter problems along the way, work through problems with others and the TAs during the lab session. 



## Deliverables

- [ ] Locally clone your 214 Git repository and commit and push a change README.md file.
- [ ] Install node.js, TypeScript, and an editor/IDE of your choice. Show that you can compile and run the TypeScript starter code of homework 1 on your machine.
- [ ] Add a library to the project with npm and use it.



## Instructions

### Setting Up Your Repo 

In this and the next lab, we will work with the starter code from homework 1. Each student in 17-214/514 is assigned a GitHub repo per homework assignment. You can create it by following the GitHub Classroom link in the description of Homework 1 on Canvas.

- If you do not have *git* yet, follow the [download instructions](https://git-scm.com/downloads).
- If you do not have a *GitHub* account yet, [create one](https://github.com/). 
- Follow the GitHub classroom link on Canvas/Piazza to create your own GitHub repository with the starter code for homework 1.

**Setting up your Personal Access Token.** Before cloning the repository, you should set up your own personal access token; otherwise, you might get an invalid username or password error. GitHub removes these every year, so even if you have made one in the past, you may need to recreate it. You can follow the [instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) for the general outline on how and where to create a personal access token. Some things to note: 

- You can name it something like 17214f23 or whatever you’d like 
- Set the expiration date to be some time past the end of the semester (e.g. 12/21/23), so that you don’t have to remake it again this semester 
- You can select all of the options if you’d like and read more about what they do [here](https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps). At the very least, make sure you have the **repo, workflow, user, project** scopes selected. 
- **Important:** Once you generate the token, make sure you save it somewhere safe and accessible to you before you leave the page. You will need to use it as your password to log-in and you won’t be able to see it again after leaving the page. 

**Cloning the Repository.** Navigate to your own remote repository, and then click on the green “code” button to copy the URL of this remote repository so that you can clone it. 

We recommend to learn to use *git* on the command line, but you can also the integration in your IDE or [GitHub Desktop](https://desktop.github.com/). To clone the repository from the command line run the following in a terminal: `git clone <The URL of the remote repository>`

This will download the entire repository to your computer. If you are prompted to input your username and password, make sure that you use your personal access token you created above as the password. 

### TypeScript Tools

To run JavaScript applications outside the browser we use Node.js. We write TypeScript code that gets compiled into JavaScript.

**Installing Node.js.** Follow [instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) to install Node.js on your system. We recommend you install it through [nvm](https://github.com/nvm-sh/nvm). If you’re working on a Windows machine, we recommend using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) for installing nvm (and subsequently using WSL for all development in this class). 

The following command will automatically download the installation script and update your environment to install it: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash`  Verify it installed correctly by running: 

`command -v nvm`, which should output nvm.

With nvm installed, you can then install Node.js. Run the command `nvm install node` which should install the latest version of node. Then, run `nvm install-latest-npm` which should install the latest version of npm supported by the node version you installed.

**Package management with npm.** We are using npm for package management:

- The `package.json` file is the configuration file, which lists dependencies and commands
- `npm install` installs all dependencies and puts them in a local directory `node_modules`, which should *not* be committed to version control and is automatically in the search path for imports from JS/TS code
- The `package.json` file has a `dev-dependencies` section, which are development tools not needed at runtime, such as test execution, compilers, and style checkers.
- `npm install -g X` installs package X globally, so not just for the current directory. This is often useful for tools like TypeScript that are installed through npm. `npx` is a useful tool for executing a tool installed locally and hence not otherwise in the path, like `npx tsc`.
- The `package.json` file has a `scripts` section, which is just a way to describe command line instructions that can be easily run with `npm run X` from the command line. These are just convenient shorthands.

*Checkpoint:* Run npm install to install dependencies and tools locally. You can find them in the `node_modules` folder if you are interested. 

**Installing TypeScript.** To install TypeScript run `npm install -g typescript` and afterward `tsc` should be available on your command line. (The project we provide already sets up TypeScript, so `npm install` should already install TypeScript locally).

*Checkpoint:* Confirm that `tsc --version` works in your working directory (or `npx tsc --version` if you installed it only locally).

Run `tsc` to compile the TypeScript code. You can find the output in the dist/ directory.

**Installing VSCode.** VSCode is a popular IDE for TypeScript which we recommend for this course. It works for TypeScript out of the box, no further set up needed. 

Install VSCode following [instructions](https://code.visualstudio.com/) on its homepage or use your operating system's package manager.

*Checkpoint:* You can explore the source files of the cloned repository in the IDE.

**Running a Program in VSCode.** VSCode executes code in the debugger by default. Select “Start debugging” from the menu and confirm to use node.js as the runtime. Note that the program will fail because the debugger does not support command line input, but everything until this part will execute.

If you just want to run the code use a terminal or the built-in terminal in VSCode (“New Terminal”) and run `node dist/index.js` to start the compiled program (or `npm run start` for the preconfigured run script in package.json)

**Style checking with ts-standard.** Linters check your code against a style-guide that specifies some good coding conventions (and sometimes annoying nitpicky things). Linters automates the process of checking for common style flaws such as the use of magic numbers. We preconfigured the project with the (very picky) style checker *ts-standard*. It comes preconfigured in the project with `npm run lint` or just run it with `npx ts-standard` (or just `ts-standard` if you installed the package globally). It has a fix option `npx ts-standard --fix` that will automatically fix many issues, which can be very useful. To integrate ts-standard into vscode, install the *StandardJS* extension and in the settings pick ts-standard as the engine.

*Checkpoint:* Install and configure the StandardJS extension. Introduce some style violation to see what it reports (like extra or missing whitespace). Try to fix it automatically with “npx ts-standard --fix”.

### Adding a Library

Add the library [boxen](https://www.npmjs.com/package/boxen) version 4.2.0 as a dependency. You can either directly edit the `package.json` file to add the library to the list of dependencies and then run `npm install` or you can add it with the npm command `npm install --save boxen@4.2.0`. We use a specific version to avoid a recent compability problem.

Now you can use the library in the source code. You can import it with `import boxen from 'boxen'` and use it with something like `console.log(boxen("Flashcards 1.0"))`

Compile and run your code to see that you successfully used the library.

### Turning in Your Work

For finishing this lab (and all homeworks), you are required to submit your work by pushing changes to your repositories. Throughout the semester you will learn to work with *git*. 

Git is a version control system, which is a fancy way to say that you can take *named* snapshots (i.e. make saves) of your code base with it throughout development, and you can easily revert back to any such saves should something go wrong. Sooner or later you will write code that breaks, and you’d wish to “undo” what you wrote. Without git, you’ll have to figure out what you changed and revert them manually, which is time-costly and error-prone. With git, if you made a save when your code was working, you can revert back to that in one command. You also document your work incrementally for others.

Let's start with the basics:

````bash
git add <filename1> <filename2>
git commit -m "<some message>"
git push
````

**git add** adds files to the staging area, **git commit** saves everything on the staging area along with the given commit message, and **git push** records local commits to the remote repository. After pushing changes you should see them on GitHub.

You can also push changes to your repository using the VSCode UI or use [GitHub Desktop](https://desktop.github.com/). In VSCode, the source control tab (3rd from the top) provides you with an interface where you can stage, commit, and push changes. Clicking the + icon on the file stages it to be committed. Once you have staged all of your files, you can use the text box to add a commit message and press commit. You can then use the UI to push. 





## Appendix: Understanding Git

**Important Git Concepts:**

- **Git Repository:** A git repository is a database of files and their history. On a local computer it will be stored in a .git directory. A repository on your computer is called a *local repository*, and a (typically shared) repository stored somewhere online (e.g. on GitHub) is called a *remote repository*. 
- **Git Commit:** A git commit is a snapshot / save of your git repository. You make a save of your code base by making a git commit. A commit has an ID and a description. It follows another commit. You can later revert back to it. 
- **Working directory:** Code from a git repository can be *checked out* in a directory. This will copy all files from the (typically last) commit from the git database to your directory where you can edit them.
- **Staging Area:** Before you can make a git commit, you need to specify the files you want to include in your commit. In git you do this by *adding* them to the staging area, where you can double check that you are saving what you want. The *commit* command will create a commit of all files staged, but not of other changed files in your working directory.
- **Remote Repository:** A remote repository is like a folder on Google Drive. Just like how you could backup your local files online to Google Drive, you can backup your local Git Repository online as a remote repository. This also enables collaboration: remote repositories are usually shared, when your collaborators *push* (upload) new changes to a shared remote repository, you can *fetch* (download) them to your computer. 
- **Branching:** Git branching allows you to create new development paths for your code. Each path is called a branch. Changes on one branch are independent from changes made on a different branch. Later, if desired, changes from different branches can be merged together. People commonly use branching when implementing new features. They create a new “development branch” and implement new code on it, keeping the default “master branch” clean. If the new code works out, they merge changes from the development branch into the master branch. If it doesn’t work out, they just discard the development branch. This ensures that the master branch always contains working code. 



![img](https://lh4.googleusercontent.com/dGUCNsOeIKcHSjAEj1XARjgulfXrbndajIB8KfpuJjLvOWFIcEH-Ts6R5bsvViIQf0YxUSBxXtURK0iEmaLh8Zy3BXWHLpgbAWFdpVfG_WAQ6INa3mI_pyzpve0GZLN5FpfK7lPJ0X-ps8ckeqF9JQ)

**Useful Git commands:**

- `git clone <remote repository link>` (Clone, i.e. download in entirety a git repository from a remote location and check it out in a local working directory)
- `git pull` (Pull, i.e. download, any new changes from the remote repository not previously downloaded and merge them into your local working directory)
- `git add <filename1> <filename2>...` (Add files to the staging area)
- `git status` (Shows which files have been changed and which files are on the staging area)
- `git commit -m "<some message>"` (Make a commit saving everything on the staging area. The save is tagged with a message <some message>)
- `git log` (List all the commits you’ve made)
- `git push` (Push, i.e. upload, any new commits you made locally to the remote repository)
- `git branch "<branch name>"` (Create a new branch named <branch name>)
- `git checkout <branch name>` (Check out files from the git repository to your local working directory of the branch named <branch name>)

**Useful resources to learn git:**

- [Git cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf) 

- - A concise guide for git commands

- [Pro Git book](https://git-scm.com/book/en/v2)

- [Git Game](https://learngitbranching.js.org/?locale=en_US)


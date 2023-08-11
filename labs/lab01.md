# Lab 1: Git and Typescript Tooling

During this course, you will become familiar with several popular and industry-relevant software engineering tools, including an IDE, build systems, and automated style checkers for both Java and TypeScript. In this lab, you will set up your environment and explore some tools for getting started with TypeScript. If you encounter problems along the way, work through problems with others and the TAs during the lab session. 

## Deliverables

- [ ] Locally clone your 214 Git repository and commit and push a change README.md file.
- [ ] Install node.js, TypeScript, and an editor/IDE of your choice. Show that you can compile and run the TypeScript starter code of homework 1.
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

**Style checking with ts-standard.** We preconfigured the project with the (very picky) style checker *ts-standard*. It comes preconfigured in the project with `npm run lint` or just run it with `npx ts-standard` (or just `ts-standard` if you installed the package globally). It has a fix option `npx ts-standard --fix` that will automatically fix many issues, which can be very useful. To integrate ts-standard into vscode, install the *StandardJS* extension and in the settings pick ts-standard as the engine.

*Checkpoint:* Install and configure the StandardJS extension. Introduce some style violation to see what it reports (like extra or missing whitespace). Try to fix it automatically with “npx ts-standard --fix”.

### Adding a Library

Add the library [boxen](https://www.npmjs.com/package/boxen) version 4.2.0 as a dependency. You can either directly edit the `package.json` file to add the library to the list of dependencies and then run `npm install` or you can add it with the npm command `npm install --save boxen@4.2.0`. We use a specific version to avoid a recent compability problem.

Now you can use the library in the source code. You can import it with `import boxen from 'boxen'` and use it with something like `console.log(boxen("Flashcards 1.0"))`

Compile and run your code to see that you successfully used the library.

### Turning in Your Work

For homework 1, you are required to submit your work by pushing changes to your repository. Throughout the semester you will learn to work with *git*. Let's start with the basics:

````bash
git add <filename1> <filename2>
git commit -m "<some message>"
git push
````

**git add** adds files to the staging area, **git commit** saves everything on the staging area along with the given commit message, and **git push** records local commits to the remote repository. After pushing changes you should see them on GitHub. Additionally, **git status** will show which files have been added to the staging area. 

You can also push changes to your repository using the VSCode UI or use [GitHub Desktop](https://desktop.github.com/). In VSCode, the source control tab (3rd from the top) provides you with an interface where you can stage, commit, and push changes. Clicking the + icon on the file stages it to be committed. Once you have staged all of your files, you can use the text box to add a commit message and press commit. You can then use the UI to push. 

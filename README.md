# GitHub-Actions

- https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions

## Codes & Slides

- You find course resources (code snapshots & slides) on GitHub, in this [repository](https://github.com/nayanrajani/github-actions-course-resources)
- The folders in the Code folder map to the different course sections.

- The folders inside those subfolders (e.g., Code/03 Events/01 Starting Project) represent individual code snapshots - e.g., the starting project code for a course section.

## Section-1: Getting Started

### What is GitHub Actions?

- GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

- GitHub Actions goes beyond just DevOps and lets you run workflows when other events happen in your repository. For example, you can run a workflow to automatically add the appropriate labels whenever someone creates a new issue in your repository.

- GitHub provides Linux, Windows, and macOS virtual machines to run your workflows, or you can host your own self-hosted runners in your own data center or cloud infrastructure.

### The components of GitHub Actions

- You can configure a GitHub Actions workflow to be triggered when an event occurs in your repository, such as a pull request being opened or an issue being created. Your workflow contains one or more jobs which can run in sequential order or in parallel. Each job will run inside its own virtual machine runner, or inside a container, and has one or more steps that either run a script that you define or run an action, which is a reusable extension that can simplify your workflow.

- Workflows
  - A workflow is a configurable automated process that will run one or more jobs. Workflows are defined by a YAML file checked in to your repository and will run when triggered by an event in your repository, or they can be triggered manually, or at a defined schedule.

  - Workflows are defined in the .github/workflows directory in a repository, and a repository can have multiple workflows, each of which can perform a different set of tasks. For example, you can have one workflow to build and test pull requests, another workflow to deploy your application every time a release is created, and still another workflow that adds a label every time someone opens a new issue.

- Events
  - An event is a specific activity in a repository that triggers a workflow run. For example, activity can originate from GitHub when someone creates a pull request, opens an issue, or pushes a commit to a repository. You can also trigger a workflow to run on a schedule, by posting to a REST API, or manually.

- Jobs
  - A job is a set of steps in a workflow that is executed on the same runner. Each step is either a shell script that will be executed, or an action that will be run. Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another. For example, you can have a step that builds your application followed by a step that tests the application that was built.

  - You can configure a job's dependencies with other jobs; by default, jobs have no dependencies and run in parallel with each other. When a job takes a dependency on another job, it will wait for the dependent job to complete before it can run. For example, you may have multiple build jobs for different architectures that have no dependencies, and a packaging job that is dependent on those jobs. The build jobs will run in parallel, and when they have all completed successfully, the packaging job will run.

- Actions
  - An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task. Use an action to help reduce the amount of repetitive code that you write in your workflow files. An action can pull your git repository from GitHub, set up the correct toolchain for your build environment, or set up the authentication to your cloud provider.

- Runners
  - A runner is a server that runs your workflows when they're triggered. Each runner can run a single job at a time. GitHub provides Ubuntu Linux, Microsoft Windows, and macOS runners to run your workflows; each workflow run executes in a fresh, newly-provisioned virtual machine. GitHub also offers larger runners, which are available in larger configurations. For more information, see "About larger runners." If you need a different operating system or require a specific hardware configuration, you can host your own runners. For more information about self-hosted runners, see "Hosting your own runners."

### Git, Github, Github Actions

- Git
  - Git is a free version control system.
  - We can download in windows or linux or any.
  - Git manages sources code changes.
  - Git  allows you to take snapshots of your code like git "commit".
  - Git helps you to manages different version of code with help of "branches".
  - Moving between branches & commits via "checkout"

- GitHub
  - GitHub is a cloud git repository & service provider.
  - you can use it to share and use as a centralise repo storage or code storage instead of storing at local.
  - Push, pull from public and private team management & more.
  - features it has like code management6 & Colaborative development via issues, projects, pull request etc.

- GitHub Actions
  - GitHub offers an automation service for code and code management service.

## Section-2: Git, GitHub crash Course [If you know already skip it]

### Configuring Git

- Download Git from website -> https://git-scm.com/downloads
- restart system and go to cmd and type "git" and hit enter.
- you will get various git commands.
- you can set a username and email address that will be connected to all your code snapshots.
  
  - This can be done via:
    - git config --global user.name "your-username"
    - git config --global user.email "your-email"
    - You can learn more about Git's configuration options here: https://git-scm.com/docs/git-config

- Git Commands
  - These are common Git commands used in various situations:

  - start a working area (see also: git help tutorial)
    - clone     Clone a repository into a new directory
    - init      Create an empty Git repository or reinitialize an existing one

  - work on the current change (see also: git help everyday)
    - add       Add file contents to the index
    - mv        Move or rename a file, a directory, or a symlink
    - restore   Restore working tree files
    - rm        Remove files from the working tree and from the index

  - examine the history and state (see also: git help revisions)
    - bisect    Use binary search to find the commit that introduced a bug
    - diff      Show changes between commits, commit and working tree, etc
    - grep      Print lines matching a pattern
    - log       Show commit logs
    - show      Show various types of objects
    - status    Show the working tree status

  - grow, mark and tweak your common history
    - branch    List, create, or delete branches
    - commit    Record changes to the repository
    - merge     Join two or more development histories together
    - rebase    Reapply commits on top of another base tip
    - reset     Reset current HEAD to the specified state
    - switch    Switch branches
    - tag       Create, list, delete or verify a tag object signed with GPG

  - collaborate (see also: git help workflows)
    - fetch     Download objects and refs from another repository
    - pull      Fetch from and integrate with another repository or a local branch
    - push      Update remote refs along with associated objects

### Getting started with setup

- check out sample-code folder hwere you will find a index.html file which is new and we want it to be pushed to our repo/github.

- go to cmd and navigate to that folder.

- git init 
  - initialize the git and to be managed by git.

- Staging files and creating commits
  - git add index.html (single file)
  - git add index.html xyz.json ok.yml (multiple files)
  - git add subfolder/
  - git add . (stage all files)

  - git status (to check which file is staged and which is not)
  - git commit -m "my code files or new feature xyz" (creating a snapshot with message so that we can remember for what purpose we created this commit)
  - git log to check who has recently committed the changes.

- Multiple Commits & Checking out Snapshots
  - to check more commits
  - add one line in index.html and do stage, commit and then check via git log
  - now if you want to check the previous file do git checkout (id of previous commit)
    - git checkout (id of previous commit from git log)
    - the code will get changed and you will now see older code
    - if you want to go back to the original head of the branch do
      - git switch -
      - git checkout main
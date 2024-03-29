# Version Control With Git <img src="./images/git/logo.png" width="20">

## Basic Concepts:

- **Git != Github**:

- **_Git_** version control system, a software tool for tracking changes made to files over time. Think of it like a record player keeping track of where the needle is on a record, allowing you to jump back and forth between different versions of your code.
- **_Github_** web-based hosting platform for Git repositories. Think of it like a library where you can store your record collection (Git repositories) and easily access and share them with others.

- **Working Directory**

  - It's the main hub of your local project, containing all the files and folders that make up your project at any given point. Think of it as your personal playground where you can make changes, experiment, and collaborate before sharing with others.

- **Staging Area**

  - The bridge between your local working directory and the final commits you make to the remote repository. It's not a physical location but rather a conceptual space where you gather the specific changes you want to include in your next commit.

    Think of it like a staging area for actors before a play - you decide who (changes) will be on stage (in the commit) for the audience (remote repository).

- **Local Repository**

  - a local repository in Git exists solely on your individual computer. It serves as your personal workspace for cloning, making changes to, and managing a Git project. Think of it as your own copy of the project, where you can experiment, develop, and commit changes before pushing them to collaborate with others on a remote server.

- **Remote Repository**
  - A remote repository ,often just called a "remote", is a copy of your Git project hosted on a different server, typically somewhere on the internet. It acts like a central hub where you can push local changes made to your project and pull updates from others who are collaborating on it.

## Commands

- **git clone**
  - Creates a local copy of an existing Git repository stored on a remote server.
  - Example: _git clone https://github.com/wissemmtiri/project.git my-local-project_
- **git init**
  - Initializes a new Git repository in your current directory. This essentially creates a hidden directory called .git where Git stores all the information about your project's history, including versions of your files, commit messages, and branch information.
  - Command: _git init_
- **git add**
  - Selects changes from your working directory to be included in the next commit.
  - Example: _git add main.py_ or _git add ._
- **git commit**
  - Captures the staged changes in the staging area, creating a permanent snapshot of your project's state.
  - Example: _git commit -m "Fixed bug in main function"_
- **git push**
  - Uploads your local commits to a remote repository for sharing and collaboration.
  - Command: _git push_
- **git log**
  - Displays the history of commits made to the repository.
  - Command: _git log_
- **git status**
  - Shows the current state of your working directory and staging area.
  - Command: _git status_

## Setting up a git repo

### _If the remote repository already exists_

1. _git clone https://github.com/wissemmtiri/repo.git project_name_
   1. project_name: name of the local repository
2. _cd project_name_

### _If the code is local and no remote repo is initialized_

1. _git init_
   1. creates a _.git_ directory in the working directory
2. _git add ._
3. _git commit -m "comment"_
4. create a remote repository in the preferred hosting platform (Github)
5. _git remote add origin https://github.com/wissemmtiri/repo.git_
   1. link the local repository with the remote repo
   2. origin: label given to the remote repo to help easily reference.
6. _git branch -M main_
   1. create a branch
7. _git push -u origin main_

## Branches Concept

![feature-branch](./images/git/BranchConcept.png)

- **_Definition_**

  - A lightweight pointer to a specific commit in your repository's history. It serves as a named divergence from the main development line, allowing you to experiment with changes, fix bugs, or develop new features without affecting the main branch. Think of it as a parallel path you can create and work on independently, eventually merging it back into the main road when your changes are ready.

- **_Commands_**

  - _git branch_
    - Lists all existing branches in your local repository.
  - _git pull_
    - Retrieves changes from the remote repository and merges them into your current branch.
  - _git checkout branch-name_

    - Switches your working directory to the specified branch.

  - _git checkout -b branch-name_
    - Creates a new branch locally and switches to it in one step.
  - _git push --set-upstream origin branch-name_
    - Creates and sets an upstream branch for a locally created branch, enabling easy pushing to the remote.

- **_Best Practises_**
  - create a branch for every feature and every bugfix
    - for features: feature/name
    - for bugfixes: bugfix/name

## Pull Requests

- **_Definition_**
  - They act as formal proposals to integrate changes from one branch into another, typically the main branch. This provides a controlled and transparent way to review and discuss potential changes before they become permanent.
- **_Use cases_**
  - Junior Dev, Big Features, Expertise needs
- **_How_**

  - The functionality for creating and reviewing merge requests typically resides within specific platforms or Git hosting services like GitHub, GitLab, or Bitbucket.
    - _It is not recommended to use CLI for pull requests_

  1. **_Ensure your branch is ahead of the main branch_**: This means your branch contains newer commits that aren't present in the main branch.
     1. ![alt text](./images/git/pullReq1.png)
  2. **_Access the pull request functionality on your chosen platform_**
     1. ![alt text](./images/git/image-3.png)
  3. **_Fill out the form_**
     1. ![alt text](./images/git/image-4.png)
  4. **_Your request will be visible to designated reviewers or the wider team, based on your workflow._**
  5. **_Acceptance and merging_**: Once the code is deemed ready, designated reviewers or merge approvers will integrate your changes into the main codebase.

- **_NB_**
  - Merge requests are more than just code integration, they're a collaborative learning and optimization opportunity.

## Deleting Branches

- **_Delete a branch or leave it ?_**
  - If the changes from the branch have been merged into the main branch, the branch is no longer needed and **deleting** it helps declutter your repository.
  - If you are unsure whether you might need the branch again, or the branch is part of a bigger development process, **retain it** until the process is complete.
- **_Delete on the remote repo_**

  - **use GUI:**
    - **_Navigate to the branches section_**
      - ![branches](./images/git/branches.png)
    - **_Locate the branch you want to delete_**
      - ![branch](./images/git/branch.png)
    - **_Click delete branch_**
      - ![deleteBranch](./images/git/delete.png)

- **_NB_**: The local repo will not be notified about the deleted branch. We need to delete it manually.

- **_Delete locally_**
  - _git checkout main/master_
  - _git pull_
  - _git branch -d branch-name_

## Streamline Your Git Workflow: Ditch Merge Commits with Rebasing

- **_Introduction_**

  - Ever feel frustrated by cluttered Git histories with merge commits littering your branches? You're not alone! While merges are essential for integrating changes, they can create messy logs that hinder collaboration and clarity. Enter the power of rebasing, a technique that rewrites history for a cleaner, linear Git experience.

- **_Scenario_**

  - Imagine you're part of a dynamic development team working on a new feature. You diligently craft your feature branch, committing changes for UI design, core functionality, and bug fixes. Meanwhile, the main branch receives valuable updates and bug fixes from your teammates.

- **_Clash of Branches_**

  - Attempting to push your feature directly leads to an error: "remote contains work that you do not have locally."
    - ![alt text](./images/git/push_fail_rebase.png)
  - The traditional solution involves pulling the latest changes and then pushing your work, resulting in two commits: one for your feature and another for the merge.
    - ![alt text](./images/git/double_commit_rebase.png)

- **_Rebase to the Rescue_**
  - Instead of creating merge clutter, consider rebasing your feature branch onto the updated main branch using _git pull -r_. This command:
    - Fetches updates from all remotes (not just the default).
    - Attempts to integrate those updates into your current branch.
  - If integration is seamless, your feature branch seamlessly aligns with the latest changes, resulting in a single, linear history devoid of merge commits.
    - ![alt text](./images/git/rebase_solution.png)

## Merge Conflicts

- **_Introduction_**
  - Merge conflicts arise when distinct modifications are made to the same code lines across different branches. This results in Git identifying conflicting sections, presenting developers with a "battlefield" of conflicting versions. Each version, designated as "theirs" and "yours," requires careful analysis and integration.
- **_Solutions_**
  - **Manual Resolution**: The traditional approach involves meticulous examination of both versions within a text editor. Selecting the optimal components from each and merging them into a single, cohesive line constitutes the core strategy.
  - **Merge Tool Expertise**: Many modern IDEs and Git clients offer sophisticated visual merge tools. These interactive interfaces facilitate intuitive conflict resolution, often presenting side-by-side comparisons and allowing for streamlined merging.
    - ![alt text](./images/git/conflict.png)

## Maintaining Confidentiality with .gitignore

- **_Introduction_**
  - Within the collaborative arena of version control, Git fosters transparency and efficient code sharing. However, safeguarding sensitive information remains paramount. Data such as API keys, database credentials, or local development configurations require stringent protection. This is where the .gitignore file emerges as a crucial security measure.
- **_Avoiding the All-Encompassing_** _git add ._
  - Consider a development team actively pushing and pulling code changes. While the _git add ._ command expedites the process, it can inadvertently include all files in the current directory, potentially sweeping up sensitive information. Sharing such unintended secrets through a remote repository poses significant risks.
- **_The .gitignore File: A Shield for Sensitive Data_**
  - This is where the **.gitignore** file takes center stage. Residing within your project's root directory, this unassuming text file serves as a shield, instructing Git to exclude specific files during the staging and subsequent commit phases. Think of it as a gatekeeper, meticulously ensuring only authorized files gain access to the shared repository, while denying entry to those containing confidential information.
- **_Protecting Common Assets_**
  - **Environment files**
  - **API Keys and Credentials**
  - **Locally Generated Data**: Temporary files, cached data, or test artifacts
- **_The Guardian needs to be protected_**
  - While leveraging the .gitignore file is crucial for safeguarding sensitive information in your Git repository, a critical safeguard often goes overlooked: protecting the .gitignore itself. Unintentionally adding it to the repository can have unintended consequences.
  - **_Note_**
    - .gitignore only affects files that haven't yet been committed.
      - Solution: force git to stop tracking the commited files. (_git rm -r(if folder) --cached filename/foldername_)

## Stashing Progress: Ensuring Agile Git Workflows

- **_Introduction_**
  - Within the dynamic environment of version control, maintaining flexibility and control over ongoing changes proves crucial. The git stash command emerges as a valuable tool, facilitating the temporary storage and subsequent retrieval of work-in-progress modifications, fostering enhanced workflow agility.
- **_Use_**
  - _**git stash**_: This fundamental command triggers the storage of current changes. Imagine meticulously organizing your manuscript for temporary safekeeping.
  - **_git stash pop_**: When ready to resume development, this command retrieves the stashed changes and integrates them back into your working directory.
- Beyond fundamental usage, git stash offers compelling benefits for diverse scenarios:

- **_Use Cases_**
  - **Hypothesis Testing**:
    - Suspecting a recent change might trigger an issue? Stash your current work, revert to an earlier commit, and conduct testing without your modifications. If the problem persists, git stash pop effortlessly reintroduces your work for further debugging.
  - **Branch Switching Efficiency**:
    - Multitasking between features? Stash your changes on one branch, seamlessly switch to another, and make progress there. Upon returning, git stash pop effortlessly reintegrates your stashed modifications.

## Navigating Git History

- **_Introduction_**
  - Git empowers us to explore the intricate paths of project history, providing invaluable insights into past decisions, debugging intricacies, and facilitating reversions to previous states. This guide presents two essential commands that unlock this power:
    - _git log_
      - ![alt text](./images/git/gitlog.png)
    - _git checkout_
- **_How to use ?_**
  - While _git log_ allows observation, _git checkout_ serves as your temporal portal. This command empowers you to precisely switch your working directory to a specific point in time, represented by a commit SHA, branch name, or tag.
    - **Example**:
      - _git checkout 6d842319062d476c06e7877321159f2fbca980a2_
        - Teleports you to the commit with the specified SHA, granting immediate access to that specific state.
      - _git checkout branch-name_
        - switches you to the designated branch, effectively traveling to the latest commit on that branch.

## Modifying and Reverting Git Commits

- **_Introduction_**
  - Git empowers developers with several commands to undo, modify, and revert edits, ensuring optimal code cleanliness and collaborative harmony.
- **_How to do it ?_**
  - _git reset --hard/soft HEAD~n_
  - The git reset command allows you to move the HEAD pointer back in history, essentially undoing specific commits. It offers two primary modes:
    - **--hard**: This operation permanently discards all changes introduced in the targeted commit(s). Use it with caution, as lost changes are unrecoverable
    - **--soft** (default): This mode undoes the commit metadata (author, message, timestamp) but preserves the actual file changes. It's ideal for updating commit messages or making minor corrections without losing valuable code modifications.
  - The **HEAD~n** syntax specifies the number of commits to move back within history (e.g., HEAD~2 moves back two commits).
- **_Updating the Last Commit with git commit --amend_**

  - This command allows you to directly modify the contents of the last local commit, incorporating changes and updating the message without creating a new commit history entry.

- **Considerations for Remote Repositories**
  - Caution! Directly modifying history on a remote repository can create issues for collaborators. If you've already pushed a problematic commit:
    - **Local Undo**: Use **_git reset --hard HEAD~1_** to undo the commit locally.
    - **Force Push** (Use with Caution): While generally discouraged due to potential conflicts, **_git push --force_** forcefully updates the remote repository with your local changes. **Only use this option when absolutely necessary and after clear communication with collaborators.**
    - **OR:**
      - **_git revert_**: This safer alternative creates a new commit that reverses the changes introduced in the problematic commit. It doesn't remove the original commit but provides a clear audit trail of the corrective action.

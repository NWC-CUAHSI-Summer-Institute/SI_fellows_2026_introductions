# Summer Institute 2026 - GitHub Training

Description: A training repository for introducing basic git collaboration workflows.

Welcome to the National Water Center Innovators Program Summer Institute GitHub training repository! This repository is designed to help participants of the Summer Institute get comfortable with using GitHub, a tool for collaborative software development and data science.

#### Training Objective

The goal of this training is to familiarize you with the basics of GitHub. You will learn how to clone a repository, make edits, and commit changes. This exercise is intended to prepare you for contributing to collaborative projects during the Summer Institute, ensuring that all code and findings are public and reproducible.

# Getting Started

## 0. Prerequisites

- We will be using the CIROH 2i2c cloud compute platform during the Summer Institute bootcamp. You can access that platform here: https://ciroh.awi.2i2c.cloud/. Log in using your GitHub username.

> If you do not have an account:
>
> 1.  Visit [the CIROH Hub Infrastructure Access website](https://docs.ciroh.org/docs/services/access/).
> 2.  Click on "Cloud Infrastructure Request Form” under “CIROH-2i2c JupyterHub”.

- You probably already have a GitHub account, but in case you don’t, you can sign up [here](https://github.com).

## 1. Log into CIROH AWI 2i2c JupyterHub

For the Summer Institute bootcamp, we’ll use the 2i2c AWI JupyterHub cloud computing platform hosted by The Alabama Water Institute. The administrators have already set this up for you, so should already have access to this platform.

1. Go to https://ciroh.awi.2i2c.cloud/hub/login and log in with your GitHub username
2. Choose Server Option – Small machine with image: “New Pangeo Notebook base image 2024.04.08” and click the _Start_ button at the bottom of the page. It might take a minute or two to start up. When it starts, it will open up a bash terminal on the right, and a file explorer on the left.
   ![2i2c Small Machine](screenshots/2i2c_small.png)

   > _**Quick Trick in the JupyterHub**_
   >
   > 1. Click on "View" and toggle on "Show hidden files"
   >    ![Show Hidden Files](screenshots/show_hidden.png)

## 2. Generating an SSH Key for Interacting with GitHub

The first thing we need to do is to set up our SSH Key to make changes to our _remote_ GitHub Repo.

1. **Open a Terminal Window**:  
   Once you launch the 2i2c JupyterHub, if a terminal windown isn't already open, open the _Launcher_ by clicking the <span style="color:#0F52BA">blue rectangle with a "+" sign</span>. There you can select _Terminal_. The following commands should be entered into this terminal.

2. **Configure Git**:

   First, tell Git who you are. Replace the examples below with your own information:

   ```
   git config --global user.name "Your Name"
   git config --global user.email "your_email@example.com" # this should be the email associated with GitHub
   ```

   Verify your settings:

   ```
   git config --global --list
   ```

   You should see something similar to:

   `user.name=Your Name`  
   `user.email=your_email@example.com`

3. **Create an SSH Key**

   SSH keys allow GitHub to recognize your JupyterHub environment securely. To generate a new SSH key, run the following in the Terminal:

   ```
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   When prompted to "`Enter file in which to save the key`", press _**Enter**_ to accept the default location, which in the JupyterHub is `/home/jovyan/.ssh/id_ed25519`

   When prompted to "`Enter passphrase (empty for no passphrase)`":
   - Press Enter to leave it blank (this is fine for this workshop), OR
   - Create a passphrase for additional security

   You should see output similar to:

   ```
   Your identification has been saved in /home/jovyan/.ssh/id_ed25519

   Your public key has been saved in /home/jovyan/.ssh/id_ed25519.pub
   ```

## 3. Create a new SSH Authentication Key on Github:

1. **Copy your SSH key from 2i2c JupyterHub**:  
    Before heading over to https://www.github.com, you'll need to copy your SSH key. Print your public key by running:

   ```
   cat /home/jovyan/.ssh/id_ed25519.pub
   ```

   The output will look something like:

   `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAI... your_email@example.com`

   Copy the entire line to your clipboard, making sure to copy everything beginning with `ssh-ed25519` and ending with your email address.

2. **Add the SSH Key to Github**:  
   Open GitHub on your web browser and do the following:
   - sign in to [GitHub](https://www.github.com)
   - click your profile picture (upper right)
   - select _Settings_
   - in the left sidebar, select _SSH and GPG keys_ (left side menu)
   - click _New SSH key_ button

   This will take you to the _**Add new SSH Key**_ form:
   ![SSH Key Form](screenshots/gh_ssh_key.png)

   In the SSH Key form, edit the:
   - _Title_ - fill in a descriptive title (e.g., "CIROH JupyterHub")
   - _Key Type_ - leave the key type as "Authentication Key"
   - _Key_ - Paste your SSH key you copied from the 2i2c terminal.

   Click the _Add SSH Key_ button and you're set! GitHub may ask you to confirm your password or complete two-factor authentication.

## 3. Clone the Repository

1. Go to the GitHub site for our repository: `NWC-CUAHSI-Summer-Institute/SI_fellows_2026_introductions`, and click on the green button and copy the **SSH** address.
   ![Copy Repo SSH](screenshots/copy_repo_ssh.png)
2. In Jupyter environment, type:

   ```
   git clone git@github.com:NWC-CUAHSI-Summer-Institute/SI_fellows_2026_introductions.git
   ```

   Change directories into the _SI_fellows_2026_introductions_ directory:

   ```
   cd SI_fellows_2026_introductions
   ```

## 4. Make a New Branch

1. Understand the difference between forks and branches: [Fork vs Branch](https://www.ssw.com.au/rules/fork-vs-branch/).
2. Create a new branch:

   ```
   git checkout -b [your_branch_name]
   ```

   List all of the branches, for fun:

   ```
   git branch -a
   ```

## 5. Make a New Text File and Add Your Information to it

1. Copy the `introductions.txt` file in Jupyter Lab:

```
cd SI_fellow_profiles

cp introductions.txt <yourName_profile.txt>
```

2. Open the new file, add a few notes about yourself, and save the file.

## 8. Commit Your Changes

1. Stage and commit your changes:

```
git add introductions.txt
git commit -m "Added my profile file"
```

## 9. Push Your Changes

1. Push your branch to the remote repository:

```
git push --set-upstream origin [your_branch_name]
```

## 10. Create a Pull Request

1. Go to the GitHub repository website.
2. Click the “Compare & pull request” button.
   ![Pull Request 1](screenshots/pull_request1.png)
3. Fill in the pull request details and submit.
   ![Pull Request 2](screenshots/pull_request2.png)

By following these steps, you’ll contribute your changes to the repository and learn the basics of GitHub workflows.

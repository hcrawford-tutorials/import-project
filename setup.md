# Getting Started

## Step 1: Create a GitHub Codespace for the warm-up exercises

- From the homepage of this repo, click on the green `Code` button and choose the `Codespaces` tab and click on the green `Create codespace on main` button:

The browser-based VSCode window will open automatically. Your Codespace is built and ready to use when you can see the lab files in the Code Explorer window (left) and have a prompt in the terminal window (bottom).

## Step 2: Use your Codespace to make a fork of the original repo

- Add a directory called `animal-classification` to your workspace.
- Add and commit the change you just made. At this point, the Codespace will notify you that you don't have push access to the original repo.
- Type `Y` to proceed. GitHub will create a fork of the original repo within your personal org.
- Push your change to your newly forked lab repo!

## Step 3: Browse the codebase
Take a few minutes to explore the codebase and familiarize yourself with using browser-based VSCode:
- In the terminal window, start a Python REPL (Python 3.14 is installed) and try out a few Python commands if you like!

- If you're not familiar with VSCode:
	- explore the directory structure and the files that are contained within it
	- check out the different icons and menu options
	- check out the tabs at the top of the integrated terminal (Problems, Output, Debug Console and Terminal)
	- Try running the code under the debugger. Setting breakpoints and using the Debug Console to run code can be helpful when understanding the flow of control with import statements and the errors they can throw
		- note that running the `run-exercises.py` script will fail - part of the lab is fixing this exception

- Close the AI agent window that opens automatically. We won't be using AI for this tutorial, although it may be helpful to use it in Ask mode to explain things to you as you work through the tutorial exercises

## Working with GitHub Codespaces
__You do not need to pay for anything to work with this tutorial.__

GitHub Codespaces provides an easy to use and set up environment for writing code that is hosted in the cloud. Codespaces can be created from any template, branch or commit in a repository. Codespaces use two types of compute resources: CPU time and storage space. Each free GitHub account has a monthly quota of these compute resources without providing payment details. At the time of writing, these quotas are as follows:

| Account Plan                      | Storage Per Month | Compute time per month |
|-----------------------------------|-------------------|------------------------|
| GitHub Free for personal accounts | 15 GB per month   | 120 hours              |
| GitHub Pro                        | 20 GB per month   | 180 hours              |

Source: GitHub Codespaces billing

Compute time is used when a Codespace is actively running. Storage is used as long as the Codespace exists, even if it's not running. To make the most of your monthly quotas, remember to stop the Codespace when you're not using it (i.e., at the end of this tutorial) and delete it when you don't intend to use it for a while. Deleting the Codespace does not affect the forked repo created when you first pushed changes. This means that you can delete a Codespace and recreate it from the forked repo whenever you want to work with the repo again. Make sure you commit and push your changes so you don't lose them when you delete the Codespace.

### To stop a Codespace:
1. Click the hamburger menu at the left of your GitHub repo menu (not the VSCode browser window)
1. Click Codespaces
1. From the list of Codespaces, find the one you want to stop
1. In the Your Codespaces section, click on the three dots menu to the right of the codespace and click Stop Codespace

This Codespace can be restarted from the same place simply by clicking on it in the Your Codespaces section.

### To delete a Codespace:
1. Commit and push any changes you've made that you want to keep
	- If you delete a Codespace with un-pushed changes, they will be lost
1. Click the hamburger menu at the left of your GitHub repo menu (not the VSCode browser window)
1. Click Codespaces
1. In the Your Codespaces section, click on the three dots menu to the right of the codespace and click Delete

For more information on GitHub Codespaces, check out the [documentation](https://docs.github.com/en/codespaces).

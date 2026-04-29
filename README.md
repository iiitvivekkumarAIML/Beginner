# Beginner
Github for Beginner

Installing Git

One-time setup — do this once on your machine

WINDOWS
# Download from git-scm.com/download/win
# Then verify in Command Prompt or PowerShell:
PS> git --version
git version 2.44.0.windows.1
MAC
$ brew install git
# or: xcode-select --install
$ git --version
git version 2.44.0


LINUX / WSL (Ubuntu)
$ sudo apt-get install git
$ git --version
git version 2.43.0
FIRST-TIME SETUP — tell Git who you are
$ git config --global user.name "Your Name"
$ git config --global user.email "you@email.com"
# This name appears on all your commits

Git config settings guide — view, understand, and set all important Git configuration options
Step 1 — view all your current settings
Run this right now to see everything Git knows about you
$ git config --list
user.name=Your Name
user.email=you@email.com
core.editor=vim
core.autocrlf=false
init.defaultbranch=main
color.ui=auto
# ...and more
# See where each setting comes from (file path shown)
$ git config --list --show-origin
file:/home/user/.gitconfig user.name=Your Name
file:/home/user/.gitconfig user.email=you@email.com
Step 2 — the 3 config levels (scope)
Settings can live in 3 places — lower overrides higher
--system
/etc/gitconfig
Applies to every user on this computer. Rarely edited.
--global
~/.gitconfig
Applies to all your projects. This is where you set name, email, editor.
--local
.git/config
Applies only to one project. Overrides global. Useful for work vs personal.
# Check only global settings (most common)
$ git config --global --list

# Check a single value
$ git config user.email
you@email.com
Step 3 — what every setting means
The settings that matter for a data scientist
user.name
Your display name on commits. This appears in git log and on GitHub. Set it to your real name or handle. required
user.email
The email linked to your commits. Must match your GitHub account email so commits are linked to your profile. required
init.defaultbranch
Name of the first branch when you run git init. Set to main — GitHub's default is also main, so they will match.
core.editor
Text editor Git opens for writing long commit messages. Default is vim (confusing for beginners). Change to nano or VS Code.
core.autocrlf
Line endings — how Git handles Windows vs Mac/Linux newlines. Set to true on Windows, input on Mac/Linux. Prevents noisy diffs in notebooks.
color.ui
Coloured terminal output. auto means Git adds colour when displaying to a terminal. Leave this as-is.
alias.*
Custom shortcuts for long commands. optional You create these yourself — e.g. git st instead of git status.
credential.helper
How Git stores your GitHub password / token. Set to store or osxkeychain so you don't re-enter credentials every push.
Step 4 — recommended setup for data scientists
Run these once after installing Git
# Identity (required)
$ git config --global user.name "Your Name"
$ git config --global user.email "you@email.com"

# Use main as default branch name (matches GitHub)
$ git config --global init.defaultbranch main

# Use VS Code as editor instead of vim
$ git config --global core.editor "code --wait"

# Line endings: Windows
$ git config --global core.autocrlf true
# Line endings: Mac / Linux
$ git config --global core.autocrlf input

# Useful shortcuts (aliases)
$ git config --global alias.st status
$ git config --global alias.lg "log --oneline --graph"

# Now you can use:
$ git st ← same as git status
$ git lg ← pretty commit graph
# Verify everything looks right
$ git config --global --list
user.name=Your Name
user.email=you@email.com
init.defaultbranch=main
core.editor=code --wait
alias.st=status
alias.lg=log --oneline --graph

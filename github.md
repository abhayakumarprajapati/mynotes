

git blame src/components/Form.tsx

git remote set-url origin git@github.com:your-username/your-repo.git => **set https to ssh**

git conflict pull.rebase false = > in  ec2 console


ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# start ssh agent
eval "$(ssh-agent -s)"
# edit ssh config file
nano ~/.ssh/config
# Personal GitHub account
Host github.com-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal

# Company GitHub account
Host github.com-company
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

# Add your SSH keys to the ssh-agent

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_personal
ssh-add ~/.ssh/id_ed25519

# get key
cat ~/.ssh/id_ed25519.pub

# Update your project’s Git remote URL (if needed)

git remote set-url origin git@github.com-personal:abhayakumarprajapati/dsaproblems.git
git remote -v

origin  git@github.com-personal:abhayakumarprajapati/dsaproblems.git (fetch)
origin  git@github.com-personal:abhayakumarprajapati/dsaproblems.git (push)

  
cat ~/.ssh/id_rsa.pub

**Test SSH Connection to GitHub** => ssh -T git@github.com

create env file => nano .env

# by mistake if you make a commit with other user name or you want to delete last commit
git reset --hard HEAD~1
git push --force


# Here's exactly what to do to merge your changes from developer-ab into main after pushing.

git checkout main
git pull origin main(optional)
git merge developer-ab
git push origin main

# in my laptop i use two accounts of github so i want to see keys


Step 1: List All SSH Keys on Your Laptop
Open your terminal and run:


ls ~/.ssh

This will list all your SSH-related files, such as:


id_rsa        id_rsa.pub
id_work       id_work.pub
id_personal   id_personal.pub
config

Files without .pub are private keys

Files with .pub are public keys

Step 2: View Contents of Public Keys
To see the public key of each account:

cat ~/.ssh/id_personal.pub => ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AIIw1ZbEJ84510vs7Ae1wzEAnO2IMPK9BiIn5DDDORPKwabhayprajapati1000@gmail.com

Copy the output and make sure you've added it to the correct GitHub account:

Go to GitHub → Settings → SSH and GPG Keys → New SSH Key

Step 3: Setup SSH Config File (if using multiple accounts)

Edit or create the ~/.ssh/config file:

notepad $env:USERPROFILE\.ssh\config

Add this:

# Personal GitHub
Host github.com-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_personal

# Work GitHub
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_work

Step 4: Use Different GitHub Accounts in Git
In your project folder, configure Git to use the correct user:


git config user.name "Your Name"
git config user.email "your-personal-email@example.com"

Also, set remote to use correct host alias:

git remote set-url origin git@github.com-personal:yourusername/repo.git


Step 5: Test Your Connection

To test if the key is working:

ssh -T git@github.com-personal
ssh -T git@github.com-work

You should see:


Hi yourusername! You've successfully authenticated...



##### Steps to Generate New SSH Keys on Windows for GitHub

Step 1: Open Git Bash
If you don’t have Git Bash, install Git from https://git-scm.com — it includes Git Bash.

Open Git Bash (not CMD or PowerShell).

 Step 2: Generate a New SSH Key

 ssh-keygen -t rsa -b 4096 -C "your-email@example.com"

 When prompted:
It will ask where to save the key:


Enter file in which to save the key (/c/Users/YourName/.ssh/id_rsa):

If you're creating keys for multiple accounts:

Use something like: /c/Users/YourName/.ssh/id_personal or /c/Users/YourName/.ssh/id_work

Press Enter, and optionally enter a passphrase (you can leave it empty if you prefer).

Step 3: Add the SSH Key to the SSH Agent
Start the ssh-agent:


eval "$(ssh-agent -s)"

Add your key to the agent:


ssh-add ~/.ssh/id_personal
Replace id_personal with your key file name (id_work, etc.) if different.

Step 4: Add the SSH Public Key to GitHub
Get the public key content:


cat ~/.ssh/id_personal.pub

Copy the output (starts with ssh-rsa or ecdsa or ssh-ed25519).

Go to GitHub → Settings → SSH and GPG Keys → New SSH key

Title: "Personal Laptop" or "Work Laptop"
Key: Paste the copied key.

Do this for each account with their respective key.

Step 5: Configure SSH to Use Different Keys
Edit your SSH config file:


notepad ~/.ssh/config

Paste this (adjust paths and names as needed):

# Personal GitHub account
Host github.com-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_personal

# Work GitHub account
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_work

  Step 6: Clone Repos Using the Correct Host

  When cloning a repo:

  # Personal account
git clone git@github.com-personal:yourusername/your-repo.git

# Work account
git clone git@github.com-work:yourworkusername/your-repo.git

Step 7: Set Git Config for Each Repo

Inside the project directory:

git config user.name "Your Name"
git config user.email "your-email@example.com"

Step 8: Test Connection

ssh -T git@github.com-personal
ssh -T git@github.com-work

You should see:

Hi yourusername! You've successfully authenticated...
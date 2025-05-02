

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

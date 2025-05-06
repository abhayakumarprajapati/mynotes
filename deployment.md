sudo apt install-ynginx

sudo nginx -s reload

sudo nano /etc/nginx/sites-enabled/default => ctrl+o  enter ctrl+x



sudo apt install -y certbot python3-certbot-nginx
sudo certbot --nginx -d www.ytdemo.com

sudo certbot renew --dry-new

git clone git@github.com:abhayakumarprajapati/Redis-Tutorial.git

# after taking pull  in ec2 ubuntu 
pm2 restart all => to restart your project so that changes reflected in live

# Restart Nginx (if config changed):
sudo nginx -t => check nginx syntax is ok

sudo nginx -s reload
sudo systemctl restart nginx

# in ece instance first time when you take pull of nextjs or reactjs then :

npm install
npm run build

pm2 start npm --name "next-app" -- start => for first time

pm2 restart all=> use this after 

# check app running

pm2 list

# How i login to putty and winscp using ip address of ec2 aws

open putty=> enter public ipv4 address from aws in ip => click on ssh in connection => click auth=>click credentials => select private key (.ppk file)
=> now putty interface open and asking for login as : type ubuntu and enter

# How other teammates will work ? 

1. Teammate generates their own SSH key pair

On their computer, they run:

ssh-keygen -t rsa -b 2048 -f my-teammate-key

This creates:

my-teammate-key (private key)

my-teammate-key.pub (public key)

They send only the .pub file to you.

2. You add their public key to EC2
SSH into your EC2 instance (via PuTTY).

Run:

sudo su
cd /home/ec2-user/.ssh
nano authorized_keys

3. Paste your teammate’s public key (.pub file content) on a new line.

4. Save and exit (Ctrl + O, then Ctrl + X).

5. Set correct permissions (just to be safe):

chmod 600 authorized_keys
chown ec2-user:ec2-user authorized_keys

Teammate connects using their private key:

They use:

Hostname/IP of the EC2

Username: ec2-user

Private key: their my-teammate-key (converted to .ppk for PuTTY/WinSCP if needed)


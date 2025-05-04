sudo apt install-ynginx

sudo nginx -s reload

sudo nano /etc/nginx/sites-enabled/default => ctrl+o  enter ctrl+x

 sudo nginx -t => check nginx syntax is ok
sudo nginx -s reload

sudo apt install -y certbot python3-certbot-nginx
sudo certbot --nginx -d www.ytdemo.com

sudo certbot renew --dry-new

git clone git@github.com:abhayakumarprajapati/Redis-Tutorial.git

# after taking pull  in ec2 ubuntu 
pm2 restart all => to restart your project so that changes reflected in live

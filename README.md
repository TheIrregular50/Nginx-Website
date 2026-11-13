WHAT THIS IS?
This is a project in which i hosted my own website on Nginx

WHAT I USED?
WSL UBUNTU, NGINX, GIT

STEPS
1 mkdir ~/nginx-website, then cd ~/nginx-website
2 turned the directory to a git project with git init, then renamed the branch to main with git branch -m main
3 mkdir ~/nginx-website/site to create a folder site, then nano ~/nginx-website/site/index.html to create my website frontend
4 mkdir -p /var/www/mysite,then sudo cp ~/nginx-website/site/index.html /var/www/mysite/ to copy index.html to mysite, then sudo chown -R username:www-data /var/www/mysite to make myself the owner and www-data (nginx workers) the group for the mysite and everything inside
5 sudo chmod 755 /var/www/mysite to enable access to the folder then sudo chmod 644 /var/www/myself/index.html
6 sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/default.bak to back up the default first then sudo nano /etc/nginx/sites-available/mysite to set my configuration
7 sudo ln -s /etc/nginx/sites-available/mysite /etc/nginx/sites-enabled/mysite to create a shortcut as nginx only uses configs in sites-enabled, then rm /etc/nginx/sites-enabled/default to remove the default shortcut not the file itself as it still exists in /sites-available/default and we also backed it up (default.bak)
8 sudo nginx -t to first test my configuration, then sudo systemctl reload nginx only when successful so it rereads your new config.
9 checked it work through http://localhost

LOGS
checked the logs to see all visits using tail -n 10 /var/logs/nginx/access.log

WHAT WENT WRONG AND HOW I FIXED IT?
I purposely broke the website by changing the permissions to sudo chmod 600 /var/www/nginx/mysite/index.html to get and error and i checked for errors using tail -n 10 /var/logs/nginx/error.log
and the i changed back the permissions to 644 to fix it.

WHAT I LEARNT
I SUCCESSFULLY LEARNT HOW TO HOST MY WEBSITE ON NGINX and check the access logs and error logs.

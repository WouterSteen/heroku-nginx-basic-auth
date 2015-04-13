# Heroku, static Sites, nginx, BasicAuth

This project shows a simple example on how to deploy static sites onto Heroku using nginx as a server and BasicAuth. The main purpose is for prototyping and being able to share it with your peers. 

# Configuration
~ Use nginx and php:
- place a Procfile in your app root directory
- put the following command in that file: "web: vendor/bin/heroku-php-nginx -C config/nginx.conf". This command tells Heroku to use the php/nginx build pack and include (-C) the custom nginx configuration file. 
- NOTE: the path to the custom configuration file is relative from the Procfile!

~ Create custom nginx configuration file:
- as specified above, make a new directory "config" and place the file "nginx.conf" in there
- under "location" you can define the to be restricted path, put a "/" for the root itself
- "auth_basic" is the message that will apear in the browser
- "auth_basic_user_file" tells where to look for the .htpasswd file which contains valid users and their passwords, NOTE: use absolute paths here!

~ Create a .htpasswd file:
- you can generate the passwords in the command line or using online generators

~ Include a HTML file into index.php
- to be able to deploy static sites you need to wrap your html files in php files. Heroku is made for apps, so you have to create a "app" which does nothing more then wrapping static html files.
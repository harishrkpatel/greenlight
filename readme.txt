# Installation instructions

https://docs.bigbluebutton.org/2.2/install.html
[CustomGreenlight] https://docs.bigbluebutton.org/greenlight/gl-customize.html 

# Restart greenlight

docker-compose down
./scripts/image_build.sh greenlight_hp_forked release-v2
docker-compose up -d


# Restart server 

sudo bbb-conf --restart 


# Whitelabel changes

a) 
The below file contains the changes that are to be done within the default chat window that comes.
Also this same file is used to stop the default presentation from showing up.

vi /usr/share/bbb-web/WEB-INF/classes/bigbluebutton.properties

b) 
The default PDF can be replaced by changing the files here 
/var/www/bigbluebutton-default/default.pdf
/var/www/bigbluebutton-default/default.pptx

c) 
The other whitelabel changes are on the public documentation of Greenlight & BBB server.

This file contains the title changes and making html5 client as the default client.
/usr/share/meteor/bundle/programs/server/assets/app/config/settings.yml 




https://docs.bigbluebutton.org/support/faq.html#how-many-simultaneous-users-can-bigbluebutton-support
https://www.ovh.com/world/dedicated-servers/prices/

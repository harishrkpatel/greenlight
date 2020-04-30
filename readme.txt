# Installation instructions

Setup on dedicated host:
Server type: bbb-server.png
https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server


https://docs.bigbluebutton.org/2.2/install.html
[CustomGreenlight] https://docs.bigbluebutton.org/greenlight/gl-customize.html 

# Restart greenlight

docker-compose down
./scripts/image_build.sh greenlight_hp_forked release-v2
docker-compose up -d

docker exec greenlight-v2 bundle exec rake user:create["Harish Patel","harish@logicloop.io","Harish@3214","admin"]

# Restart server 

sudo bbb-conf --restart 
sudo bbb-conf --check

# Whitelabel changes

a) 
The below file contains the changes that are to be done within the default chat window that comes.
Also this same file is used to stop the default presentation from showing up.

vi /usr/share/bbb-web/WEB-INF/classes/bigbluebutton.properties

Keys modified are 
beans.presentationService.defaultUploadedPresentation
defaultWelcomeMessage=Welcome to <b>%%CONFNAME%%</b>!<br><br>To join the audio bridge click the phone button.  Use a headset to avoid causing background noise for others.
defaultWelcomeMessageFooter=...

b) 
The default PDF can be replaced by changing the files here 
/var/www/bigbluebutton-default/default.pdf
/var/www/bigbluebutton-default/default.pptx

c) 
The other whitelabel changes are on the public documentation of Greenlight & BBB server.

This file contains the title changes and making html5 client as the default client.
/usr/share/meteor/bundle/programs/server/assets/app/config/settings.yml

    clientTitle: CloudMeet
    appName: CloudMeet HTML5 Client
    copyright: ""
    helpLink: https://cnh.cloudmeet.online

This file contains module configuration for the config xml.
/var/www/bigbluebutton/client/conf/config.xml

http://docs.bigbluebutton.org/client-configuration.html#videoconf-module

Favicon changes
/var/www/bigbluebutton-default/favicon.ico


docker exec greenlight-v2 bundle exec rake user:create["Harish","harish@logicloop.io","Harish@3214","admin"]

SIZING:

https://docs.bigbluebutton.org/support/faq.html#how-many-simultaneous-users-can-bigbluebutton-support
https://docs.bigbluebutton.org/support/faq.html#bandwidth-requirements
https://docs.bigbluebutton.org/support/faq.html#what-are-the-bandwidth-requirements-for-running-a-bigbluebutton-server
https://www.ovh.com/world/dedicated-servers/prices/
https://groups.google.com/forum/#!topic/bigbluebutton-dev/s9V-Bns5MTQ


API: 

http://docs.bigbluebutton.org/dev/api.html

Generate checksum using the below PHP.

$sharedSecret = 'jUTJJiSNsKuKQg60RBHGuxhaXp4ElWPtQdoy2lQHBZI';

// For getMeetings
$api = 'getMeetings';
$checksum = sha1($api . $sharedSecret);
echo $checksum;

// For isMeetingRunning
$api = 'isMeetingRunning';
$params = 'meetingID=535c81ea415d235f15bbf54c9fc856f0b7ea07fb';
$checksum = sha1($api . $params . $sharedSecret);
echo $checksum;

// For end
$api = 'end';
$params = 'meetingID=535c81ea415d235f15bbf54c9fc856f0b7ea07fb&password=fvocHnmXzfBJ';
$checksum = sha1($api . $params . $sharedSecret);
echo $checksum;

getMeetings: 
https://cloudmeet.online/bigbluebutton/api/getMeetings?checksum=8855d6c1ba563021b5e22b32955f4a4b49475016

isMeetingRunning:
https://cloudmeet.online/bigbluebutton/api/isMeetingRunning?meetingID=535c81ea415d235f15bbf54c9fc856f0b7ea07fb&checksum=a38880da3b6cd0966c36292b2e9022c2c189a26a

end:
https://cloudmeet.online/bigbluebutton/api/end?meetingID=535c81ea415d235f15bbf54c9fc856f0b7ea07fb&password=fvocHnmXzfBJ&checksum=b865540a9d160682f74a87f9dd374e5c71d198fd




https://wellness.connectandheal.com/video/bbb/joinCMMeeting?callID=15565&attendeeType=d1
http://cnh.local/video/bbb/joinCMMeeting?callID=15565&attendeeType=d1

https://wellness.connectandheal.com/video/bbb/joinCMMeeting?callID=15565&attendeeType=pat
http://cnh.local/video/bbb/joinCMMeeting?callID=15565&attendeeType=pat

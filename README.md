# nginx-fallback-stream
nginx configuration for streaming fallback

you will need ubuntu 18.4 LTS

sudo apt install nginx nginx-rtmp-module ffmpeg 

if you have trouble getting artifacts during transition from pause to in rtmp stream try using delay.sh instead of changing source directly.

change this:
exec_publish /usr/bin/curl http://localhost:80/control/redirect/subscriber?app=src&addr=127.0.0.1&newname=in;

to

this:
exec_publish /bin/bash /etc/nginx/delay.sh;

this would delay the source switch to 10 seconds after the stream has started.

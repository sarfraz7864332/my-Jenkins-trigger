#! /bin/bash

url="https://www.tooplate.com/zip-templates/2135_mini_finance.zip"

set -x
set -e

cd /tmp
mkdir -p artifact
rm -rf /tmp/artifact/*
wget $url -O /tmp/artifact/webapp.zip
cd /tmp/artifact && unzip webapp.zip
rm -rf /tmp/artifact/webapp.zip
file=$(ls /tmp/artifact)
rm -rf /var/www/html/*
cp -rf /tmp/artifact/$file/* /var/www/html/
systemctl start httpd
rm -rf /tmp/artifact/*
echo "Web application deployed successfully."
echo "Access the application at http://$(hostname -I | awk '{print $2}')"

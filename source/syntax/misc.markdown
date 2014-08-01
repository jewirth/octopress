---
layout: page
#title: "Hall Of Syntax"
comments: true
sharing: true
footer: true
sidebar: false
---
<p style="margin-top:0.5em; margin-bottom:0.3em"><strong><a href="/syntax">Hall of Syntax</a> -> Miscellanous content:</strong>
<ul>
    <li><a href="#matlab">Matlab: Manually plot connected dots</a></li>
    <li><a href="#osxHiddenFiles">OS X: bash script toggling visibility of hidden files in Finder</a></li>
    <li><a href="#dns">Editing DNS Records</a></li>
</ul>
</p>

<br><strong><a name="matlab"></a></strong>
{% img right /syntax/matlab.png 350 'image' 'images' %} This Matlab script draws and connects single points which are given by the array with the variable name ```points```. The image to the right shows the result of the script below. The script checks the size of the array ```points``` with the ```size()``` function and assigns the returned value - which is ```(8, 2)``` in the example below - to the variable ```x```. That means we have an array with 8 times 2 values. Later, ```x``` is used  by the for-loop to get the amount of points with ```x(1)``` which returns ```8```. Before doing the actual task, a horizontal and a vertical black line is plotted to indicate the abscissa and the ordinate. Then the script draws a filled circle for each point and then plots a line to the next point.

``` matlab draw connected points with Matlab
hold off

% set points to draw and connect
points = [ 0 0;  5 5;  10 5;  11 10; 15 5; 15 15; 5 15; 0 0];

% get amount of points in array points
x = size(points);
amount = x(1);

% plot the axes to the plot explicitly
plot([0 0], [-5 20], 'k-')
hold on
grid on
plot([-5 20], [0 0], 'k-')

% draw each point and a line to the next point
for i = 0:x(1)-1
    scatter(points(i+1,1),points(i+1,2),50,'blue','filled')
    plot([points(i+1,1) points(i+2,1)], [points(i+1,2) points(i+2,2)], 'blue-')
end
scatter(points(i+1,1),points(i+1,2),50,'blue','filled')

hold off
```

<br><strong><a name="osxHiddenFiles"></a></strong>
OS X: bash script toggling visibility of hidden files in Finder:
``` bash toggle hidden files visibility in OS X Finder
if [ "$1" == "ON" ];then
echo "Setting Finder to show hidden files"
defaults write com.apple.finder AppleShowAllFiles TRUE;killall Finder
else
    if [ "$1" == "OFF" ];then
    echo "Setting Finder to NOT show hidden files"
    defaults write com.apple.finder AppleShowAllFiles FALSE;killall Finder
    else
        echo "Give me parameter ON or OFF"
    fi
fi
```

<br><strong><a name="dns"></a></strong>
Editing DNS Records:
``` text dns records
General Syntax: [DOMAIN/SUBDOMAIN] [TYPE] [VALUE]

TYPE        DESCRIPTION
--------------------------
A           point to IPv4
AAAA        point to IPv6
CNAME       redirect to another domain or subdomain

examples:
website.com       A       1.2.3.4
www.website.com   CNAME   website.com
blog.website.com  CNAME   website.com
ftp.website.com   CNAME   website.com
*.website.com     CNAME   website.com
pi.snej.de        CNAME   snej.mygreatdnsservice.com
```

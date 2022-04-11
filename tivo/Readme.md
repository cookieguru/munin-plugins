tivo
====
This graph will plot the used disk space on a TiVo DVR.  The value is derived by
polling the TiVo for all program information since there is no API exposed by 
the unit iself to get disk space used.

Sample Graph
------------
![Graph of tivo](https://raw.githubusercontent.com/cookieguru/munin-plugins/screenshots/tivo.png)

Requirements
------------
A recent version of PHP with the BC Math, cURL, and SimpleXML extensions
installed.  How extensions are installed depends on your platform.  A step below
will test to make sure the necessary extensions are installed on your system.

Installation Instructions
-------------------------
```bash
#Download the plugin
sudo wget https://raw.githubusercontent.com/cookieguru/munin-plugins/master/tivo/tivo -O /usr/share/munin/plugins/tivo
```
Edit lines 3 and 4 to set `IP` and `MAK` (Media Access Key)
```bash
#Add execution permissions
sudo chmod +x /usr/share/munin/plugins/tivo
#Create a cache file
sudo touch /var/cache/munin/tivo
#Set owernship
sudo chmod nobody.munin /var/cache/munin/tivo
#Make sure dependencies are installed (this should print "yes")
sudo munin-run tivo autoconf
#Install the plugin
sudo ln -s /usr/share/munin/plugins/tivo /etc/munin/plugins/tivo
#Restart munin-node
sudo /etc/init.d/munin-node restart
#Optionally, test the output
sudo munin-run tivo config
sudo munin-run tivo
```

A cache file stores the date the Now Playing list last changed (according to the
TiVo DVR).  If the recordings haven't changed, the last known size is returned.
The retreival of the information for every program can take several seconds, and
fetching data again would unnecessarily delay graph generation.

TiVo Suggestions are not included in the total because they are automatiaclly
removed to make space AND because they would be counted towards used space while
they are recording.  The TiVo's API only indicates that a program is recording,
not that it is recording a suggestion.  This also means in-progress recordings
are not shown in the total because they can't be differentiated between
in-progress suggestions being recorded.

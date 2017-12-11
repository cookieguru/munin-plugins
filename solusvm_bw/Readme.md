solusvm_bw
==========
This graph will plot the used and total available bandwidth for a VPS using the
information available from the SolusVM control panel.  You will need API access
to the SolusVM installation.

Sample Graph
------------
![Graph of solusvm_bw](https://raw.githubusercontent.com/cookieguru/munin-plugins/screenshots/solusvm_bw.png)

Requirements
------------
PHP 5.4+ with the cURL extension loaded

Installation Instructions
-------------------------
```bash
#Download the plugin
sudo wget https://raw.githubusercontent.com/cookieguru/munin-plugins/master/solusvm_bw/solusvm_bw -O /usr/share/munin/plugins/solusvm_bw
```
Edit `key`, `hash`, and the URL to your SolusVM API endpoint using your favorite
text editor (see TODO comments) and then:
```bash
#Add execution permissions
sudo chmod +x /usr/share/munin/plugins/solusvm_bw
#Install the plugin
sudo ln -s /usr/share/munin/plugins/solusvm_bw /etc/munin/plugins/solusvm_bw
#Create the cache file
sudo touch /var/cache/munin/solusvm_bw
sudo chown nobody.munin /var/cache/munin/solusvm_bw
#Restart munin-node
sudo /etc/init.d/munin-node restart
#Optionally, test the output
sudo munin-run solusvm_bw config
sudo munin-run solusvm_bw
```

Setting critical/warning limits
-------------------------------
On the munin master, edit `/etc/munin/munin.conf` and set
`solusvm_bw.used.warning` and `solusvm_bw.used.critical` to the number of bytes
at which you want to trigger a warning for the given host.  For example, to set
`host.example.com`'s warning to 375 GiB and critical to 450 GiB:
```plain
[host.example.com]
	solusvm_bw.used.warning 402653184000
	solusvm_bw.used.critical 483183820800
```

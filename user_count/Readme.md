user_count
==========
This graph will plot the number of users on a system, grouped by shell.  Users
without a shell are omitted from the graph.

Sample Graph
------------
![Graph of user_count](https://raw.githubusercontent.com/cookieguru/munin-plugins/screenshots/user_count.png)

Installation Instructions
-------------------------
```bash
#Download the plugin
sudo wget http: -O /usr/share/munin/plugins/user_count
#Add execution permissions
sudo chmod +x /usr/share/munin/plugins/user_count
#Install the plugin
sudo ln -s /usr/share/munin/plugins/user_count /etc/munin/plugins/user_count
#Restart munin-node
sudo /etc/init.d/munin-node restart
#Optionally, test the output
sudo munin-run user_count config
sudo munin-run user_count
```
wordpress_users
===============
This graph will plot the number of users for a given Wordpress installation

Sample Graph
------------
![Graph of wordpress_users](https://raw.githubusercontent.com/cookieguru/munin-plugins/screenshots/wordpress_users.png)

Installation Instructions
-------------------------
```bash
#Download the plugin
sudo wget https://raw.githubusercontent.com/cookieguru/munin-plugins/master/wordpress_users/wordpress_users -O /usr/share/munin/plugins/wordpress_users
```
Edit `PATH_TO_WP_LOAD` as necessary
```bash
#Add execution permissions
sudo chmod +x /usr/share/munin/plugins/wordpress_users
#Install the plugin
sudo ln -s /usr/share/munin/plugins/wordpress_users /etc/munin/plugins/wordpress_users
#Restart munin-node
sudo /etc/init.d/munin-node restart
#Optionally, test the output
sudo munin-run wordpress_users config
sudo munin-run wordpress_users
```
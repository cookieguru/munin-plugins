wordpress_comments
==================
This graph will plot the number of comments for a given Wordpress installation

Sample Graph
------------
![Graph of wordpress_comments](https://raw.githubusercontent.com/cookieguru/munin-plugins/screenshots/wordpress_comments.png)

Installation Instructions
-------------------------
```bash
#Download the plugin
sudo wget https://raw.githubusercontent.com/cookieguru/munin-plugins/master/wordpress_comments/wordpress_comments -O /usr/share/munin/plugins/wordpress_comments
```
Edit `PATH_TO_WP_LOAD` as necessary
```bash
#Add execution permissions
sudo chmod +x /usr/share/munin/plugins/wordpress_comments
#Install the plugin
sudo ln -s /usr/share/munin/plugins/wordpress_comments /etc/munin/plugins/wordpress_comments
#Restart munin-node
sudo /etc/init.d/munin-node restart
#Optionally, test the output
sudo munin-run wordpress_comments config
sudo munin-run wordpress_comments
```
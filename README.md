# SYSCONF profile for an Etherpad-lite installation

This is a [SYSCONF](https://github.com/geonef/sysconf.base)
profile. SYSCONF is a method and tool to manage custom system files
for easy install, backup and sync.

This profile provides an [Etherpad](http://etherpad.org/) service.


## Services

```
# netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      12800/node
```

* The main service is Etherpad-lite running on port 8080.
* You can also access the MySQL service on the port 3306.


## Gitted import/export

This profile provides [import/export](tree/etc/gitted/sync/) for:
* Git's ```sysconf/``` directory <-> guest sysconf directory
* Git's ```mysql/``` files <-> MySQL database


## Gitted integration

* To create a new Gitted repository, follow the instructions at
  [How to setup Gitted for an tplication](http://gitted.io/tutorial/setup-gitted-sysconf/)
  
* Then add this Sysconf profile:
```
git subtree add -P sysconf.gitted.etherpad git@github.com:geonef/sysconf.gitted.etherpad.git master
```

* Integrate it in the dependency chain, for example:
```
echo sysconf.gitted.etherpad >actual/deps
```

* Then push it to the container:
```
./gitted-target init lxc:pad
git push pad sysconf/master
```


## Authors

Written by Jean-Francois Gigand <jf@geonef.fr>. Feel free to contact me!

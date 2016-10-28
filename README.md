#Install:

##Install tor
### Linux
```
$ apt-get install tor
```
### OSX
```
sudo port install tor
```

Install phantomjs from source or copy ubuntu binary in /usr/bin



tor folder contains the tor related files
  tor/config  to store generated config files for TOR (must be writable)
  tor/data    for tor to store its data for different ports (must be writable)
  tor/log     for tor to store its log files for different ports (must be writable)

phatomjs folder contains javascript files that will be executed by phantomjs headless Browser
  phantomjs/log  for tor to store its log files when debugging (must be writable)

we use multiple instances of tor proxy running on seperate ports for different countries

#Make working directories
mkdir ./tor/config
mkdir ./tor/data
mkdir ./tor/log
mkdir ./phantomjs/log


#Execute:

Edit settings.php as necessary


```
cd tor
php generate_config.php
```

this will generate all config files for tor in tor/config folder
and running commands in tor/tor_command.txt file

Copy commands from tor/tor_command.txt and run it in bash terminal
This will get the TOR services running for various countries as specified in settings

Run PhantomJS
```
phantomjs --proxy=<proxy>  --proxy-type=socks5 <scriptpath> <'device'> <'url'>
```

Example:
```
phantomjs --proxy=127.0.0.1:9051  --proxy-type=socks5 ./phantomjs/proxydetails.js 'Linux_Chrome'
`

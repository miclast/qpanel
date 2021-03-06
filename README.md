
# Qpanel

[![Join the chat at https://gitter.im/qpanel/Lobby](https://badges.gitter.im/qpanel/Lobby.svg)](https://gitter.im/qpanel/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/roramirez/qpanel.svg?branch=master)](https://travis-ci.org/roramirez/qpanel)

Qpanel is dashboard for Queues in Asterisk and FreeSWITCH

![Demo](samples/animation.gif)

## Overview

Qpanel is a panel for queues on Asterisk and FreeSWITCH, powerful and simple monitor in realtime:

* General resume for calls. Abandoned, Incoming, Answer time and Waiting time.
* Show information on detail by queue.
* Show agents status if these are free, busy or unavailable.
* Pause reason and time to agents.
* Percent of abandoned calls.
* Allows rename the queue name or hide in case if required not show a determined queue.
* Show callers by queue with the priority and wait time.
* Spy, Whisper and Barge for agents on queues.
* Show service level of queues
* Hangup incomming calls
* Authentication Access.
* Simple configuration. Just use Asterisk manager.
* Multi languages availables: English, Spanish, German, Russian and Portuguese.
* Written on Python.
* Responsive design.
* Opensource by MIT licence.


Also you can use a [API of Qpanel](doc/api.md) for data query related to queues



## Requirement
 * Python 2.7, 3.4
 * [Flask](http://flask.pocoo.org/) 0.10+
 * [Asterisk](http://www.asterisk.org) 1.4+ and enabled manager or [FreeSWITCH](http://www.freeswitch.org) and connection permission to Event Socket Library.

  The feature to scheduler reset stats a queue is required Redis Redis >= 2.6.0


### Asterisk
On /etc/asterisk/manager.conf do you set command permission for read and write, example:

```
    [qpanel]
    secret = mi_super_secret_password
    read = command
    write = command,originate,call,agent
```

#### AMI options
  * _originate_ for spy, whisper and barge.
  * _call_ feature hangup calls.
  * _agent_ remove agents from the queues.


Some features maybe not included in your Asterisk version. In the [patch
directory](patches) you can find the patchs for add more powerfull to the QPanel.


### Freeswitch

The feature realtime counter for answered and abandoned calls in a  queues if not included in your FreeSWITCH version. In the [patch
directory](patches/freeswitch) you can find the patch


You can configure a freeswitch section for your config.ini file like

```
    [freeswitch]
    host = 127.0.0.1
    port = 8021
    password = ClueCon
```

In general section set config

```
    freeswitch = True ; Use FreeSWITCH as backend. Use mod_callcenter
```

## 1. Clone this repository
```
 git clone https://github.com/roramirez/qpanel.git
```

## 2. Install dependencies

```
 $ pip install -r requirements.txt
```
If dont have pip in your system. For install

### Debian and Ubuntu
 ```
 sudo apt-get install python-pip
 ```

### Fedora
 ```
 sudo yum install python-pip
 ```

### Get Javascript, CSS and external web libraries
Is necessary have installed Node.

 ```
    npm install
 ```


##  3. Go and prepair environment
 ```
  cd qpanel
  cp samples/config.ini-dist config.ini
 ```
  Edit config.ini file with Manager Asterisk parameters

  **Note**: Can set the absolute path for configuration file in an enviroment variable called `QPANEL_CONFIG_FILE`.

## 4.- Translations
 ```
  pybabel compile -d qpanel/translations
 ```


## 5.- Run and relax
 ```
    python app.py
 ```

Go url of machine http://IP:5000

If you want run QPanel like a service, see the [samples configurations
files](samples/configs).  There are a example for use with uWSGI + NGINX

## QueueLog Stats for Asterisk
You could use the stats for queue of `Asterisk` from QueueLog. If need more informacion about this go [Stats, Realtime and other things](doc/StatsConfig.md)
or see the section `[queue_log]` of the [sample configuration file](samples/samples/config.ini-dist)


## New features?
If you like new features or something is wrong [please open a issue](https://github.com/roramirez/qpanel/issues/new)

If you want check the development version get checkout of `develop` branch

 ```
 git clone -b develop https://github.com/roramirez/qpanel.git
 ```


## Updating source new in a release

Go the Qpanel directory
```
    cd qpanel
```


Get the new code

```
    git pull
```

Update dependencies

```
    pip install -r requirements.txt
    npm install
```


## How to contribute

 * Fork the project
 * Create a feature branch (git checkout -b my-feature)
 * Add your files changed (git add file_change1 file_change2, etc..)
 * Commit your changes (git commit -m "add my feature")
 * Push to the branch (git push origin my-feature)
 * Create a pull request

Happy coding :)

[![Baikal](https://baikal.io/badges/torque59/nosqlpot)](https://baikal.io/torque59/nosqlpot)

NoSQL-Honeypot-Framework (NoPo)
==

Adapted from https://github.com/torque59/nosqlpot by Francis Alexander (NoSQL-Honeypot-Framework, NoPo, 2015), migrated to Python 3.

Python 3 changes
----------------

* Runs on Python 3.8 or later (tested with Python 3.11 on Debian 12) with current Twisted, fakeredis, redis_protocol 0.0.2 and CherryPy; Python 2 is no longer required. Tested versions are pinned in `requirements.txt`.
* print statements, `ConfigParser`, `httplib`/`urllib` and implicit relative imports updated to their Python 3 equivalents; mixed tab and space indentation normalised.
* Network data is decoded as latin-1 (one character per byte, as a Python 2 `str`) and replies are encoded back to bytes, so the Redis engine sees exactly what it saw under Python 2.
* fakeredis 0.x shared one data store between all `FakeStrictRedis` instances; current fakeredis does not, so the Redis engine now passes one shared `FakeServer`, keeping SET and GET working across commands and connections as before.
* The CouchDB configuration is read without interpolation (`RawConfigParser`), as Python 3's `ConfigParser` rejects the `%s` placeholder that Python 2 accepted.

The behaviour seen by clients (the emulated Redis and CouchDB replies) is unchanged from the original at commit 225ab5a (January 2017). Run it from the repository directory, as the engines read and write their configuration files by relative path.

The original licence (GNU GPL version 2, see `LICENSE`) and copyright notices are kept.


NoSQL-Honeypot-Framework (NoPo) is an open source honeypot for nosql databases that automates the process of detecting attackers,logging attack incidents. The simulation engines are deployed using the twisted framework.Currently the framework holds support for redis.

N.B : The framework is under development and is prone to bugs 

Screenshots
----
* Server Deployed
![Screenshot](http://i.imgur.com/4cCX3Me.png)

Installation
----

You can download NoPo by cloning the [Git](https://github.com/torque59/nosqlpot) repository:

    git clone https://github.com/torque59/nosqlpot.git
    
    pip install -r requirements.txt

This version works with [Python](http://www.python.org/download/) 3.8 or later (the original required **2.6.x** or **2.7.x**).


Added Features:
============================

- First Ever Honeypot for NoSQL Databases
- Support For Config Files 
- Simulates Protocol Specification as of Servers
- Support for Redis


Usage
----

Get a list of basic options :

    python nosqlpot.py -h

Deploy an nosql engine:

    python nosqlpot.py -deploy redis
    pythom nosqlpot.py -deplot couch

Deploy an nosql engine with a configuration file:

    python nosqlpot.py -deploy redis -config filename
    
Log commands,session to file :

    python nosqlpot.py -deploy redis -out log.out


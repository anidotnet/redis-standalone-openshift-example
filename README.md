Redis on OpenShift
==================

This git repository helps you get up and running quickly with Redis on OpenShift.


Quickstart
----------------------------

Create an account at http://openshift.redhat.com/

Create a Openshift application with a cartridge of your choice.

    rhc app create -a redis -t diy-0.1

Add this upstream repo

    cd redis
    git remote add upstream -m master git://github.com/anidotnet/redis-standalone-openshift-example.git
    git pull -s recursive -X theirs upstream master
    
Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://redis-$yournamespace.rhcloud.com


Command Line Tools
----------------------------

SSH into you application and run command

    export PATH=${OPENSHIFT_RUNTIME_DIR}bin/:$PATH

the following command line tools are now available

    redis {start|stop}
    redis-cli
    redis-server
    redis-benchmark
    redis-check-aof
    redis-check-dump

Redis server listens on port 16000. So the correct command to run Redis CLI is

    redis-cli -p 16000


Log File
----------------------------

To view the redis.log file use command

    rhc app tail -a $APPNAME

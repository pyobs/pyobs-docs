Installing pyobs
****************

For installing, you first have to clone the *pyobs* repository::

    git clone git@gitlab.gwdg.de:pyobs/pyobs-core.git pyobs

Then you can simply install it::

    cd pyobs-core
    python3 setup.py install


Using the pyobsd tool
=====================

*pyobs* comes with its own little tool called *pyobsd* for starting and stopping *pyobs* modules. On Linux systems,
you should create a new user "pyobs"::

    adduser pyobs --home /opt/pyobs

Note that we've set the user's home directory to /opt/pyobs.

Change into the new user, and create some directories::

    su pyobs
    mkdir -p /opt/pyobs/config
    mkdir -p /opt/pyobs/log
    mkdir -p /opt/pyobs/run

Every configuration YAML file in the *config* directory will now automatically show up in the *pyobsd* tool. Logs will
be written into the *log* directory, and PID files for each process into *run*.

Docker
======

Build Docker image::

    docker build --tag=pyobs .

And run it::

    docker run -v $(pwd)/camera.yaml:/pyobs.yaml pyobs
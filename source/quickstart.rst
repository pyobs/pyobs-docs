Quickstart
==========

Setting up ejabberd
-------------------
In case you already have a working XMPP server, skip this step.

1. Download ejabberd from https://www.process-one.net/en/ejabberd/downloads/ and install it.

2. Since the allowed packet sizes are by default a little too small, find the ejabberd config file **ejabberd.yml**
   and find and edit the "shaper" part::

    shaper:
      normal: 100000
      fast: 5000000

3. Start ejabberd server using::

    ejabberdctl start

4. Add a Shared Roster Group so that all clients are in each others roster (replace <host> with local hostname)::

    ejabberdctl srg_create all <host> all all all
    ejabberdctl srg_user_add @all@ <host> all <host>

5. Register users (may skip for now), e.g.::

    ejabberdctl register <name> <host> <password>

Install *pyobs*
---------------
1. Clone the *pyobs* repository::

    git clone git@gitlab.gwdg.de:pyobs/pyobs-core.git pyobs
    cd pyobs

2. Create virtual environment::

    python3 -m venv venv
    source ./venv/bin/activate

3. Install requirements::

    pip install -r requirements.txt

Run simple config
-----------------
Create a new file **standalone.yaml** with the following content::

    class: pyobs.modules.test.StandAlone
    message: Hello world
    interval: 10

And run it::

    pyobs standalone.yaml

Now you should get some output about starting the module, and every 10 seconds a message like this should appear::

    [INFO] standalone.py:38 Hello world

You can shutdown pyobs via crtl+c.

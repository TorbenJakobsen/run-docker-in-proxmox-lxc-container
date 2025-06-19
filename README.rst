#############################
  Run Docker in Proxmox LXC
#############################

****************
  Introduction
****************

Going forward I will shorten 'Proxmox Virtual Environment' to 'PVE' or 'pve'.

https://www.proxmox.com/

*******************************
  Create a container template
*******************************

Select (download) latest Ubuntu LTS (2404.2-2).

Update
======

Do the usual post-install housekeeping chores.

.. code:: bash

  apt update && apt dist-upgrade -y

Install Docker
==============

As both Ubuntu and RaspberryOS are based on Debian scripts can be quite similar.
Follow:
https://raspberrytips.com/docker-compose-raspberry-pi/
to install Docker and lean about related useful topics.

#. Install :code:`curl`

.. code:: bash

  apt install curl

#. Install :code:`docker`

.. code:: bash

  curl -sSL https://get.docker.com | sh

#. Verify

.. code:: bash

  systemctl status docker

  docker --version

Add user
========

Add password and the rest can be blanks (press return multiple times).

.. code:: bash

  adduser ve

Add to sudo group

.. code:: bash

  adduser ve sudo

.. code:: bash

  adduser ve docker

Verify...

.. code:: bash

  groups ve

Expected result is: :code:`ve : ve sudo users docker`.

Login as :code:`ve` (or use :code:`su`):

.. code:: bash

Disable (lock) root account 

.. code:: bash

  sudo passwd -l root

You will now have to login as :code:`ve` and use :code:`sudo`.


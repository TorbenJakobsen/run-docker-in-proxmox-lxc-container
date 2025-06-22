#######################################
  Run Docker in Proxmox LXC Container
#######################################

****************
  Introduction
****************

Going forward I will shorten 'Proxmox Virtual Environment' to 'PVE' or 'pve'.

I will describe the process using Ubuntu.

*******************************
  Create a Container Template
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

1. Install :code:`curl`

.. code:: bash

  apt install curl

2. Install :code:`docker`

.. code:: bash

  curl -sSL https://get.docker.com | sh

3. Verify

.. code:: bash

  systemctl status docker

  docker --version

Add User
========

1. Add password when asked; the remaining inputs can be empty (press return multiple times).
It is fine to use a simple password as you should change it after cloning the template.

.. code:: bash

  adduser ve

2. Add to groups

.. code:: bash

  adduser ve sudo

.. code:: bash

  adduser ve docker

3. Verify

.. code:: bash

  groups ve

Expected result is: :code:`ve : ve sudo users docker`.

4. Login

Login as :code:`ve` (or use :code:`su`):

Lock Down root
==============

Disable (lock) root account 

.. code:: bash

  sudo passwd -l root

.. note::

  You will now have to login as :code:`ve` and use :code:`sudo`.

Minimize Size
=============

.. code:: bash

  sudo apt clean
  sudo apt autoremove 

Make into a Template
====================

  ...

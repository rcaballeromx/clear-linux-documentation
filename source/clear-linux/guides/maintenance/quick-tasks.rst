.. _maintenance-quick-tasks:

Maintenance quick tasks
#######################

This guide provides instructions for quick tasks
associated with maintaining |CLOSIA| after :ref:`installation <get-started>`
is completed.

Quick tasks included in this document:
 * :ref:`check-current-release`
 * :ref:`add-admin-user`
 * :ref:`change-hostname`
 * :ref:`install-root-cert`

.. _check-current-release:

Check the current release running on your system
************************************************

To check which |CL| release is running on your
system, enter one of the following commands:

.. code-block:: console

   grep VERSION_ID /usr/lib/os-release

or

.. code-block:: console

   $ sudo swupd update -s

.. _add-admin-user:

Add a user to the administrator group
*************************************

To be able to execute all applications with administrative privileges,
we must add the `<userid>` to the `wheel group`_.

.. code-block:: console

   usermod -G wheel <userid>

.. _change-hostname:

Change your Clear Linux hostname
********************************

.. code-block:: console

   hostnamectl set-hostname myhostname

.. _install-root-cert:

Install root certificate
************************

Run the following command:

.. code-block:: console

   c_hash ca.crt

Copy the output to the left of the :guilabel:`=>`. This is be your hash.
Run the command below with the copied output in place of `<HASH>`.

.. code-block:: console

   mkdir -p /etc/ssl/certs
   cp ca.crt /etc/ssl/certs
   cd /etc/ssl/certs
   ln -s ca.crt <HASH>

.. _`wheel group`:
   https://en.wikipedia.org/wiki/Wheel_(Unix_term)
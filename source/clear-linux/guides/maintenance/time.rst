.. _time::

Set the time
############

|CLOSIA| utilizes `systemd-timesyncd.service` to sync time. Default network
time protocol (NTP) servers are configured as time1.google.com,
time2.google.com, time3.google.com, and time4.google.com. It is not possible
to set the time manually, via `timedatectl` or to use `RTC` mode.

This section provides instructions to set the time in the event that the
time is incorrect on your |CL| system and the default NTP servers cannot be
reached.

#. Install the os-core-dev bundle:

   .. code-block:: console

      swupd bundle-add os-core-dev

#. Set your timezone (this example uses Los Angeles).

   .. code-block:: console

   timedatectl set-timezone America/Los_Angeles

   .. note::
      To see a list of timezones, enter:
      `timedatectl list-timezones | grep <locale>`

#. Create `/etc/systemd/` directory.

   .. code-block:: console

      mkdir /etc/systemd/

#. Open your chosen editor and type into the
   :file:`/etc/systemd/timesyncd.conf` file.

   .. code-block:: .conf

      [Time]
      NTP=<Preferred Server>
      FallbackNTP=<backup server 1> <backup server 2>

#. Restart the `timesyncd` daemon

   .. code-block::

      systemctl  restart systemd-timesyncd

.. _Note::
   Check to make sure your time is correctly set, enter the :command:`date`
   command.

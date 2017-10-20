.. _bundle-commands:

Useful bundle commands
######################

 * See a list of currently-installed bundles:

   .. code-block:: console

      # swupd bundle-list

   or

   .. code-block:: console

      ls /usr/share/clear/bundles

 * See the list of all available bundles:

   .. code-block:: console

      # swupd bundle-list --all

   or

   .. code-block:: console

      cat /var/lib/swupd/<build number>/Manifest.MoM

 * Add a bundle:

   .. code-block:: console

      # swupd bundle-add <bundle name>

 * See which packages are included in a given bundle:

   https://download.clearlinux.org/update/<VER>/Manifest.<BUNDLE>

 * Subscribe to a bundle:

   .. code-block:: console

      swupd bundle-add <bundle name>

 * Remove a bundle

   .. code-block:: console

      swupd bundle-remove <bundle name>
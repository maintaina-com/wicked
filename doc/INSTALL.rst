======================
 Installing Wicked H5
======================

:Contact: horde@lists.horde.org

.. contents:: Contents
.. section-numbering::

This document contains instructions for installing the Wicked Wiki application
on your system.

For information on the capabilities and features of Wicked, see the file
README_ in the top-level directory of the Wicked distribution.


Prerequisites
=============

To function properly, Wicked **requires** the following:

1. A working Horde installation.

   Wicked runs within the `Horde Application Framework`_, a set of common tools
   for web applications written in PHP.  You must install Horde before
   installing Wicked.

   .. Important:: Wicked H5 requires version 5.0+ of the Horde Framework -
                  earlier versions of Horde will **not** work.

   .. Important:: Be sure to have completed all of the steps in the
                  `horde/doc/INSTALL`_ file for the Horde Framework before
                  installing Wicked. Many of Wicked's prerequisites are also
                  Horde prerequisites. Additionally, many of Wicked's optional
                  features are configured via the Horde install.

   .. _`Horde Application Framework`: http://www.horde.org/apps/horde

2. SQL support in PHP.

   Wicked stores its data in an SQL database. Build PHP with whichever
   SQL driver you require; see the Horde INSTALL file for details.

The following items are not required, but if present will enable advanced
features in Wicked:

1. The following PEAR packages:
   (See `horde/doc/INSTALL`_ for instructions on installing PEAR packages)

   .. Important:: If you are going to install Wicked the recommended way,
                  i.e. using the PEAR installer, you can skip the remainder of
                  this section. Installing Wicked through PEAR will
                  automatically download and install all required PEAR modules.

   a. Text_Figlet

      Text_Figlet can be used to require unauthenticated users to enter a
      CAPTCHA when updating pages.


Installing Wicked
=================

The **RECOMMENDED** way to install Wicked is using the PEAR installer.
Alternatively, if you want to run the latest development code or get the
latest not yet released fixes, you can install Wicked from Git.

Installing with PEAR
~~~~~~~~~~~~~~~~~~~~

First follow the instructions in `horde/doc/INSTALL`_ to prepare a PEAR
environment for Horde and install the Horde Framework.

When installing Wicked through PEAR now, the installer will automatically
install any dependencies of Wicked too. If you want to install Wicked with all
optional dependencies, but without the binary PECL packages that need to be
compiled, specify both the ``-a`` and the ``-B`` flag::

   pear install -a -B horde/wicked

By default, only the required dependencies will be installed::

   pear install horde/wicked

If you want to install Wicked even with all binary dependencies, you need to
remove the ``-B`` flag. Please note that this might also try to install PHP
extensions through PECL that might need further configuration or activation in
your PHP configuration::

   pear install -a horde/wicked

Installing from Git
~~~~~~~~~~~~~~~~~~~

See http://www.horde.org/source/git.php


Configuring Wicked
==================

1. Configuring Wicked

   You must login to Horde as a Horde Administrator to finish the configuration
   of Wicked.  Use the Horde ``Administration`` menu item to get to the
   administration page, and then click on the ``Configuration`` icon to get the
   configuration page.  Select ``Wiki`` from the selection list of
   applications.  Fill in or change any configuration values as needed.  When
   done click on ``Generate Wiki Configuration`` to generate the ``conf.php``
   file.  If your web server doesn't have write permissions to the Wicked
   configuration directory or file, it will not be able to write the file.  In
   this case, go back to ``Configuration`` and choose one of the other methods
   to create the configuration file ``wicked/config/conf.php``.

   Documentation on the format and purpose of the other configuration files in
   the ``config/`` directory can be found in each file. You may create
   ``*.local.php`` versions of these files if you wish to customize Wicked's
   appearance and behavior. See the header of the configuration files for
   details and examples. The defaults will be correct for most sites.

2. Creating the database tables

   Once you finished the configuration in the previous step, you can create all
   database tables by clicking the ``DB schema is out of date.`` link in the
   Wicked row of the configuration screen.

   Alternatively creating the Wicked database tables can be accomplished with
   horde's ``horde-db-migrate`` utility.  If your database is properly setup in
   the Horde configuration, just run the following::

      horde-db-migrate wicked

3. Testing Wicked

   Test at least the following:

   - Modify a page
   - Create a new page via a WikiLink
   - Delete a page


URL Styles
==========

Wicked can use two forms of URLs: mod_rewrite style, or GET style. Your web
server must have URL rewriting enabled to use the mod_rewrite style. Apache
Servers or Apache Proxy Servers may also need to have AllowEncodedSlashes
and/or AcceptPathInfo enabled to use the mod_rewrite style. The GET style URLs
should work without any special configuration.

Note for users of Lighttpd web server: The rewrite url generation relies on
rewrite rules being configured on your web server. Since lighttpd does not
support .htaccess files like Apache, there is also a configuration file for
lighttpd included that contains the necessary rewrite rules. This file is::

    doc/lighttpd-ansel.conf

Instructions for using it are included in the file.


Obtaining Support
=================

If you encounter problems with Wicked, help is available!

The Horde Frequently Asked Questions List (FAQ), available on the Web at

  http://wiki.horde.org/FAQ

The Horde Project runs a number of mailing lists, for individual applications
and for issues relating to the project as a whole.  Information, archives, and
subscription information can be found at

  http://www.horde.org/community/mail

Lastly, Horde developers, contributors and users may also be found on IRC,
on the channel #horde on the Freenode Network (irc.freenode.net).

Please keep in mind that Wicked is free software written by volunteers.  For
information on reasonable support expectations, please read

  http://www.horde.org/community/support

Thanks for using Wicked!

The Wicked team


.. _README: README
.. _`horde/doc/INSTALL`: ../../horde/doc/INSTALL
.. _`horde/doc/TRANSLATIONS`: ../../horde/doc/TRANSLATIONS

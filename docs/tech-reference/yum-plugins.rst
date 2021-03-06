===========
Yum Plugins
===========

Yum Types
=========

The following are the supported unit types for the Yum plugins. Each unit has a
unit type and metadata component. Unit type is a unique combination of fields,
and metadata constitutes the rest of the information associated to the unit. The order of the unit fields is
significant (and they are listed in order), as they together represent the unit key.

RPM
----

The RPM's ID is ``rpm``.

Unit Key
^^^^^^^^

``name``
 Name of the rpm package

``version``
 Version number of the rpm package

``release``
 Release of the rpm package

``epoch``
 Epoch of the rpm package

``arch``
 Arch of the rpm package

``checksumtype``
 Checksum type used to generate the rpm checksum value

``checksum``
 Checksum of the rpm package. This is the checksum of the package itself and not the rpm header checksum

Metadata
^^^^^^^^

``filename``
 Filename of the rpm package

``vendor``
 The organization responsible for building this rpm package

``description``
 A more verbose description of the rpm package

``buildhost``
 The hostname of the build machine on which this package is built

``license``
 The license information of the vendor

``requires``
 Used to include required package dependencies for this rpm package

``provides``
 Used to include rpm provides information

``repodata``
 metadata xml snippets for rpm package. This includes primary, filelists and other xmls.
 Example format: ``{"primary" : <primary_xml>, "filelist" : <filelist_xml>, "other" : <other_xml> }``

SRPM
----

The SRPM's ID is ``srpm``.

Unit Key
^^^^^^^^

``name``
 Name of the srpm package

``version``
 Version number of the srpm package

``release``
 Release of the srpm package

``epoch``
 Epoch of the srpm package

``arch``
 Arch of the srpm package

``checksumtype``
 Checksum type used to generate the srpm checksum value

``checksum``
 Checksum of the srpm package. This is not the srpm header checksum

Metadata
^^^^^^^^

``filename``
 Filename of the srpm package

``vendor``
 The organization responsible for building this srpm package

``description``
 A more verbose description of the srpm package

``buildhost``
 The hostname of the build machine on which this package is built

``license``
 The license information of the vendor

``requires``
 Used to include the required package dependencies for this srpm package

``provides``
 Used to include srpm provides information

``repodata``
 metadata xml snippets for srpm package. This includes primary, filelists and other xmls.
 Example format: ``{"primary" : <primary_xml>, "filelist" : <filelist_xml>, "other" : <other_xml> }``

DRPM
----

The DRPM's ID is ``drpm``.

Unit Key
^^^^^^^^
``epoch``
 Epoch of the rpm package

``version``
 Version of the rpm package

``release``
 Release of the rpm package

``filename``
 filename of the drpm package

``checksum``
 checksum of the drpm package

``checksumtype``
 checksum type of the drpm package

Metadata
^^^^^^^^
``size``
 Size of the drpm

``sequence``
 delta rpm sequence

``new_package``
 new rpm package associated with the drpm package

Errata
------

The Erratum's ID is ``erratum``.

Unit Key
^^^^^^^^

``id``
 Erratum ID string

Metadata
^^^^^^^^

``title``
 Title of the erratum

``description``
 A more detailed description of the erratum

``version``
 Version of the erratum

``release``
 Release of the erratum

``type``
 Type of erratum. Valid values include "security", "bugfix" and "enhancement" erratum

``status``
 Status of the erratum. Example status: "final"

``updated``
 Updated date of the erratum. Expected format "YYYY-MM-DD HH:MM:SS"

``issued``
 Issued date of the erratum. Expected format "YYYY-MM-DD HH:MM:SS"

``severity``
 severity of the erratum. Valid values include "Low", "Moderate", "High"

``references``
 Reference information associated with this erratum

``pkglist``
 Includes package information associated with this erratum

``rights``
 Copyrights information associated for the erratum

``summary``
 Detailed summary information for this erratum

``solution``
 Detailed Solution information for this erratum

``from``
 Typically an email address of the erratum issuer

``pushcount``
 Number of times the erratum has been pushed

``reboot_suggested``
 Flag indicating if this erratum is installed it will require a reboot of the system

``relogin_suggested``
 Flag indicating if this erratum is installed it will require a relogin of the system -
 this flag exists only on SUSE erratum

``restart_suggested``
 Flag indicating if this erratum is installed it will require a restart of the system -
 this flag exists only on SUSE erratum

Distribution
------------

The distribution type's ID is ``distribution``. A distribution tree is described in a
``treeinfo`` or ``.treeinfo`` file. This INI-style file is described in the
`productmd <https://release-engineering.github.io/productmd/treeinfo-1.0.html>`_
project's documentation. A distribution tree can be created with the
`lorax <https://github.com/rhinstaller/lorax/>`_ tool and is used by the
`anaconda <https://github.com/rhinstaller/anaconda>`_ installer to kickstart installations.
A distribution is contained within a yum repository.

There are cases where a repository contains files that are not referenced by the repository's
metadata files or by the ``treeinfo`` file. In these cases, there may be a
``PULP_DISTRIBUTION.xml`` file present used to enumerate such files. This XML file was introduced
in the 2.5 release of the ``pulp_rpm`` plugin. The initial
`schema <https://github.com/pulp/pulp_rpm/blob/2.5-release/plugins/usr/share/pulp-rpm/pulp_distribution.xsd>`_
fails to include elements necessary for file validation.

Unit Key
^^^^^^^^

``id``
 ID of the distribution to be inventoried

``family``
 Family of the distribution tree. For example: Red Hat Enterprise Linux

``variant``
 Variant of the distribution tree. For example: Workstation

``version``
 Version of the distribution tree. For example: 6Server

``arch``
 Arch of the distribution tree. For example: x86_64

Metadata
^^^^^^^^

``files``
 Files associated with the distribution tree.

``timestamp``
 The ``timestamp`` value as taken from the treeinfo file.

Package Group
-------------

The Package Group's ID is ``package_group``.

Unit Key
^^^^^^^^
``id``
 Package group ID

``repo_id``
 Repository ID the package group ID is associated

Metadata
^^^^^^^^
``name``
 Name of the package group

``description``
 Description of the package group

``default``
 Include this package group by default. Valid values are `True` and `False`

``user_visible``
 If the packagegroup should be visible when queried. Valid values are `True` and `False`

``langonly``
 Language support groups are selected based on this option

``display_order``
 Display order of the package group. If not specified, default value is '1024'

``mandatory_package_names``
 Mandatory package names to include in the package group

``conditional_package_names``
 Conditional package names to include in the package group

``optional_package_names``
 Optional package names to include in the package group

``default_package_names``
 Default package names to include in the package group

Package Group Category
----------------------

The Package Group Category's ID is ``package_category``.

Unit Key
^^^^^^^^
``id``
 Package group category ID

``repo_id``
 Repository ID to which the package group category ID is associated


Metadata
^^^^^^^^
``name``
 Name of the package group category

``description``
 Description of the package group category

``display_order``
 Display order of the package group category. If not specified, default value is '1024'

``packagegroupids``
 Package group IDs associated with the package category


Package Group Environment
-------------------------

The Package Group Environment's ID is ``package_environment``.

Unit Key
^^^^^^^^
``id``
 Package group Environment ID

``repo_id``
 Repository ID to which the package group category ID is associated


Metadata
^^^^^^^^
``name``
 Name of the package group environment

``translated_name``
 Translated names of the package group environment.  These are saved as a dictionary of locale
 codes to translated names.
 Example format: ``{"zh_TW" : 'KDE Plasma 工作空間'}``

``description``
 Description of the package group environment

``translated_description``
 Translated descriptions of the package group environment.  These are saved as a dictionary of locale
 codes to translated descriptions.
 Example format: ``{"ru" : 'KDE Plasma Workspaces - легко настраиваемый графический интерфейс пользователя, который содержит панель, рабочий стол, системные значки и виджеты рабочего стола, а также множество мощных приложений KDE.'}``

``display_order``
 Display order of the package group environment. If not specified, default value is '1024'

``group_ids``
 List of Package group IDs associated with the package environment
 Example format: ``['<group_id_1>','<group_id_2>']``

``options``
 Package group IDs and whether they are default options.  The default flag must be set to either
 `True` or `False`.
 Example format: ``{"group" : <group_id>, "default" : True}``


.. note::
    Package_group, package_category and package environment elements can also be uploaded via comps file.
    For more info see :ref:`upload_comps_xml_file`.


Yum Repo Metadata File
----------------------

The Yum Repo Metadata File's ID is ``yum_repo_metadata_file``.

Unit Key
^^^^^^^^
``repo_id``
 The repository id that this metadata file belongs to

``data_type``
 The type of the metadata file

Metadata
^^^^^^^^
``checksum``
 The checksum of the metadata file

``checksum_type``
 The name of the algorithm used to calculate the ``checksum``


Yum Importer
============

The Yum Importer can be used to sync an RPM repository with an upstream feed. The Yum Importer ID is
``yum_importer``.

Configuration Parameters
------------------------

The following options are available to the yum importer configuration. All
configuration values are optional.

``feed``
 URL where the repository's content will be synchronized from. This can be either
 an HTTP URL or a location on disk represented as a file URL.

``ssl_validation``
 Indicates if the server's SSL certificate is verified against the CA certificate
 uploaded. The certificate should be verified against the CA for each client request.
 Has no effect for non-SSL feeds. Valid values to this option are ``True`` and ``False``;
 defaults to ``True``.

``ssl_ca_cert``
 CA certificate string used to validate the feed source's SSL certificate (for feeds
 exposed over HTTPS). This option is ignored if ``ssl_verify`` is false.

``ssl_client_cert``
 Certificate used as the client certificate when synchronizing the repository.
 This is used to communicate authentication information to the feed source.
 The value to this option must be the full path to the certificate. The specified
 file may be the certificate itself or a single file containing both the certificate
 and private key.

``ssl_client_key``
 Private key to the certificate specified in ``ssl_client_cert``, assuming it is not
 included in the certificate file itself.

``proxy_host``
 Indicates the URL to use as a proxy server when synchronizing this repository.

``proxy_port``
 Port to connect to on the proxy server.

``proxy_username``
 Username to pass to the proxy server if it requires authentication.

``proxy_password``
 Password to use for proxy server authentication.

``basic_auth_username``
 Username to pass to the feed URL's server if it requires authentication.

``basic_auth_password``
 Password to use for server authentication.

``query_auth_token``
 An authorization token that will be added to every request made to the feed URL's
 server, which may be required to sync from repositories that use this method of
 authorization (SLES 12, for example). This mechanism only supports syncing RPM, deltarpm,
 and errata content.

``max_speed``
 The maximum download speed in bytes/sec for a task (such as a sync);
 defaults to None

``validate``
 If True, as the repository is synchronized the checksum of each file will be
 verified against the metadata's expectation. Valid values to this option are
 ``True`` and ``False``; defaults to ``False``.

``max_downloads``
 Number of threads used when synchronizing the repository. This count controls
 the download threads themselves and has no bearing on the number of operations
 the Pulp server can execute at a given time; defaults to ``1``.

``remove_missing``
 If true, as the repository is synchronized, old rpms will be removed. Valid values
 to this option are ``True`` and ``False``; defaults to ``False``

``retain_old_count``
 Count indicating how many old rpm versions to retain; by default it will download
 all versions available.

``skip``
 List of content types to be skipped during the repository synchronization.
 If unspecified, all types will be synchronized. Valid values are: rpm, drpm, srpm,
 distribution, erratum; default is []. If ``rpm`` is specified, ``srpm`` packages
 will be skipped as well.

``checksum_type``
 checksum type to use for metadata generation; defaults to source checksum type of ``sha256``.

``num_retries``
 Number of times to retry before declaring an error during repository synchronization;
 defaults to ``2``.

``copy_children``
 Supported only as an override config option to a repository copy command, when
 this option is False, the copy command will not attempt to locate and copy child
 packages of errata, groups, or categories. For example, if it is already known
 that all of a group's RPMs are available in the destination repository, it can
 save substantial time to set this to False and thus not have the importer verify
 the presence of each. default is True.

``download_policy``
 Set the download policy for a repository. By default this is ``immediate``.
 The other options are ``on_demand``, where content is only downloaded when
 a client requests it, and ``background``, where the sync does not download
 content, but after the sync completes a task is dispatched to download all
 the content in the background. The content is available for client retrieval
 during this time.

``force_full``
 Boolean flag. If true, full re-sync is triggered.

``require_signature``
 Requires that imported packages like RPM/DRPM/SRPM should be signed. Defaults to False.
 This does not trigger package signature verification, it only guarantees that the package
 is signed.

``allowed_keys``
 Comma-separated list of allowed signature key IDs that imported packages can be signed with.
 The key should be lowercase 8 character abbreviated fingerprint (the so-called short key ID).
 Since short key IDs are `easy to impersonate <https://evil32.com/>`_, this feature is intended to
 make it easy to filter packages based on their signing key and does not use these key IDs for
 package signature verification.


Yum Distributor
===============

The Yum Distributor ID is ``yum_distributor``.

Configuration Parameters
------------------------

The following options are available to the Yum Distributor configuration.

Required Configuration Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

``http``
 Flag indicating if the repository will be served over a non-SSL connection.
 Valid values to this option are ``True`` and ``False``.

``https``
 Flag indicating if the repository will be served over an SSL connection. If
 this is set to true, the ``https_ca`` option should also be specified to ensure
 consumers bound to this repository have the necessary certificate to validate
 the SSL connection. Valid values to this option are ``True`` and ``False``.

``relative_url``
 Relative path at which the repository will be served.

Optional Configuration Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

``protected``
 Protect the published repository with repo authentication. Valid values to this
 option are ``True`` and ``False``.

``auth_cert``
 Certificate that will be provided to consumers bound to this repository. This
 certificate should contain entitlement information to grant access to this
 repository, assuming the repository is protected. The value to this option must
 be the full path to the certificate file. The file must contain both
 the certificate itself and its private key.

``auth_ca``
 CA certificate that was used to sign the certificate specified in ``auth-cert``.
 The server will use this CA to verify that the incoming request's client certificate
 is signed by the correct source and is not forged. The value to this option
 must be the full path to the CA certificate file.

``https_ca``
 CA certificate used to sign the SSL certificate the server is using to host
 this repository. This certificate will be made available to bound consumers so
 they can verify the server's identity. The value to this option must be the
 full path to the certificate.

``gpgkey``
 File containing GPG keys used to sign RPMs and metadata in this repository.
 These keys will be made available to consumers to use for verifying content in
 the repository. The value provided to this option must be the full path to a
 GPG key file containing one or more ASCII armored public keys.

``generate_sqlite``
 Boolean flag to indicate whether or not sqlite files should be generated during
 a repository publish.  If unspecified it will not run due to the extra time needed to
 perform this operation.

``repoview``
 Boolean flag to indicate whether or not static HTML files should be generated by
 the repoview tool during a repository publish to improve browsing experience. If
 specified it requires the ``generate_sqlite`` flag to be ``True``.

``checksum_type``
 Checksum type to use for metadata generation. For any units where the checksum of this type is not
 already known, it will be computed on-the-fly and saved for future use. If any such units have not
 been downloaded, then checksum calculation is impossible, and the publish will fail gracefully.

``updateinfo_checksum_type``
 Checksum type to use for updateinfo.xml generation. For each package listed in updateinfo.xml
 the checksum of this type will be published if available, otherwise ``checksum_type`` will be used.

``gpg_sign_metadata``
 Boolean flag to indicate whether or not a repomd.xml.asc file should be
 generated when the repository is published. If yum is configured with
 repo_gpgcheck=1 then yum will use the repomd.xml.asc file to verify the
 authenticity of the repomd.xml file. This flag defaults to ``False``, however
 the default value can be overridden by creating a
 ``/etc/pulp/server/plugins.conf.d/yum_distributor.json`` file containing
 ``{ "gpg_sign_metadata": true }``.

``gpg_cmd``
 Path to a signing command that will be used for signing repository
 metadata, if ``gpg_sign_metadata`` is set.

 The supplied signing command has to be an executable, accessible to the Apache
 user.

 The signing command will receive the name of the file to be signed as the first
 positional argument.

 Also, the signing command will be passed the name of the repository as the
 ``GPG_REPOSITORY_NAME`` environment variable.

 Additionally, if ``gpg_key_id`` is set (see below), its value will
 be passed to the signing command as the ``GPG_KEY_ID`` environment variable.
 This option should be added to the JSON configuration file described above,
 or may be supplied in the distributor configuration.
 Example: ``{ "gpg_sign_metadata": true, "gpg_cmd": "/usr/local/bin/sign.sh" }``

.. note:: ``gpg_cmd`` can only be set in the plugin configuration file
   ``/etc/pulp/server/plugins.conf.d/yum_distributor.json``. For security
   reasons, it cannot be set in the distrirbutor configuration or as an
   override option at publish time.

``gpg_key_id``
 Key ID to be used for signing. See ``gpg_cmd``.

``skip``
 List of content types to skip during the repository publish.
 If unspecified, all types will be published. Valid values are: rpm, drpm,
 distribution, errata, packagegroup.

``force_full``
 Boolean flag to indicate whether or not publish should be done from scratch.
 If unspecified the incremental publish will be performed when possible.

``remove_old_repodata``
 Boolean flag to indicate whether or not repodata past expiration are removed
 during publish. If not present it defaults to True. The default expiration is
 14 days. Files that present in repomd.xml are preserved no matter of
 their age.

``remove_old_repodata_threshold``
 If ``remove_old_repodata`` is true, this attribute specify maximal age of
 repodata in seconds that are not removed during publish. This attribute defaults
 to 14 days.

GPG Signing of Repository Metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If ``gpg_sign_metadata`` is ``True``, and ``gpg_cmd`` is not set,
a Pulp worker process will use the ``/usr/bin/gpg``
command to generate the repomd.xml.asc file. By default, ``gpg`` will look for a
GPG signing key under ``~/.gnupg/`` in the account that the Pulp worker process
runs as. This path can be overridden by exporting a ``$GNUPGHOME`` environment
variable in the pulp_workers startup script. The signing key must not be
protected by a password. The public key associated with the signing key must be
added to the ``gpgkey`` file configured on this distributor.

To generate a GPG signing key under ``~/.gnupg/`` in the account that the Pulp
worker process runs as::

    $ sudo -u pulp -H -s
    $ gpg --gen-key

(Use the default ``RSA and RSA``, ``2048`` bits, and ``key does not expire``
values, and simply press ``Enter`` when prompted for a password.)

To generate a GPG signing key under a different directory::

    $ mkdir -p /path/to/gnupg
    $ gpg --homedir /path/to/gnupg --gen-key
    $ chown -Rh pulp /path/to/gnupg

To remove the password from an existing GPG signing key::

    $ gpg --homedir /path/to/gnupg --list-keys
    $ gpg --homedir /path/to/gnupg --edit-key <Key ID> passwd

To export the public key associated with the GPG signing key::

    $ sudo -u pulp -H \
      gpg --homedir /path/to/gnupg --armor --export <Key ID> >> /path/to/gpgkey.file

To test the generation of a .asc file::

    $ sudo -u pulp -H -s
    $ cd
    $ touch test
    $ gpg --yes --homedir /path/to/gnupg --detach-sign --armor test
    $ rm test test.asc

**WARNING!** The example, as presented above, is not suitable for production
use. Unprotected GPG keys may be easily stolen. You may want to consider
more secure alternatives for your signing needs, like a dedicated server,
potentially with a
`Hardware Security Module <https://en.wikipedia.org/wiki/Hardware_security_module>`.

GPG Signing Of Repository Metadata With An Alternate Command
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In certain circumstances, using ``/usr/bin/gpg`` is not acceptable
as a signing solution, given that private keys cannot be passphrase-protected.

If a different signing command is necessary, one can set the ``gpg_cmd``
configuration variable to point to such command.

.. note:: ``gpg_cmd`` can only be set in the plugin configuration file
   ``/etc/pulp/server/plugins.conf.d/yum_distributor.json``. For security
   reasons, it cannot be set in the distrirbutor configuration or as an
   override option at publish time.


The signing command will be passed the following environment variables:
* ``GPG_CMD``
* ``GPG_KEY_ID`` (if specified in the configuration)
* ``GPG_REPOSITORY_NAME``

The signing command may decide on a key ID to use based on the repository name.

A minimal signing command using GPG could be::

    #!/usr/bin/python

    import os, subprocess, sys

    repo_id = os.environ.get("GPG_REPOSITORY_NAME", "")
    key_id = "my-devel-key" if repo_id.endswith("-devel") else "my-key"

    fname = sys.argv[1]

    cmd = ["/usr/bin/gpg", "--homedir", "/var/lib/pulp/gpg-home",
           "--detach-sign", "--default-key", key_id, "--armor",
           "--output", fname + ".asc", fname]

    sys.exit(subprocess.call(cmd))

This hypothetical script selects the signing key ``my-devel-key`` if the
repository name ends in ``-devel``, otherwise uses ``my-key``.

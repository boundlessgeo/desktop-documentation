QGIS Global Settings File
=========================

Starting from Boundless Desktop 1.1, QGIS supports global settings.

Almost all settings for QGIS application are stored using the `QSettings`
framework that is provided by the `Qt` library upon which QGIS is built.

For every setting value, an optional default value can be specified inline
in the application code, the global settings implementation allows the
inline default values to be overridden by an external and totally optional
global settings file (in `.ini` format).

Therefore, by providing a global settings file, the order for setting a default
value becomes:

- user profile settings file
- global settings file
- inline (code) default

The global setting file can be used to provide pre-configuration and/or
custom default values for all settings used inside QGIS.

QGIS Global settings and defaults can be set by editing the
:file:`qgis_global_setting.ini` file. Moreover, it is possible to overwrite the
path for the :file:`qgis_global_setting.ini` by using one of the following:

* Specifying the file's path using the ``--globalsettingsfile`` option when running
  QGIS. For instance:

  ::

     $ qgis --globalsettingsfile /home/user/qgis_global_setting.ini

* Setting the ``QGIS_GLOBAL_SETTINGS_FILE`` environment variable with the file
  location.

.. tip::

   Setting the ``qgis_global_setting.ini`` file path to a network shared folder,
   allows the system administrator to change global settings and defaults
   in several machines by only editing one file.

If none of the two above methods is used, QGIS will use the file's default location.
On Windows, the default folder location is:

``C:\ProgramData\Boundless\Desktop\2.0\Library\apps\qgis\qgis_global_setting.ini``

or, in case of single user installation:

``C:\Users\<username>\Boundless\Desktop\2.0\Library\apps\qgis\qgis_global_setting.ini``

.. commenting until future release for Mac OS

   While on Mac OS, the default location is:

   ``/Library/Boundless/Desktop/2.0/apps/QGIS for Boundless Desktop.app/Contents/Resources/qgis_global_setting.ini``

Exporting QGIS settings to INI format
-------------------------------------

Since Windows and macOS versions of QGIS don't store settings in INI
format, having to create a ``qgis_global_setting.ini`` file from scratch may be
a laborious task. For this purpose, a script is available to dump QGIS QgsSettings to a ``.ini``
file. The resultant file can then be used to help populate a
``qgis_global_settings.ini`` file.

#. Download :download:`qgis-settings-to-ini.py.zip <qgis-settings-to-ini.py.zip>`
   file to your machine and extract it.

#. From within QGIS, open the :guilabel:`Python Console`
   (:menuselection:`Plugins --> Python Console`).

#. In the :guilabel:`Python Console`, click the :guilabel:`Show Editor` button.

#. In the Editor toolbar, click the :guilabel:`Load Script`, browse to the
   :download:`qgis-settings-to-ini.py` file and click :guilabel:`Open`.

#. Finally, click the :guilabel:`Run script` button.

A message in the :guilabel:`Python Console` will inform you of the path to the
output file, or any runtime errors.

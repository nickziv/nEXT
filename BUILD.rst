Building nEXT Browser
========================================================================
NeXT browser is built with ECL and EQL, and is designed to be cross
platform compatible. To download a prebuilt-binary, please see the
"Releases" section of this repository.

OSX Compilation Instructions
------------------------------------------------------------------------
Installing Xcode Command Line Tools
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Before installing anything, install the Xcode Comand line tools. To
install the Xcode Command Line tools on OSX execute the following in a
terminal:

``xcode-select --install``

To verify that the command tools were successfully installed type:

``xcode-select -p``

the output of this command should be the path at which the command
line tools are installed.

Installing QT5 (Cross Platform GUI Toolkit)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
QT5 is available from a number of sources, the easiest is to install
it via a package manager such as Macports or Brew. However you
install, ensure that you install it with webkit support.

You can install QT5 via Macports with the following command:

``port install qt5``

You can also install QT5 via the official qt installer:

https://www.qt.io/download/

To test your installation/version of QT, execute ``qmake --version``.

Installing ECL (Embeddable Common Lisp)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Compilable tarballs can be found on the ECL website:

https://common-lisp.net/project/ecl/static/files/release/

To verify your installation of ECL:

- Execute ``/usr/local/bin/ecl``, it should show an ECL Prompt
- Verify the contents of ``/usr/local/lib`` contain the ecl libraries.
- Verify the contents of ``/usr/local/include/ecl`` contain the header files

Installing EQL5 Library & Executable (Embedded QT Lisp)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The source for EQL5 is available here:

https://gitlab.com/eql/EQL5

To build and install the EQL Library/Executable:

1. Clone the Repository into a directory where you plan to keep the
   installation, this cannot be moved after installation.
2. In ``src/`` exec: ``ecl -shell make.lisp`` This command generates
   ``src/libini_eql5.a``.
3. Edit ``src/eql5.pro`` commenting out all QT modules you do not
   require.

   - The webkit module is required for nEXT.

4. In ``src/`` exec: ``qmake eql5.pro``. This command generates
   the makefile.
5. In ``src/`` exec: ``make``
6. In ``src/`` exec: ``sudo make install``

To test your installation exec ``eql5 -qgui``, you should presented
with a REPL and a GUI.

After the installation, the following should be completed:

- ``/usr/local/bin`` contains an ``eql5`` executable
- ``/usr/local/include`` contains a folder named ``eql5``
- ``/usr/local/lib`` contains all built QT modules (selected in
  ``src/eql5.pro``) and libeql \*.dylib files

Compiling nEXT
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From the directory next/ execute the following commands to compile:

1. ``eql5 make``
2. ``qmake``
3. ``make``

Now you should have a compiled next.app, simply execute this app to
start nEXT browser.

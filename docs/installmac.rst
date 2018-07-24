Installing Scrapy: Mac OSX
---------------------------
Scrapy is built using Python, a programming language. There are multiple packages and dependencies that must be installed for Scrapy to work on your computer.
 
Install Xcode
^^^^^^^^^^^^^
Let’s set up your Mac so we can use Xcode, Apple’s developer software. Open your Terminal, type the following command, and press Enter:

.. code-block:: bash

    xcode-select --install
 
``Note: Everything you type into a command line is case-sensitive. For accuracy, you can copy and paste the commands you see in this guide into your program.``

|

Your computer will ask if you would like to install Xcode. Accept the install and let the download complete before continuing.

|

To confirm that Xcode was successfully installed, type the following command and press Enter:

.. code-block:: bash

    xcode-select -v
 
The terminal should show your version of Xcode.

Install Homebrew
^^^^^^^^^^^^^^^^^

Next, we need to make sure that Scrapy has everything it needs to run correctly on our computer. The first dependency we need to install is Homebrew, a package manager for Mac. Install it by typing the following command and pressing Enter:

.. code-block:: bash

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
 
``Note: If you are using OS X Lion 10.7 or below, you will have to use the following two commands:``

.. code-block:: bash

    cd /usr/local

    mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
 
The Terminal will tell you to press RETURN to continue the installation. It will also ask you to type in your password. This is the same password you use to login to your computer. As an added security measure, the Terminal won’t show your password when you type it. It might look like the Terminal isn’t responding, but this is normal. Go ahead and type in your password and press Enter to continue.
 
Update the .bashrc
^^^^^^^^^^^^^^^^^^^
Now that Homebrew is installed, you will need to make sure that your Mac will be able to find the packages. The following two commands will update your computer's .bashrc file, ensuring that your system can find what it needs:

.. code-block:: bash

    echo "export PATH=/usr/local/bin:/usr/local/sbin:$PATH" >> ~/.bashrc
 
    source ~/.bashrc
 
Install Python
^^^^^^^^^^^^^^^
We're almost done! Remember when I told you that Scrapy is built using Python? We need to make sure that the correct version of Python is installed on our computer. Use the following command to install Python using Homebrew:

.. code-block:: bash
    
    brew install python
 
We need to make sure that we have the latest version of Python. Use the first command to update Homebrew, then use the second command to get the latest version of Python:

.. code-block:: bash

    brew update

    brew update python
 
Install Scrapy
^^^^^^^^^^^^^^^
Now we can finally install Scrapy using pip, another package management system:
 
.. code-block:: bash
    
    pip install Scrapy
 
If you type Scrapy into the Terminal and press Enter, it should show some information about Scrapy commands. This lets you know that your installation was successful.

|

If you had problems during your installation, reference the Troubleshooting section at the end of this guide. If not, continue to the Using Scrapy section.

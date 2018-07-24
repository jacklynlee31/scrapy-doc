Installing Scrapy: Windows
--------------------------

Scrapy is built using Python, a programming language. There are multiple packages and dependencies that must be installed for Scrapy to work on your computer.
 
Install Miniconda
^^^^^^^^^^^^^^^^^^
The easiest way to install Scrapy on Windows is to use Miniconda, a package management system. Open your web browser and navigate to the following link: `https://conda.io/miniconda.html <https://conda.io/miniconda.html>`_

Download the latest, 64-bit version of Miniconda for Windows. Go ahead and install Miniconda on your computer.

``Note: Make note of where you installed Miniconda on your computer. You will have to navigate to this destination later.``
 
Update Path
^^^^^^^^^^^^
Now that Miniconda is installed, we need to make sure that our computer knows to use Miniconda’s scripts. To do that, we need to update our computer’s Path.

On your computer, navigate to the folder where Miniconda is installed. The path should show at the top of the window. Click the path and use CTRL+C to copy it to your clipboard.

Next, in your computer’s search bar, type in Environment Variables. You should see an option that says ‘Edit the system environment variables.’ Select this option, and a new window should open.
 
Find the PATH environment variable and select it. Click Edit, then click Add. Paste in the path to Miniconda that you copied to your clipboard.

Click Add. Paste in the path to Miniconda, but add \Scripts\ to the end of the path.

Go to the following: My Computer, Properties, Env Variables, Path
Add the Miniconda Folder
Add the Miniconda Folder + \Scripts\

Open the Command Prompt. Type the following command and press Enter:

.. code-block:: bash

    conda
 
``Note: Everything you type into a command line is case-sensitive. For accuracy, you can copy and paste the commands you see in this guide into your program.``

The Command Prompt should show that Miniconda is installed.
 
|

Install Scrapy
^^^^^^^^^^^^^^
Next, install Scrapy by typing the following command and pressing Enter:

.. code-block:: bash
    
    conda install -c condo-forge scrapy
 
You can confirm that the installation was successful by using the following command:

.. code-block:: bash

    run scrapy
 
After you press Enter, it should show information to confirm that Scrapy was installed. 

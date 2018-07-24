.. ScrapyDoc documentation master file, created by
   sphinx-quickstart on Sun Jul 22 15:46:54 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Scrapy User's Guide
====================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

It’s no secret that we live in a digital age. Thanks to technology, we have access to all kinds of information. However, too much information can be a curse. If you’re looking for something specific, you might have to go to multiple websites before you find the answer. The issue becomes even more complicated when you are working in academia or research. Researchers are often working with limited sources and an overload of information. So how do we, as researchers, navigate this new and complicated digital landscape?

Introducing Scrapy
------------------
Scrapy is a data scraper that helps you collect and extract data from the web. Data scrapers, also known as web crawlers, allow us to gather information from practically any website we choose. With Scrapy, we can get the data we need and export it to a readable format. More than ever before, we can control digital information.

|

Using a program like Scrapy requires a basic knowledge of HTML, CSS, your computer’s command line, and more. For new users, this can seem daunting. That’s where this guide comes in.

|

This guide will show you how to:

1. Use your computer’s command line to install Scrapy.
2. Use Scrapy to get information from a website, while adhering to web scraping best practices.
3. Export data in a readable format to be used for your next research project or paper.
 
To advance the field of research, we must be willing to take advantage of all that technology has to offer us. This guide will help you scrape the web while introducing you to a series of tools that will help you take control of your computer and the web.

Getting Started
---------------

To complete the steps in this guide, you will need the following programs:

- A web browser like Google Chrome, Firefox, or Safari.
- A command line program.
- A text editor like Notepad or TextEdit.
 
These programs should already be on your computer. If you are on a Mac, your command line will be called Terminal. If you are on a Windows PC, it will be called Command Prompt.

|

*Note: Terminal and Command Prompt are both extremely powerful tools. Do NOT run a command unless you know what it does first.*

|

If you are using Windows, skip the next section and go to the Installing Scrapy: Windows section. If you are working on a Mac, continue to the following section.
 
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

|

Installing Scrapy: Windows
--------------------------

Scrapy is built using Python, a programming language. There are multiple packages and dependencies that must be installed for Scrapy to work on your computer.
 
Install Miniconda
^^^^^^^^^^^^^^^^^^
The easiest way to install Scrapy on Windows is to use Miniconda, a package management system. Open your web browser and navigate to the following link: `https://conda.io/miniconda.html <https://conda.io/miniconda.html>`_

|
 
Download the latest, 64-bit version of Miniconda for Windows. Go ahead and install Miniconda on your computer.

``Note: Make note of where you installed Miniconda on your computer. You will have to navigate to this destination later.``
 
Update Path
^^^^^^^^^^^^
Now that Miniconda is installed, we need to make sure that our computer knows to use Miniconda’s scripts. To do that, we need to update our computer’s Path.
 
|

On your computer, navigate to the folder where Miniconda is installed. The path should show at the top of the window. Click the path and use CTRL+C to copy it to your clipboard.

|

Next, in your computer’s search bar, type in Environment Variables. You should see an option that says ‘Edit the system environment variables.’ Select this option, and a new window should open.

|
 
Find the PATH environment variable and select it. Click Edit, then click Add. Paste in the path to Miniconda that you copied to your clipboard.

|

Click Add. Paste in the path to Miniconda, but add \Scripts\ to the end of the path.

Go to the following: My Computer, Properties, Env Variables, Path
Add the Miniconda Folder
Add the Miniconda Folder + \Scripts\

|

Open the Command Prompt. Type the following command and press Enter:

.. code-block:: bash

    conda
 
``Note: Everything you type into a command line is case-sensitive. For accuracy, you can copy and paste the commands you see in this guide into your program.``

|

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
 
Using Scrapy
-------------
Web Scraping Best Practices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Now that we have everything installed on our computer, we can finally use Scrapy. But before we do, we need to remember that gathering information from the web can be a little complicated. There are some websites that don't want us to gather their data, regardless of content, and put strict guidelines in place to stop you from doing so.

|

Although there are ways to avoid being blocked when scraping data, the easiest way is to follow the rules the website provides.

|

Every website has a robots.txt file. It tells a web scraper if certain content on a website should be accessed. For example, go to Amazon's website, but use the following link: `https://www.amazon.com/robots.txt <https://www.amazon.com/robots.txt>`_

 
|

In this example, there is a list of links that shows where a web scraper can go. The site Disallows web scrapers from accessing multiple pages, but there are some pages - such as PrimeMusic or a wishlist - that Amazon allows.

|

It can be confusing to figure out what pages you are allowed to access. Thankfully, Scrapy does it for us using a ROBOTSTXT_OBEY field in a settings file.
 
|

Respect the perimeters that a website puts into place, and remember to never use a website's information for profit. For more information on web scraping best practices, go to this website: `https://www.promptcloud.com/blog/web-scraping-best-practices <https://www.promptcloud.com/blog/web-scraping-best-practices>`_

 
Create a New Project
^^^^^^^^^^^^^^^^^^^^
Let's get ready to scrape the web. In this guide, we are going to use Rotten Tomatoes as our example.

|

The first thing we want to do is create a new Scrapy project on our computer. Use your command line to navigate to the location where you want to start your project. This can be done using the cd command.
 
|

For example, Mac users would use the following command to access the Documents folder:
 
.. code-block:: bash

    cd Documents
 
 
Windows users, on the other hand, would use a command similar to the following (replacing username with your own username):

.. code-block:: bash 

    cd C:\Users\username\Documents
 
``Note: If you aren't sure where you are on your computer, use the command ls (Mac) or dir (Windows) and press Enter. You should see a layout of your current location. If you get too confused, quit out of the command line and reopen it. Your position should 'reset', allowing you to get to where you need to be.``
 
|

Now that you're in the folder, let's start a new Scrapy project using the following command:
 
.. code-block:: bash

    scrapy startproject tutorial
 
If you navigate to your chosen folder on your computer, you should see a brand new 'tutorial' directory. While you're in the directory, open the 'tutorial' folder. You should see a list of python files - they have the .py extension.
 
Configure your Settings.py
***************************
Before we begin, let’s make sure that the settings.py file I mentioned earlier is configured to follow the rules of a website’s robots.txt file. Open the settings.py file using your text editor and navigate to the following line:

.. code-block:: python

    # Obey robots.txt rules
    ROBOTSTXT_OBEY = True
 
Make sure that the ROBOTSTXT_OBEY field is set to True, without a hashtag (#) at the beginning of the line.

|

``Note: The # at the beginning of a line of code means that the line is a comment and won’t affect how the program works.``
 
|

It is also important to define your user agent when scraping a website. The user agent field tells a website who is trying to collect their information and why. While not required, the user agent field is an important part of web scraping best practices.

|

In the settings.py file, find the following section:

.. code-block:: python

    # Crawl responsibly by identifying yourself (and your website) on the user-agent
    #USER_AGENT = 'tutorial'

Remove the hashtag before USER_AGENT. Replace ‘tutorial’ with text that identifies you and, if applicable, the reason why you are doing the research project. Make sure your text is surrounded by single quotes.

|

For example, if you are doing a research project for a course, you could put the following:

.. code-block:: python

    USER_AGENT = 'Research Methods course project at The University of Arkansas'

Once the fields are set, save the file and return to your folder.

Create a Spider
****************
 
In the world of data scraping, you will often see ‘spiders’ mentioned. Thankfully, we aren’t talking about actual spiders. We use spiders to ‘crawl’ the code and extract the information that we need from a website.

|

Use the following command to create a new spider:
 
.. code-block:: bash

    scrapy genspider reviews link

In your tutorial directory, open the folder called spiders. You should see a new file called reviews_spider.py with the following contents:

.. code-block:: python
 
    # -*- coding: utf-8 -*-
    import scrapy
    
    
    class ReviewsSpider(scrapy.Spider):
        name = 'reviews'
        allowed_domains = ['link']
        start_urls = ['http://link/']
    
        def parse(self, response):
            pass
 
Let’s look at what this code is doing.

- allowed_domains: Tells the spider which domains it is allowed to crawl.
- start_urls: The URL that your spider will start with when it begins to crawl.

For now, let’s give our spider some information. Fill in the fields using the following information:

.. code-block:: python

    allowed_domains = ['rottentomatoes.com']

    start_urls = ['https://www.rottentomatoes.com/m/ghostbusters/reviews/?type=user']

There is also a section that begins with def parse; this will tell our spider how to process our data. For the purposes of this tutorial, update this section so that it looks like the following example:

.. code-block:: python
    
    def parse(self, response):
        #pass
        page = response.url.split("/")[-2]
        filename = 'reviews-%s.html' % page
        with open(filename, 'wb') as f:
            f.write(response.body)
        self.log('Saved file %s' % filename)

The code above is telling Scrapy to save the spider results as a HTML file.

Run the Spider
***************
 
Now that we have our first spider saved, configured, and ready to go, let’s run the file.

|

Open your command line and make sure you are in your project’s tutorial folder.
(Remember, if you aren’t sure where you are, use ls/dir to find out.)

|

Run the following command:

.. code-block:: bash

    scrapy crawl reviews
 
You are going to see a lot of information pop up into your command line that shows your spider crawling the information. Open your tutorial folder on your computer. You should see a file called reviews-reviews.html

|

Open the file using your web browser. You should see a simplified replica of the Rotten Tomatoes review page. So what did Scrapy just do? We gave it a URL and asked it to get us information. We didn’t give it specific criteria, so it returned everything it could find.
 
Extracting & Exporting Data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
 
We have the information, but it doesn’t do us any good unless we can pull specific parts from the webpage. Let’s say that we want to pull all of the review comments from the page.

|

Scrapy provides a tool called ‘scrapy shell’ that helps us work through our code and develop our spiders. Run scrapy shell using the following commands:

|

Mac

.. code-block:: bash

    scrapy shell 'https://www.rottentomatoes.com/m/ghostbusters/reviews/?type=user'
 
 
Windows

.. code-block:: bash

    scrapy shell "https://www.rottentomatoes.com/m/ghostbusters/reviews/?type=user"
 
 
A lot of information is going to come up in your command line, including some brief instructions and shortcuts that tell you how to navigate the scrapy shell.

|
 
``Note: The >>> at the beginning of the line tells you that you are in the scrapy shell. To exit the shell, you will have to type in quit().``
 


Find Selectors
***************

Data scrapers use selectors in order to grab specific parts of a webpage. A website is made up of different kinds of code including HTML and CSS. While HTML has different parts that tells a website how to organize information, CSS tells a website what to look like.

|
 
Open your web browser and navigate to the Ghostbuster’s review page. We can view the HTML and CSS of a page directly in our browser by using its Developer Tools:

|

**Chrome**

Right click the webpage and choose Inspect.
 
|

**Internet Explorer**

Press F12 to open Developer Tools.

|

**Safari**

Make sure that the Develop tab is enabled in your Safari Preferences. Then, open the Develop tab and click Show Web Inspector.

|
 
Find the first review on the page and right-click on it. You should see an option that says Inspect Element. When you inspect the element, you should see that section’s HTML appear in the Developer Tools window.

|
 
As you can see in the example above, when we move our cursor over the code, the associated information is highlighted. By doing this, we can easily figure out what selectors to use in our scrapy shell.

|
 
In this case, we see div class=”user_review” - this is the information we need.

|
 
Open your command line to go back to the scrapy shell. Use the following command:

.. code-block:: python

    response.css('.user_review::text')
 
We are telling the scrapy shell to grab the text from the user_review class.

|
 
The shell returns a lot of information, so let’s extract the text we need using the following command:

.. code-block:: bash

    response.css('.user_review::text').extract()
 
Now you should see all of the movie reviews on that page - text only!

Get Ready to Export
*******************

Let’s get ready to export our data. First, we need to change our information output. Let’s tell Scrapy to put our information in a csv file.

|

Open settings.py and add the following lines:

.. code-block:: python

    FEED_FORMAT = "csv"
    FEED_URI = "reviews.csv"
 

It doesn’t matter where you put the information. I put my lines near the top of the file, making it easier to find in the future.

|

Now we need to edit our spider. Open the reviews.py file that has your spider information in it. Remember the parse section? We need to update the section to include the selectors we found in the last section.

|

Update your parse section to the following:

.. code-block:: python
    
    def parse(self, response):
    
            #Extracting the content using css selectors
            reviews = response.css('.user_review::text').extract()
           
            #Give the extracted content row wise
            for item in zip(reviews):
                #create a dictionary to store the scraped info
                scraped_info = {
                    'review' : item[0],
                }
    
                #yield or give the scraped info to scrapy
                yield scraped_info


The spider will now loop through every review that belongs to the user_review class and put it into a python dictionary. We are then yielding the information; Scrapy returns the text in the user review back to us after it is extracted.

|

Save the file, then return to your command line. Scrape the website again using the following command:

.. code-block:: bash

    scrapy crawl reviews

There should now be a reviews.csv file in your tutorial folder. When you open it, you should see the column name ‘reviews’ with a list of the reviews on that page. The csv file can be imported to another program, like Excel or Google Sheets.


Wrapping Up
------------

Scrapy is a powerful program that includes a lot of built-in functionality. You can use the methods listed above to scrape multiple fields on a page. You can also use Scrapy to get information from multiple pages.

|

Every web scraper has its benefits and drawbacks. However, using a program like Scrapy will give you a good foundation moving forward even if you decide to use a different web scraper.

|

Visit Scrapy’s online documentation for more information on how to customize your data scrapers or if you have any questions regarding how to use Scrapy.

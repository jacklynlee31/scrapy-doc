********************
SCRAPY USER’S GUIDE
********************

It’s no secret that we live in a digital age. Thanks to technology, we have access to all kinds of information. However, too much information can be a curse. If you’re looking for something specific, you might have to go to multiple websites before you find the answer. The issue becomes even more complicated when you are working in academia or research. Researchers are often working with limited sources and an overload of information. So how do we, as researchers, navigate this new and complicated digital landscape?


===================
Introducing Scrapy
===================
Scrapy is a data scraper that helps you collect and extract data from the web. Data scrapers, also known as web crawlers, allow us to gather information from practically any website we choose. With Scrapy, we can get the data we need and export it to a readable format. More than ever before, we can control digital information.

Using a program like Scrapy requires a basic knowledge of HTML, CSS, your computer’s command line, and more. For new users, this can seem daunting. That’s where this guide comes in.

This guide will show you how to:

 1. Use your computer’s command line to install Scrapy.
 2. Use Scrapy to get information from a website, while adhering to web scraping best practices.
 3. Export data in a readable format to be used for your next research project or paper.

To advance the field of research, we must be willing to take advantage of all that technology has to offer us. This guide will help you scrape the web while introducing you to a series of tools that will help you take control of your computer and the web.

=================
Getting Started
=================

In order to complete the steps in this guide, you will need the following programs:

 *	A web browser like Google Chrome, Firefox, or Safari.
 *	A command line program.
 *	A text editor like Notepad or TextEdit.

Note: If you are unfamiliar with one of the words or programs mentioned in this guide, check the Glossary for a basic overview.

These programs should already be on your computer. If you are on a Mac, your command line will be called Terminal. If you are on a Windows PC, it will be called Command Prompt.

Note: Terminal and Command Prompt are both extremely powerful tools. Do NOT run a command unless you know what it does first.
If you are using Windows, skip the next section and go to the Installing Scrapy: Windows section. If you are working on a Mac, continue to the following section.

---------------------------
Installing Scrapy: Mac OSX
---------------------------

Scrapy is built using Python, a programming language. There are multiple packages and dependencies that must be installed for Scrapy to work on your computer.

^^^^^^^^^^^^^^
Install Xcode
^^^^^^^^^^^^^^

Let’s set up your Mac so we can use Apple’s developer software. Open your Terminal, type the following command, and press Enter:
xcode-select --install

Note: Everything you type into a command line is case-sensitive. For accuracy, you can copy and paste the commands you see in this guide into your program.

Your computer will ask if you would like to install Xcode. Accept the install and let the download complete before continuing.
To confirm that Xcode was successfully installed, type the following command and press Enter:

xcode-select -v

The terminal should show your version of Xcode.

^^^^^^^^^^^^^^^^^
Install Homebrew
^^^^^^^^^^^^^^^^^

Next, we need to make sure that Scrapy has everything it needs to run correctly on our computer.

Homebrew is a package manager for Mac. Install it by typing the following command and pressing Enter:

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Note: If you are using OS X Lion 10.7 or below, you will have to use the following commands:

cd /usr/local 
mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew

The Terminal will tell you to press RETURN to continue the installation. It will also ask you to type in your password. This is the same password you use to login to your computer. Homebrew is just making sure that the same person who owns the computer is also installing the program. 

When you type your password into the Terminal, it will look like nothing is happening. This is normal. As an added security measure, it won't show your password when you type it. Go ahead and type your password and press Enter.

^^^^^^^^^^^^^^^^^^^
Update the .bashrc
^^^^^^^^^^^^^^^^^^^

Now that Homebrew is installed, you will need to make sure that your Mac will be able to find the packages. The following two commands will update your computer's .bashrc file, ensuring that your system can find what it needs:

echo "export PATH=/usr/local/bin:/usr/local/sbin:$PATH" >> ~/.bashrc

source ~/.bashrc

^^^^^^^^^^^^^^^
Install Python
^^^^^^^^^^^^^^^

We're almost there! Remember when I told you that Scrapy is built using Python? Well, we need to make sure that Python is installed on our computer using the following command:

brew install python

Your Mac should already come with Python installed, but we need to make sure that we have the latest version. Use the following two commands:

brew update
brew update python

^^^^^^^^^^^^^^^
Install Scrapy
^^^^^^^^^^^^^^^

Now we can finally install Scrapy using the following command:

pip install Scrapy

If you type Scrapy into the Terminal and press Enter, it should show some information about Scrapy commands. This lets you know that your installation was successful.

If you had problems during your installation, reference the Troubleshooting section at the end of this guide. If not, continue to the Using Scrapy section.

---------------------------
Installing Scrapy: Windows
---------------------------

Scrapy is built using Python, a programming language. There are multiple packages and dependencies that must be installed in order for Scrapy to work on your computer.

^^^^^^^^^^^^^^^^^^
Install Miniconda
^^^^^^^^^^^^^^^^^^

The easiest way to install Scrapy on Windows is to use Miniconda, a package management system. Open your web browser and navigate to the following link: (LINK)

Choose the latest version and choose the 64-bit installer.

Note: Make note of where you installed Miniconda on your computer. You will have to navigate to this destination later.

Note: Everything you type into a command line is case-sensitive. For accuracy, you can copy and paste the commands you see in this guide into your program.

^^^^^^^^^^^^
Update Path
^^^^^^^^^^^^

Although Miniconda is installed, you need to make sure that your Command Prompt can find the program and use its scripts.

On your computer, navigate to the folder where Miniconda is installed. The program's path should show at the top of the window. Click the path and use CTRL+C to copy it to your clipboard.

Go to the following: My Computer, Properties, Env Variables, Path
Add the Miniconda Folder
Add the Miniconda Folder + \Scripts\

Restart the Command Prompt - close it and open it again - so that the changes you just made will take place. Type conda into the Command Prompt and press Enter. It should [CONFIRM THAT MINICONDA IS INSTALLED].

^^^^^^^^^^^^^^^
Install Scrapy
^^^^^^^^^^^^^^^

Next, install Scrapy by typing the following command and pressing Enter:

conda install -c condo-forge scrapy

You can confirm that the installation was successful by using the following command:

run scrapy

After you press Enter, it should show information to confirm that Scrapy was installed.

=============
Using Scrapy
=============
Information here.

----------------------------
Web Scraping Best Practices
----------------------------

Now that we have everything installed on our computer, we can finally use Scrapy. But before we do, we need to remember that gathering information from the web can be a little complicated. There are some websites that don't want us to gather their data, regardless of content, and put strict guidelines in place to stop you from doing so.

Although there are ways to avoid being blocked when scraping data, the easiest way is to follow the rules the website provides.

Every website has a robots.txt file. It tells a web scraper if certain content on a website should be accessed. For example, go to Amazon's website, but use the following link: https://www.amazon.com/robots.txt

In this example, there is a list of links that shows where a web scraper can go. The site Disallows web scrapers from accessing multiple pages, but there are some pages - such as PrimeMusic or a wishlist - that Amazon Allows.

It can be confusing to figure out what pages you are allowed to access. Thankfully, Scrapy does it for us using a ROBOTSTXT_OBEY field in a settings file.

Respect the perimeters that a website puts into place, and remember to never use a website's information for profit. For more information on web scraping best practices, go to this website.

---------------------
Create a New Project
---------------------

Let's get ready to scrape the web. In this guide, we will be using Rotten Tomatoes as our example.

The first thing we want to do is create a new Scrapy project on our computer. Use your command line to navigate to the location where you want to start your project. This can be done using cd. I've decided that I want to save my project in my Documents folder, so I'll use the following command:

cd Documents

Your command line should always start at the 'base' of your computer. Mac users should be able to use the same command to go into their Documents folder. They can also navigate to a different folder using cd.

Windows users can use the following command to go to their Documents folder: COMMAND. Feel free to replace Documents with Desktop/etc for a different location.

Note: If you aren't sure where you are on your computer, use the command ls (Mac) or dir (Windows) and press Enter. You should see a layout of your current location. If you get too confused, quit out of the command line and reopen it. Your position should 'reset', allowing you to get to where you need to be.

Now that you're in the folder, let's start a new Scrapy project using the following command:

scrapy startproject tutorial

If you navigate to your chosen folder on your computer, you should see a brand new 'tutorial' directory. While you're in the directory, open the 'tutorial' folder. You should see a list of python files - python files have the .py extension.

INFORMATION ABOUT CHANGING THE SETTINGS.PY FILE

We want to have a place to store all of the information we scrape from Rotten Tomatoes. Scrapy calls these places items. Think of each item as a container that will hold all of our data.

First, let's choose what we want to scrape. Maybe we need a list of movie reviews to code for our research project. For the purposes of this tutorial, let's choose 1984's Ghostbusters.

Navigate to the page in Rotten Tomatoes, then scroll down and click on Audience Reviews.

(SCREEN?)

What data do we want to get from this page? Let's get the following information:
 *	Reviewer name
 *	Number of stars awarded
 *	Date
 *	Content of the review

Let's tell Scrapy that we want to get this information. Go back to the tutorial folder on your computer and open the items.py file. Open it in Notepad or TextEdit. You can also use a code editor to open the file, if you have one on your computer.

Your items.py file should look similar to the following:

SCREEN

All we need to do is tell Scrapy what information we want to collect. Scrapy gives us the following template: 
name = scrapy.Field()

Let's add our own. Create a new line below the example, but above where it says 'pass'. Type the following:

reviewer = scrapy.Field()

----------------
Create a Spider
----------------

In Scrapy, spiders are used to scrape information from the web. They are classes that you define with your own information. Spiders tell Scrapy how to navigate a website and what information to grab.

Open Notepad or TextEdit and paste the following code:


import scrapy


class QuotesSpider(scrapy.Spider):
    name = "quotes"

    def start_requests(self):
        urls = [
            'http://quotes.toscrape.com/page/1/',
            'http://quotes.toscrape.com/page/2/',
        ]
        for url in urls:
            yield scrapy.Request(url=url, callback=self.parse)

    def parse(self, response):
        page = response.url.split("/")[-2]
        filename = 'quotes-%s.html' % page
        with open(filename, 'wb') as f:
            f.write(response.body)
        self.log('Saved file %s' % filename)


Let's look at what this code is doing. It's defining our Spider and giving it a name ("reviews"). It lists the URL to scrape from, then parses the response.

scrapy crawl reviews

Saved in a reviews.html file. If you open this file, you should see a Rotten Tomatoes page. Remember when we put a URL in our Spider file? This is that URL.

scrapy shell (MAC AND WINDOWS?)

Response.css(".user_review::text").extract()[1]

================
Troubleshooting
================

================
Glossary
================
Command line: A powerful program used to interact with your computer.

Using Scrapy
-------------
Web Scraping Best Practices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Now that we have everything installed on our computer, we can finally use Scrapy. But before we do, we need to remember that gathering information from the web can be a little complicated. There are some websites that don't want us to gather their data, regardless of content, and put strict guidelines in place to stop you from doing so.

Although there are ways to avoid being blocked when scraping data, the easiest way is to follow the rules the website provides.

Every website has a robots.txt file. It tells a web scraper if certain content on a website should be accessed. For example, go to Amazon's website, but use the following link: `https://www.amazon.com/robots.txt <https://www.amazon.com/robots.txt>`_

In this example, there is a list of links that shows where a web scraper can go. The site Disallows web scrapers from accessing multiple pages, but there are some pages - such as PrimeMusic or a wishlist - that Amazon allows.

It can be confusing to figure out what pages you are allowed to access. Thankfully, Scrapy does it for us using a ROBOTSTXT_OBEY field in a settings file.

Respect the perimeters that a website puts into place, and remember to never use a website's information for profit. For more information on web scraping best practices, go to this website: `https://www.promptcloud.com/blog/web-scraping-best-practices <https://www.promptcloud.com/blog/web-scraping-best-practices>`_

 
Create a New Project
^^^^^^^^^^^^^^^^^^^^
Let's get ready to scrape the web. In this guide, we are going to use Rotten Tomatoes as our example.

The first thing we want to do is create a new Scrapy project on our computer. Use your command line to navigate to the location where you want to start your project. This can be done using the cd command.

For example, Mac users would use the following command to access the Documents folder:
 
.. code-block:: bash

    cd Documents
 
 
Windows users, on the other hand, would use a command similar to the following (replacing username with your own username):

.. code-block:: bash 

    cd C:\Users\username\Documents
 
``Note: If you aren't sure where you are on your computer, use the command ls (Mac) or dir (Windows) and press Enter. You should see a layout of your current location. If you get too confused, quit out of the command line and reopen it. Your position should 'reset', allowing you to get to where you need to be.``

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

``Note: The # at the beginning of a line of code means that the line is a comment and won’t affect how the program works.``

It is also important to define your user agent when scraping a website. The user agent field tells a website who is trying to collect their information and why. While not required, the user agent field is an important part of web scraping best practices.

In the settings.py file, find the following section:

.. code-block:: python

    # Crawl responsibly by identifying yourself (and your website) on the user-agent
    #USER_AGENT = 'tutorial'

Remove the hashtag before USER_AGENT. Replace ‘tutorial’ with text that identifies you and, if applicable, the reason why you are doing the research project. Make sure your text is surrounded by single quotes.

For example, if you are doing a research project for a course, you could put the following:

.. code-block:: python

    USER_AGENT = 'Research Methods course project at The University of Arkansas'

Once the fields are set, save the file and return to your folder.

Create a Spider
****************
 
In the world of data scraping, you will often see ‘spiders’ mentioned. Thankfully, we aren’t talking about actual spiders. We use spiders to ‘crawl’ the code and extract the information that we need from a website.

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

Open your command line and make sure you are in your project’s tutorial folder.
(Remember, if you aren’t sure where you are, use ls/dir to find out.)

Run the following command:

.. code-block:: bash

    scrapy crawl reviews
 
You are going to see a lot of information pop up into your command line that shows your spider crawling the information. Open your tutorial folder on your computer. You should see a file called reviews-reviews.html

Open the file using your web browser. You should see a simplified replica of the Rotten Tomatoes review page. So what did Scrapy just do? We gave it a URL and asked it to get us information. We didn’t give it specific criteria, so it returned everything it could find.
 
Extracting & Exporting Data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
 
We have the information, but it doesn’t do us any good unless we can pull specific parts from the webpage. Let’s say that we want to pull all of the review comments from the page.

Scrapy provides a tool called ‘scrapy shell’ that helps us work through our code and develop our spiders. Run scrapy shell using the following commands:

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
 
Open your web browser and navigate to the Ghostbuster’s review page. We can view the HTML and CSS of a page directly in our browser by using its Developer Tools:


**Chrome**

Right click the webpage and choose Inspect.


**Internet Explorer**

Press F12 to open Developer Tools.


**Safari**

Make sure that the Develop tab is enabled in your Safari Preferences. Then, open the Develop tab and click Show Web Inspector.
 
Find the first review on the page and right-click on it. You should see an option that says Inspect Element. When you inspect the element, you should see that section’s HTML appear in the Developer Tools window.
 
As you can see in the example above, when we move our cursor over the code, the associated information is highlighted. By doing this, we can easily figure out what selectors to use in our scrapy shell.
 
In this case, we see div class=”user_review” - this is the information we need.
 
Open your command line to go back to the scrapy shell. Use the following command:

.. code-block:: python

    response.css('.user_review::text')
 
We are telling the scrapy shell to grab the text from the user_review class.
 
The shell returns a lot of information, so let’s extract the text we need using the following command:

.. code-block:: bash

    response.css('.user_review::text').extract()
 
Now you should see all of the movie reviews on that page - text only!

Get Ready to Export
*******************

Let’s get ready to export our data. First, we need to change our information output. Let’s tell Scrapy to put our information in a csv file.

Open settings.py and add the following lines:

.. code-block:: python

    FEED_FORMAT = "csv"
    FEED_URI = "reviews.csv"
 

It doesn’t matter where you put the information. I put my lines near the top of the file, making it easier to find in the future.

Now we need to edit our spider. Open the reviews.py file that has your spider information in it. Remember the parse section? We need to update the section to include the selectors we found in the last section.

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

Save the file, then return to your command line. Scrape the website again using the following command:

.. code-block:: bash

    scrapy crawl reviews

There should now be a reviews.csv file in your tutorial folder. When you open it, you should see the column name ‘reviews’ with a list of the reviews on that page. The csv file can be imported to another program, like Excel or Google Sheets.

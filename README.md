
Intranet Stack Exchange
-----------------------
A tool to enable using the [StackExchange datadumps](https://archive.org/details/stackexchange)
in offline environments (e.g. internal network of a company, not connected to the
internet).

Here are a few screenshots:

 * <http://www.mediafire.com/view/l9rdrmi6i7zz398/ISE_SingleSite.png>
 * <http://www.mediafire.com/view/io5veplpn1k2q99/ISE_SearchResults.png>
 * <http://www.mediafire.com/view/nv1vzy31ib3mrdi/ISE_QuestionAndAnswers.png>

This application will enable organizations, whose network is isolated from the web, to enjoy
the massive Q&A database StackExchange has publicly released, in various topics ranging from
Programming to Movies to Math and much more.

Questions, ideas and bugs - please contact me: ran@ranlevi.com

## Prerequisites:
* Python 2.7
* A Linux server with admin privileges


## Dependencies:

* [Bottle](http://bottlepy.org/docs/dev/index.html)
* [Whoosh](https://pypi.python.org/pypi/Whoosh)
* [CherryPy](www.cherrypy.org)

* Known issues:  None.

## Basic Usage:

  * Clone (or Unzip) the git to some directory.
  * install the required libraries: either run "pip install -r requirements.txt" for 
    automatic install, or install the libraries (Whoosh, bootle, etc.) manually.
  * Go to the /Sources directory
  * Run:

        python Indexer.py
    
    The app will index all the datadumps in the /Datadumps folder.

  * Run: 

        python Webserver.py <optional: server's ip address> <optional: port number>

    The webserver will start.

    If no IP or Port number were given, the server will launch in 'development mode':
    localhost, 8080.

    Open the web browswer, and go to the server's ip address. e.g.:
    "http://192.1.2.3:80/" or "http://localhost:8080/"
    You will get a browesable version of the Stack Exchange sites. 
    
##  Advanced Options:

  1. The application comes with 3 sample databases: Ardunio, Astronomy and Beer. To add
     more databases, go to the Internet-Archive download page for data-dumps
     (https://archive.org/details/stackexchange), and download the databases you want.
     Unzip the downloaded databases into the /Datadumps folder, under a folder with the database's name.

   For example:
  
     /Datadumps
        /Beer
        /Astronomy
        /Ardunio
        /Movies
            Posts.xml
            Comments.xml
            ...

  2. It is possible to index only selected database(s), to save time. in /Sources, type: python Indexer.py debug

  3. The website I used for the application is minimal and basic. You can modify it easily by
     changing the HTML, CSS, etc. in the /Sources/views and /Sources/static folders.
     Alternatively, you can design you're own website from scratch! The Webserver.py module calls functions
     in the Indexer.py & SearchEngine.py modules - so you can modify only the Webserver.py module for a whole
     new user experience.

**Note:**
This work is partly inspired by Stackdump (https://bitbucket.org/samuel.lai/stackdump). Thanks, Samuel! :-)

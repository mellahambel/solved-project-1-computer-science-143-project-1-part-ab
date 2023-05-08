Download Link: https://assignmentchef.com/product/solved-project-1-computer-science-143-project-1-part-ab
<br>
<h1>TuneSearch</h1>




In this project, you will design a (very) simple search engine to search for song lyrics. We will call this search engine ​<em>TuneSearch</em>​ for lack of creativity and take a trip back to the 1990s, a very exciting time for the World Wide Web and music if I say so myself.




Before Google debuted in 1998, there were a ton of other search engines with their own pros and cons and technical achievements such as AltaVista, Excite, Lycos, Yahoo (it was a search engine at one point), HotBot, Dogpile, Ask Jeeves, WebCrawler, Inktomi, MetaCrawler, InfoSeek and All the Web. Most of these search engines used some form of an index, inverted index, and some ranking method. In later years, song lyric sites started popping up. In this project, we will use a sample of data from LyricsFreak.com.




In this project, students will build a basic search engine for song lyrics backed by several technologies, but most importantly PostgreSQL. Just think, this project could have made you a billionaire back in the 90s.




The other technologies that will be used in this project (​<em>though students will not need to touch most of it</em>​) are:




<ol>

 <li><a href="https://nginx.org/en/"><strong>Nginx</strong></a><u>​</u><a href="https://nginx.org/en/">,</a> a high performance HTTP/web server. It has many other uses as a reverse proxy server, mail proxy server and a generic TCP/UDP proxy server, but we are only using the web server part.</li>

 <li><a href="http://flask.pocoo.org/"><strong>Flask</strong></a>​, a popular micro-platform for web and API development. Flask is a great way to prototype web projects and host small projects quickly. It is fairly lightweight.</li>

 <li><a href="https://uwsgi-docs.readthedocs.io/en/latest/"><strong>uWSGI</strong></a>​, is a protocol and serves as a “glue” between Nginx and Flask.</li>

 <li><a href="http://jinja.pocoo.org/"><strong>Jinja2</strong></a><u>​</u><a href="http://jinja.pocoo.org/"><strong>,</strong></a> ​is a templating engine used by Flask. Developers write standard HTML files and embed special tokens where variables passed to the template should be displayed.</li>

 <li><a href="https://www.postgresql.org/"><strong>PostgreSQL</strong></a><u>​</u><a href="https://www.postgresql.org/">,</a> is an open source object-relational database management system with an​ emphasis on extensibility and standards compliance. It can handle workloads ranging from small single-machine applications to large Internet-facing applications with many concurrent users.</li>

 <li><a href="http://initd.org/psycopg/"><strong>psycopg2</strong></a><strong>​</strong>, a Python package for interacting with PostgreSQL from Python.</li>

 <li><a href="https://www.python.org/"><strong>Python 3</strong></a><strong><u>​</u></strong><a href="https://www.python.org/">,</a> the world’s best programming language.</li>

</ol>




Since this is the beginning of a databases and data systems class, the focus of this project is on <strong>writing queries</strong>​ and the amount of new Python code that must be written should be minimal.

<h1>System Setup</h1>

To help students set up the uniform environment for the class project, we will be using <a href="https://www.virtualbox.org/">VirtualBox</a><u>​</u> to run the Linux operating system in a <u>​</u><a href="https://www.virtualbox.org/manual/ch01.html">virtual machine</a><u>​</u><a href="https://www.virtualbox.org/manual/ch01.html">.</a> VirtualBox allows a single machine to share resources and run multiple operating systems simultaneously. You will need to download the following files




<ul>

 <li><a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox binary file</a> <u>​ </u>for your host Operating System. The latest version is 6.0.4 and we have not experienced problems with it.</li>

 <li>VirtualBox Image: ​<a href="https://drive.google.com/open?id=1R1lGzY50J3UttndbQUojKkXubpPmgeFG">CS143-19S-P1.ova </a>​- This is a very large file (~2.5GB), so it may take a while to download.</li>

</ul>




and follow our <u>​</u><a href="https://docs.google.com/document/d/1eTzIW2VqxQS63PsnGZeVgG_uJAtao8T2ADEnjsB8ht0/edit">VirtualBox setup instruction</a><u>​</u> to install VirtualBox on your own machine. The provided virtual machine image is based on Ubuntu 18.04 LTS, PostgreSQL 10.6, Nginx 1.14, Flask 1.0.2, Python 3.6.7.




If you have access to an equivalent machine that has PostgreSQL, Nginx, Python 3, and Flask installed, you may use it instead of the virtual machine image. In this case, we do recommend setting up Python and Flask using virtualenv. However, please note that we ​<strong>will not</strong>​ provide support for systems other than the virtual machine image, and that your project MUST be runnable on the provided virtual machine. We will be using the virtual machine image for grading purposes, and if your submission does not work within this setup, you may get zero points. We cannot make any exceptions to your project schedule for problems incurred by using your own computing facilities.




<h1>Project</h1>

Your project is to build a simple song lyrics search engine. Your system manages all of its data at the back-end in a PostgreSQL database and provides a Web interface to the users at the front-end. While this task may sound daunting at first, you will be surprised how easy and helpful a commercial DBMS is for such a project.




To develop Project 1 all students will use the PostgreSQL DBMS and the Ubuntu Linux operating system. You will also use the Python programming language to access PostgreSQL and the Flask microplatform (powered by Nginx) to provide a Web interface. While there are many other ways to develop Web applications, and while Apache and PHP is one of the most popular method these days to implement a database-backed server for a small-to-medium scale Web site, we want to use a standard language across both CS 143 projects and also introduce students to Flask, which is very popular in the data community and lightweight. We will provide online references that will help you learn Python and PostgreSQL. We will also give you a considerable amount of real data to populate your system.




For Project 1, we will expect certain minimal functionality in your system – beyond that, the sky’s the limit. Minimal functionality includes a variety of queries and searching capabilities over the data in your system. Various integrity constraints must be monitored. Although you will use PostgreSQL, which has reasonable transaction support, multi-user issues are not a focus of the project.




The main reason for using PostgreSQL in lieu of MySQL this quarter is that it follows the ANSI SQL standard presented in the textbook much, much more closely than does MySQL. While MySQL may be more popular (currently) and in some cases easier to use, it only implements a subset of the ANSI SQL standard and even fewer features.




Project 1 consists of two parts:




<h2>Part A: Creating Schemas and Loading Data</h2>

In this part, you will get familiar with the overall project environment and learn basic Python if you do not know them yet. You will write several queries to create database tables with the correct data types, keys and constraints and then load data into these tables. <strong>This part does not require</strong>​         <strong> Python, </strong>though some students may wish to practice by writing a Python script, using the psycopg2​               package, to load the data from the script instead.




<h2>Part B: PostgreSQL Backed Search Engine</h2>

In this part, you will write queries and some Python code that fetches search results given an initial search query, and display the results on a search page. This task involves SELECT statements, JOINs and subqueries and will provide good practice for the midterm.




TuneSearch Project 1 Part A

<h1>Partners</h1>

The CS143 project may be completed in teams of one or two students. The choice is up to each student. Partnership rules consist of the following:




<ul>

 <li>An identical amount of work is expected and the same grading scale is used regardless of the size of your team.</li>

 <li>If you work in a team of two, choose your partner carefully. Partners are permitted to “divorce” at any time during the course, and “single” student may choose to find a partner as the project progresses. However students from divorced teams may not form new teams or join other teams.</li>

 <li>Partners in a team will receive exactly the same grade for each project part submitted jointly.</li>

</ul>

If you have two students in your team, please make sure to submit your work jointly – do ​<em>not</em>​ turn your project in twice, once for each partner.




<h1>Scope</h1>

The primary purpose of Part A is the following:




<ol>

 <li>To provide you with the data you need to complete the project.</li>

 <li>To create the PostgreSQL relation/table schemas you will need to complete the project.</li>

 <li>To load the data.</li>

 <li>To make sure the VirtualBox image is working correctly to ensure your further success.</li>

</ol>




We provide you with a whole bunch of basic information to get everyone up-to-speed on our computing systems and the languages and tools we will be using. Those of you who have used a database server before (remember, we do not expect any familiarity), will find this part nearly trivial. Those of you who haven’t will find it mostly straightforward. With all that said, ​<em>please don’t start at the last minute</em>​ — as with all programming and systems work, everything takes a bit of time, and unforeseen snafus do crop up.







<h1>System Setup</h1>

We will be using VirtualBox to run the Linux operating system in a virtual machine. VirtualBox allows a single machine to share resources and run multiple operating systems simultaneously. Read our VirtualBox setup instruction and follow the instructions to install VirtualBox and our virtual-machine image on your own machine.




The provided virtual machine image is based on Ubuntu 18.04.2, PostgreSQL 10.1, Nginx, Python 3 and Flask. You will need to use the provided VirtualBox guest OS to develop and test all projects for this class.




Your VirtualBox guest is essentially a Linux machine. Your guest is accessible from your host through secure shell (SSH) at localhost​          port ​     <strong>1422</strong>​     with username ​               cs143​   and password ​ cs143​   .​ The web server and framework (nginx + uwsgi + Flask) is accessible from your host at ​localhost port ​<strong>1480</strong>​.




<strong>If you have any problems with the image, let the TAs know ASAP on Piazza. </strong>

<h1>The Big Picture: What we are Going to Do</h1>




In this project, we are creating a very basic search engine a la the 1990s, called TuneSearch. We will assume that a TuneSearch user enters his/her query as a space-delimited string of tokens/words. The user can then use one of two radio buttons labeled AND or OR to determine how we will search for the terms. If OR is selected, any song that contains any of the words will be returned as search results. If AND is selected, only songs that contain ALL of the words will be returned. Nowadays, search engines like Google assume AND queries, but believe it or not, several search engines used to require the user to specify how to create the boolean predicate.




<em>An example of searching from some lyrics: </em>




<em>An example of an AND query:</em>
















<em>The results: </em>

<em> </em>




But it is not just enough to search for words in a song and present them to the user. We also need to <em>rank </em>​them in a way that makes sense. This is very complicated for modern search engines, so we are going to keep it simple. One way is to just rank by how many times the words in the query appear in each song result. A slightly more sophisticated method that we will use involves using TF-IDF, which is a metric that explains how ​<em>important </em>​a particular word is in a song. Words with high TF-IDF values are those that will lead to more specific results. TF stands for term frequency, and is simply the number of times a word appears in a song. IDF stands for Inverse Document Frequency. Its reciprocal is the number of songs where the particular term is used. TF-IDF will prioritize songs that use a rare word frequently. While a set of songs may contain the word ​<em>raspberry</em>​, it is rare enough that the song ​<em>Raspberry Beret </em>​by Prince should be ranked first, because the word ​<em>raspberry</em> appears many times compared to others and not very often in other songs. A word such as ​<em>and </em>​has a very low TF-IDF because it appears in practically all songs. We will discuss TF-IDF more in the specification for Project 1B. ​<strong>For project 1A, it is important to know that there is a TF-IDF score for each song-token pair.</strong>

<h1>The Data</h1>

The dataset consists of lyrics from several thousand songs collected from the popular website <a href="http://www.lyricsfreak.com/">LyricsFreak</a><u>​</u> in CSV format. This data was heavily cleaned by your professor. In your VirtualBox image, there is a directory named ​data​. This directory contains three files:




<ol>

 <li>csv​ contains data about each artist in the dataset. There is an ID number, and their name in quotation marks. The quotation marks are necessary because some names may have commas in them.</li>

 <li>csv​ contains data about each song in the dataset. There is an ID for both the song and the artist, the name of the song in quotation marks, and the suffix of the LyricsFreak URL where the data came from. For example, the song ​<em>Ants Marching</em>​ by</li>

</ol>

Dave Matthews Band has the URL

/d/dave+matthews+band/ants+marching_20036621.html​, which, as a full URL is <a href="http://www.lyricsfreak.com/d/dave+matthews+band/ants+marching_20036621.html">http://www.lyricsfreak.com/d/dave+matthews+band/ants+marching_2 </a><a href="http://www.lyricsfreak.com/d/dave+matthews+band/ants+marching_20036621.html">0036621.html</a>

<ol start="3">

 <li>csv contains data about the individual words (referred to as ​ ​<em>tokens</em>​) used in each song. There is an ID for the song, a token, and the number of times that word was used in the song. This table basically contains TF, or at least part of it.</li>

</ol>




<h1>The Database</h1>

Your VirtualBox instance contains a Postgres database server on it. You can access the command-line interface with the command ​psql​. You will be authorized as user ​cs143​, though note that this username did not need to be the same as the Linux username. We have set the password to ​cs143​.




If you are familiar with MySQL, you will immediately notice some differences. Let’s start with looking at what databases are stored in this server by using the ​l​ command (lowercase L). Every database user (not necessarily Linux user) has their own database that they can do whatever they want with thus there are databases for ​cs143​ and postgres. ​postgres​ is a system user that is created when the server is installed. We will only be using user ​cs143​. There is a ​TEST database you are free to use for whatever you like. You can use ​              ​cs143​ or TEST​ for development purposes if you wish. There are databases for homework, and searchengine​. You will use database ​searchengine​ for project 1. ​template0​ and template1​ are system databases — don’t modify or delete them. ​template1​ is a backup of template0.​




Below are a few more commands that will be of use:




<table width="624">

 <tbody>

  <tr>

   <td width="208"><strong>Command </strong></td>

   <td width="208"><strong>Postgres / psql </strong></td>

   <td width="208"><strong>MySQL Equivalent </strong></td>

  </tr>

  <tr>

   <td width="208">List databases</td>

   <td width="208">l</td>

   <td width="208">SHOW DATABASES;</td>

  </tr>

  <tr>

   <td width="208">List relations</td>

   <td width="208">d</td>

   <td width="208">SHOW TABLES;</td>

  </tr>

  <tr>

   <td width="208">Show schema for relation ​<em>r</em></td>

   <td width="208">d &lt;r&gt;</td>

   <td width="208">DESCRIBE &lt;r&gt;;</td>

  </tr>

  <tr>

   <td width="208">Switch databases</td>

   <td width="208">c &lt;dbname&gt;</td>

   <td width="208">USE &lt;dbname&gt;;</td>

  </tr>

 </tbody>

</table>

<em>All SQL queries must be suffixed with a semicolon, but commands do not need to be. </em>

<h1>Task 0: Load the Skeleton</h1>

Most of the Python code and web pages are already written for you. You can download these files at this <u>​</u><a href="https://drive.google.com/open?id=122BQ4DA6OT27dWo4CGv_6tbL68WGqB8g">link</a>​. Navigate to your ​vm-shared​ directory on your system and unzip the file so that your directory structure looks like the following:




vm-shared |

|– logs

|–SearchEngine




Depending on your operating system, or your zip client, it may create a directory named after the ZIP file. If this happens, move everything within that directory so that it is directly under vm-shared​. This content is accessible on your VM at directory ​www​ in the home directory.

<h1>Task 1: Create the Schema</h1>

Your first task is to create the database schema for this problem. You will design four tables with appropriate names, specify types for each of the attributes, and specify the proper primary and foreign keys. The fourth table will contain the TF-IDF score, even though we are not computing it yet. What attributes should it contain? What should the keys be?

<em>This type of problem would usually be solved with a system like ElasticSearch backed by an indexing engine like Lucene, but here we will use PostgreSQL and text processing code your professor has written for you. </em>




Create a directory in your shared folder named  ​sql​. Create a file ​schema.sql​ that creates the relations in your schema. A SQL file is simply a collection of SQL queries that are executed in order. For your sanity, you are required to drop relations if they already exist. If you do not do this, Postgres will throw an error at each query saying the relation already exists.




You will be graded on using the correct data types without being wasteful, picking the correct keys, and of course, not yielding any errors or warnings.




<h1>Task 2: Load the Data</h1>

This task in some ways will allow you to check your work for any major problems from Task 1.




Now you will load the data into the schema you just created. There are a variety of ways to do this including command-line utilities, or writing a Python script with the ​psycopg2​ package. PostgreSQL uses the ​copy ​(and/or ​COPY​ construct)​ ​command to read delimited files into Postgres pretty easily. Please take a <u>​</u><a href="https://www.postgresql.org/docs/10/sql-copy.html">look here for more information</a><u>​</u><a href="https://www.postgresql.org/docs/10/sql-copy.html">.</a> You will want to pay attention to the file format, delimiter, quoting and header. This is similar to MySQL’s ​LOAD LOCAL INFILE​ construct.




In your ​sql​ directory, create a file called ​load.sql​ that contains, one on each line, a ​copy command that loads the three CSV files into Postgres.




Once you are finished, you can check the number of rows in each relation to make sure they match:




<table width="277">

 <tbody>

  <tr>

   <td width="180"><strong>Relation Description </strong></td>

   <td width="97"><strong>Expected Tuples </strong></td>

  </tr>

  <tr>

   <td width="180">Artist info</td>

   <td width="97">643</td>

  </tr>

  <tr>

   <td width="180">Song info</td>

   <td width="97">57,650</td>

  </tr>

  <tr>

   <td width="180">Token info</td>

   <td width="97">5,375,064</td>

  </tr>

  <tr>

   <td width="180">TF-IDF scores</td>

   <td width="97">0</td>

  </tr>

 </tbody>

</table>










Late Submission Policy

Part 1A must be submitted by the deadline. See the syllabus for more information about the late policy.




Submission Instruction

<h2>Preparing Your Submission</h2>

Please create a folder named as your UID, put all your files into the folder, then compress this folder into a single zip file called ​P1A.zip​. If you are working with a partner, ​<strong>one</strong>​ partner will use their UID as the name for the folder. We will figure out who the partner is from ​TEAM.txt​.That is, the zip file should have the following structure.

P1A.zip

|

+- Folder named with Your UID, like “904200000” (without quotes)

|

+- schema.sql

|

+- load.sql

|

+- TEAM.txt

|

+- README.txt




Please note that the file names are case sensitive, so you should use the exact same cases for the file names. (For teamwork, use the submitter’s UID to name the folder)




<ul>

 <li>sql​: A SQL file containing the schema to create the necessary relations.</li>

 <li>sql​: A SQL file containing the ​copy​ commands to load the data into Postgres.</li>

</ul>

<strong>Please make the paths absolute so we can check them automatically. </strong>

<ul>

 <li>txt​: A <u>​</u><strong><u>plain text</u></strong><u>​</u> file that contains the UID(s) of every member of your team. If you worked by yourself, just include your UID. If you worked with a partner, write both UIDs on one line separated by a comma (,).</li>

 <li>txt: A ​<strong><u>plain text</u></strong>​ file that contains anything thing else you feel may be useful to us. If you had any problems getting something to work they way we want it to, include it in this file. While you may receive a point deduction, it is better than 0. This is also the file to include any citations.</li>

</ul>

<strong>Projects are submitted to CCLE, and </strong>​<strong><u>only</u></strong>​<strong> to CCLE. </strong>







TuneSearch Project 1 Part B

<h1>Overview</h1>

In this part of the project, you will use the data you loaded into PostgreSQL to create a simple search engine. In this part, you will accomplish the following:




<ol>

 <li>Connect to the PostgreSQL database via the psycopg2 package for Python 3.</li>

 <li>Use the parameters submitted by the user to form a SQL query that will fetch and rank results.</li>

 <li>Gracefully pass the results to an HTML search results page.</li>

 <li>Allow the user to page through the results in multiples of 20. (20 results shown at a time)</li>

 <li>Protect the database against SQL injections, a common attack vector.</li>

</ol>




<h1>Project Layout</h1>

In the www​          ​ directory in your home directory on the VM (your shared folder), you will see three directories: ​SearchEngine​, ​logs​, and ​sql​. We will get to the logs directory later. The SearchEngine directory contains all of the files for this project, including files you will not need to touch that create a “glue” between nginx and Flask. This “glue” is uWSGI. There are a few different files in this directory, none which need to be touched:




<ol>

 <li>ini​. While nginx handles the web connections over port 80 on the VM, nginx passes all requests to uWSGI. This .ini file configures ​SearchEngine​ for use with uWSGI. It mostly defines file permissions and the number of processes that uWSGI will run. There are a couple of parameters though that will be of interest to you. touch-reload​ and​ py-autoreload​. When a Python file in this project changes, uWSGI and Flask will reload them. Without these options, you would need to restart uwsgi or nginx every time you changed a Python file. ​logto​ specifies where the contents of stderr will be written on disk. This is where the logs directory comes in.</li>

</ol>




<ol start="2">

 <li>py ​loads the ​searchengine​ module so that Flask can see it. It also sets up logging to stderr and appends the path of the module to the Python search path. It then runs the Flask app.</li>

</ol>




Inside the ​SearchEngine​ directory, there is another directory called ​SearchEngine​ which houses a Python module called ​searchengine​. Got that? If you cd into that inner SearchEngine​ directory, you can tell it is a Python module because it contains a file called __init__.py​. This directory contains all of the files that process the data for the search engine as well as the files that control the display of the website. There are several files and directories here:




<ol>

 <li>static​ contains files that control the look and feel of the website, including the header image used for TuneSearch and a CSS file. ​<em>Feel free to play with these</em>​.</li>

 <li>templates contains an index.html file of plain HTML, and a results.html file which is a​ <a href="http://jinja.pocoo.org/docs/2.10/">Jinja2</a> ​           ​<strong>You will need to modify this Jinja2 template to get pagination to work.</strong></li>

 <li>py​ has two functions you will need to modify: dosearch()​ and​       index()​ to handle the HTTP request sent by the user.</li>

 <li>py​ which contains the main logic for connecting to the database, running the proper query and passing the results back to the Jinja2 template.</li>

</ol>




In the outermost ​www​ directory, there are two other directories: ​logs​ and ​sql​.




<ol>

 <li>logs​ contains one file, ​errlog​ which contains errors reported by Python to uWSGI.</li>

 <li>sql​ is an empty directory, and you may wish to house your queries from Part 1A in this directory.</li>

</ol>




<h1>How TuneSearch Works</h1>

As stated in the project overview, a user issues a simple query containing words (tokens). These tokens may also have punctuation attached to them, such as when searching for specific lyrics “Could anything ever feel this real forever?” The punctuation must be stripped. I have already written some code to do this for you.




The user selects either the AND constraint, or the OR constraint. If the user selects AND, only songs that contain ALL of the words in the query are returned. If the user selects OR, songs containing ANY of the words in the query are returned.




When the user visits the main search page, the function ​index()​ in ​searchengine.py​ fires off and simply renders an HTML file called ​index.html​. Whenever the user enters a search query and hits the search button, an HTTP GET request is passed to ​/search​, which is handled by the dosearch()​         function in the same file. You can access data from the request​        using the ​request.args​ dict including the query and the query type (AND or OR). We then move to the ​search()​ function in ​search.py​ where we connect to a database (if needed) and run a Postgres query that finds songs that match the terms in the query. The results are then returned back to the calling function to be rendered in the ​results.html​ Jinja2 template.




This may sound like a lot, but we have broken down this project into a series of small tasks to keep your organized. Tasks 1, 4, and 5 will probably take the most time.




<strong>To view the website, you do not need to open the HTML file or run Python. Just open a browser to </strong>​<strong>http://localhost:1480! </strong>




<h1>Task 0: Redo Part 1A with Our Solution</h1>

To prevent double jeopardy and have everyone start off on the same foot, please see our solution for project 1A which will be posted after the two day grace period. Please do not wait for that. If there are errors, you can always reload the data. We want all students to use the same schema.




<h1>Task 1: Search Ranking Query</h1>

Write a SQL query that computes the TF-IDF score for each token in each song. To do this, you will need to first compute the number of songs that each token appears in (the Inverse Document Frequency, or IDF). You already have the term frequency TF. There are several variations on how to compute TF-IDF. We will use this simple variation:




where TF is the term (token) frequency of token ​<em>i </em>​in song ​<em>j</em>​, |J| is the number of songs and DF​i is<sub>​                    </sub> the number of songs term ​<em>i</em>​ appears in. You will probably want to do this computation in a separate table, and as a one-time data processing step rather than as part of the app.




Then write a query against this table that handles both the AND case and the OR case. We can determine how well a song matches the query by summing across the TF-IDF scores in the search query and then ordering in descending order by TF-IDF. You will want to write your query such that you can test it using some of your own sample queries at the ​psql command​     line.

<h1>Task 2: Write Code to Connect and Disconnect from the Database</h1>

In ​search.py​, there is a comment with some instructions. You must connect to the Postgres instance running on your VM. Whenever you open a connection, you must also close it including when a failure occurs. Take a look at ​<a href="https://docs.python.org/3/tutorial/errors.html">try/except/finally</a> <u>​ </u>exception handling in Python.




<h1>Task 3: Integrate your Database Query in the search()​ Function​</h1>

In the search()​           function in ​       search.py​     , enter your PostgreSQL query or queries to handle​  the user’s input and extract the results from the query. See the helpful hints later in this document.




Each result lists the name of the song (which links to the corresponding LyricsFreak page), as well as the artist that performed it.




<h1>Task 4: Enable Pagination</h1>

You now have a TF-IDF table, and a Postgres query that ranks the search results. Enough Python code is written for you already to output all results in one page. But now we are going to add a Previous and Next button at the bottom of the search results page, if there are more than 20 search results. Each page of results should contain 20 results.




To enable pagination, we can rerun the query you just wrote, once for each page of results, but this is very slow and wasteful. Instead, we should use some other construct we learned in lecture to store the search results, and then write another query against those results to pull the results for each page. Do you know what construct that is? How will you maintain state as you move among pages of results? You may want to play with the ​request.args​ dict as well as embedding some information in the search results page that will indicate where we are in the list of full results.




Finally, the Previous/Next buttons should only show up when they are necessary. For example, The Previous button should not show up on the first page of results, and the Next button should not appear on the final page of results. Additionally, Next button should not be displayed if there are no more results to display.




<h1>Task 5: Protect Your Database from SQL Injections</h1>

Finally, handle user input in such a way that the user cannot commit a SQL injection. Note that because some text processing is done on the query, you won’t be able to actually do a SQL injection yourself. We just want your query to be protected from them.




Late Submission Policy

Part 1B must be submitted the deadline. See the syllabus for more information about the late policy.




Submission Instructions

Preparing Your Submission

Please create a folder named as your UID, put all your files into the folder, then compress this folder into a single zip file called ​P1B.zip​. If you are working with a partner, ​<strong>one</strong>​ partner will use their UID as the name for the folder. We will figure out who the partner is from TEAM.txt​      ​.That is, the zip file should have the following structure.




P1B.zip

|

+- Folder named with Your UID, like “904200000” (without quotes)

|

+- SearchEngine (the outermost directory, just like in the ZIP file)

|

+- sql

|

+- TEAM.txt

|

+- README.txt

(We do not need your logs directory)




Please note that the file names are case sensitive, so you should use the exact same cases for the file names. (For teamwork, use the submitter’s UID to name the folder)




<ul>

 <li>The​ sql ​directory should contain the following:</li>

</ul>

○ load.sql​ containing the query you used to populate the TF-IDF table.

○    <strong>Please make the paths absolute so we can check them automatically. </strong>

<ul>

 <li>txt​: A <u>​</u><strong><u>plain text</u></strong><u>​</u> file that contains the UID(s) of every member of your team. If you worked by yourself, just include your UID. If you worked with a partner, write both UIDs on one line separated by a comma (,).</li>

 <li>txt​: A <u>​</u><strong><u>plain text</u></strong>​ file that contains anything thing else you feel may be useful to us.</li>

</ul>

If you had any problems getting something to work they way we want it to, include it in this

file. While you may receive a point deduction, it is better than 0. This is also the file to include any citations.

<strong>Projects are submitted to CCLE, and </strong>​<strong><u>only</u></strong>​<strong> to CCLE. </strong>

<h1><strong>Testing of Your Submission </strong></h1>

Grading is a difficult and time-consuming process. In order to help you ensure you have the correct files for submission, you can test your packaging by downloading this <u>​</u><a href="https://drive.google.com/a/g.ucla.edu/file/d/1ctKJn0u_OBSOQ2vMzy4yssI2laEo0Xix/view?usp=sharing">Test Script</a>​.

In essence, this script unzips your submission to a temporary directory and tests whether or not you have included all your submission files. Once you download the test script, it can be executed like:

~$ ./p1b_test &lt;Your UID&gt;

(Put your P1B.zip file in the same directory with this test script, you may need to use “chmod +x p1b_test” if there is a permission error).

You ​<strong>MUST</strong>​ test your submission using the script before your final submission to minimize the chance of an unexpected error during grading. Significant points may be deducted if the grader encounters an error during grading. When everything runs properly, you will see an output similar to the following from this script:

Check File Successfully. Please upload your P1B.zip file to CCLE.

<h2>Helpful Hints and Troubleshooting</h2>

When you make a Python or SQL error, nginx will throw an unhelpful HTTP 502 error. If this happens, your first course of action is to look at logs/errlog​        ​ as this is where most errors from Python and Postgres will be recorded. If you catch exceptions, you need to be very careful or else you may never be able to see the error message that is causing you grief.




You can also look at the nginx error log at ​/var/log/nginx/error_log​ but that is generally more helpful for configuration problems.




The file​ search.py​ contains a small ​main()​ function that you can use to pass search queries to Postgres via your Python code. You can then embed ​print​ statements, use a debugger, or other methods to see what is being returned from Postgres. You can change the ​main() function as you see fit for your testing.




<strong>The goal of this project is to do something interesting with Postgres. We are not interested in testing a bunch of edge and corner cases on the parsing of the search query (except for preventing SQL injections), so don’t go overboard. &#x1f642; </strong>

<strong> </strong>

<h2>Resources</h2>

<a href="http://initd.org/psycopg/docs/">psycopg2</a><u>​</u><a href="http://initd.org/psycopg/docs/"> Postgres Driver for Python 3</a>




<a href="http://jinja.pocoo.org/docs/2.10/">Jinja2 Documentation</a>




<a href="http://flask.pocoo.org/docs/1.0/">Flask Documentation</a>




Textbook, 7th Edition, ​<strong>Chapter 9 </strong>

<em>This chapter focuses on Java, but the concepts are highly relevant. </em>
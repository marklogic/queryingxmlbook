Querying XML: XQuery, XPath, and SQL/XML in Context: samples
============================================================

This README describes the contents of each directory in the book samples, then describes how to run the XQuery sample app using MarkLogic Server.
For a fully-functional trial version of MarkLogic Server, go to http://marklogic.com and select "Download MarkLogic Server" under the "Products" tab.

./data
------

Data and Schemas for movies (Data A-1, Data A-2, Data A-3) and reviews (Data A-13, Data A-14, Data A-15).
Note: data is also under ./xquery/xquery-example-app/example.

./xquery/examples
-----------------

XQuery examples from the book (Example A-1 through Example A-19) plus:

* cre_table_reviews.xsl (Data A-16): a stylesheet to transform the reviews XML document and output an SQL script to create and populate the reviews table.

* test-examples.xqy: runs all the XQuery examples.
  To run this in MarkLogic Server:
  1. set up an http server, a WebDAV server, and a network place, as described at the end of this note.
  2. copy the ./xquery/examples directory into the network place so that you have a top-level directory "examples"
  3. from a web browser, go to 
http://localhost:8500/examples/test-examples.xqy

./xquery/xquery-example-app
---------------------------

XQuery code to run the example. 
Needs some configuration in the MarkLogic Server (see below).

./xquery/xquery-example-app/example
-----------------------------------

Copy of sample data -- movies and reviews.

./xquery/xquery-example-app/example/bin
---------------------------------------

XQuery code for the example app, a config file, and a possible CSS stylesheet (note: the name of the CSS stylesheet used in the app is read from config.xml, so you can create several stylesheets and choose between them).

./xquery/xquery-example-app/image
---------------------------------

Images for star ratings.

./SQL
-----

SQL code to create and populate tables for the SQL examples (Data A-4 through Data A-12)  plus:

* xquery-all.sql: all the examples that do XQuery using SQL/XML.

* sqlxml-all.sql: all the SQL/XML examples (except those that do XQuery).

* redo.sql: recreate and populate movies tables
* redo.log: spooled output from redo.sql (incomplete)

./SQL/examples
--------------

SQL examples from the book (Example A-20 through Example A-42).

Running the XQuery example app on MarkLogic Server
==================================================

These instructions assume you are running on windows, and that MarkLogic Server 3.x is installed, and that this is a trial version -- i.e. no security is required.

1. Create a new http server
* open http://localhost:8001 in your web browser
* click on "Groups"
* click on "Default"
* click on "App Servers"
* click on "Create HTTP" tab
name: example
root: /
port: 8500
modules: documents
database: documents
authentication: application-level
default user: admin
(NOTE: this means there is no security)
* click "OK"

2. Create a new Webdav server
* open http://localhost:8001 in your web browser
* click on "Groups"
* click on "Default"
* click on "App Servers"
* click on "Create WebDAV" tab
name: example
root: /
port: 8501
database: documents
authentication: application-level
default user: admin
(NOTE: this means there is no security)
* click "OK"

3. Create a new network place in windows
* in windows explorer, go to "My Network Places"
* click "add a network place"
internet or network address: http://localhost:8501
name: example

4. Open the network place from windows explorer

5. drag the directories "./xquery/xquery-example-app/example" and "./xquery/xquery-example-app/image" from the samples into the network folder you just created. Note: drag just the "example" and "image" directories, not their parents, so that you end up with "example" and "image" as top-level directories in your network folder.

6. from a web browser, go to 
http://localhost:8500/example/bin/query.xqy

7. in the "Title contains" box, type "american". Click "GO".

8. from the results screen, click a movie title to see the XML for that movie, or click a rating to see reviews for that movie (Note: not all movies have reviews).


IMDB-and-Social-Networks
========================

![Alt text](https://github.com/KritikaVersha/Network-Visualization-IMDB-and-Social-Networks/tree/master/IMDB-and-Social-Networks/step1.html?raw=true)
https://github.com/KritikaVersha/Network-Visualization-IMDB-and-Social-Networks/tree/master/IMDB-and-Social-Networks

Step 1

I have fetched the IMDB top 100 movies (by number of votes) page using this URL:
http://www.imdb.com/search/title?at=0&sort=num_votes&count=100
and saved it in a HTML file named step1.html. Few movies have titles or actors with, e.g. accented characters .I have use the utf8 encoding to write out the HTML to use Unicode and preserve any non-English characters

Step 2. 

The next step involves parsing the HTML page above with BeautifulSoup, extract movie information as described below, and save the result in a tab-delimited file named step2.txt.  The step2.txt file has 3 columns and 100 rows. The 3 columns are:
IMDB_ID
Rank
Title
The IMDB_ID is the part that sits between last two slashes in the movie URL in the table.
For example, if the URL is http://www.imdb.com/title/tt0111161/, the IMDB ID is tt0111161

Step 3

I have used the Web service http://omdbapi.com/ to get movie metadata for each of the top 100 movies using the IMDB ID collected in Step 2.  The API with sample requests is documented on the homepage. For example, this URL fetches JSON for the movie “The Social Network”, which has IMDB ID tt1285016: http://www.omdbapi.com/?i=tt1285016.One of the JSON response collected from the web service is as shown below:
{"Title":"The Social Network","Year":"2010","Rated":"PG-13","Released":"01 Oct 2010","Runtime":"120 min","Genre":"Biography, Drama","Director":"David Fincher","Writer":"Aaron Sorkin (screenplay), Ben Mezrich (book)","Actors":"Jesse Eisenberg, Rooney Mara, Bryan Barter, Dustin Fitzsimons","Plot":"Harvard student Mark Zuckerberg creates the social networking site that would become known as Facebook, but is later sued by two brothers who claimed he stole their idea, and the cofounder who was later squeezed out of the business.","Language":"English, French","Country":"USA","Awards":"Won 3 Oscars. Another 102 wins & 86 nominations.","Poster":"http://ia.media-imdb.com/images/M/MV5BMTM2ODk0NDAwMF5BMl5BanBnXkFtZTcwNTM1MDc2Mw@@._V1_SX300.jpg","Metascore":"95","imdbRating":"7.8","imdbVotes":"326,376","imdbID":"tt1285016","Type":"movie","Response":"True"}


Step 4.

The file saved in step 3 was opened and loaded with the JSON string on each line into a variable and then only the movie title and actors list were extracted and saved in a tab-delimited file named step4.txt.  The file has two columns:
1.                       Movie name
2.                       JSON string containing a list of the first 4 actors in the actors list.

Step 5. 

In this step, I have generated a DOT file containing the actor graph, using the pydot module. After downloading and install GraphViz from http://www.graphviz.org/, I installed the pydot package using pip install pydot.
The file saved in step 4 is loaded to generate a graph using the actor lists. Each actor is a graph node, and if two actors are in the actors list (of the first five actors, that is) for the same movie, then there is an edge between them in the graph. The resulting graph is saved in a .dot file, which is a plain text file in the DOT language. itertools module was useful in coming up with the list of actors working together.
Step 6. 
Command-line dot program that comes with GraphViz was then used to produce the visualisation



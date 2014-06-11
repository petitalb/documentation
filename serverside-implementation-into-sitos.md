# Documentation:

------------------------------

**open questions:**

global:
1. development question: is there a option to do "closed" moduls for the functions we have, so that we can do easy updates into our Serversystem, to have less migration work if we have at eexcess function updates
2. displayed thumbnails: law and rights about them to use them into the created texts in Sitos.


internal:
1. which code is useable for us, or do we need to change something
2. which browser should work (layout). firefox, IE version ?, chrome.
3. create a script for easyier updating files if there is an update at eexcess github branch.
4. do we need a own lokal privacy proxy. if we have the own, then we have to install it at every school, but the data of searched things and history ... is always localy and not send to everywhere.
or we use the actually one which is not localy. then the data is send to this and used for analysing search behavior.
problem is at the local option that we have to do maintance and udpate sources and so on. and we have to find a way for local implementation of it.
but i think a localy version is not necessary because user has option to limit his profile with sending information.


------------------------------

**steps / priority of implementation into sitos:**

1. insert manually a searchtext and get results in easywiki
2. put result by function into the created easywiki text (picture and title with link behind)
3. display link of result in a new tab.
4. save the information of point 2 and 3 in user history.
5. create user history - if user logout save history in sitos, if user login write history into local indexfile of browser. (user has the history in every browser and get his graphs and so on)
5. written text should be send automatically to the textsearchfield and gave results (config option for sending the text, by return or end of word or end of sentence ...)
6. marked text should be send automatically to the textsearchfield and gave results
7. content detection for text
8. privacy settings with option to disable and enable userdata for query. with levels (high, middle, low)
9. graphic view of results - FacetScape  http://prntscr.com/3rpybu
10. voting/rating of the results and save them
11. send rating/voting and used/read results to the eexcess server for analysing
12. language selection next to the result list with count of results by language (language is available in meta tags)
13. graphic view of history - timeline
14. graphic view of history - VisGraph http://prntscr.com/3rpzzj
15. graphic view of history - query crumbs http://prntscr.com/3rq0sb


------------------------------

**informations:**

plugin takes automatically the 10 most used wordes of the open pagen and gave results for them.
Stopwords are defined hardcodet.
if you mark a text, also the 10 most words are used of this text.

for history there are two options:
* clientside: in this case user can use only one browser, because history is saved in indexfile by browser and they have differnt once. here we have no summary of the whole history.
* serverside: here the system needs to save history from index file to server user profile at logount and at login write it to the index file of broser. in this case its possible to user different browser.



------------------------------

**information for testing/examples:** 

/common_js/usage_examples -> only searchtext field with result list for testing and implementing example

the query is a summary of user profile, interests of the user (the lables) and the searchtext.

the query way is at the moment:
server -> jason -> proxy -> xml -> recommander -> xml -> proxy -> jason -> server
changed during the hackaton to: server -> jason -> proxy -> recomander -> proxy -> jason -> server
we don't need the translation from jason to xml and back anymore.

------------------------------

**architectur of the extention: (importend files and functions for serverside implementation)**

background.html - always active, define which scripts are running in the background. 
content.js -> which scripts are displayed on which page, at every run of the plugin this scripts are started.
eexcess.css -> global stylesheet for the layout
contextdetector.js -> in every page integrated, includes the filtering of text.
content.js -> callBG function sends the searchquery.
apicalls.js -> line 114 create call of profile + query to the server - line 139 privacy proxy definition which get the query.

------------------------------
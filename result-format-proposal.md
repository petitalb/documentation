# Proposal for the new result format


##Actual status

* The current stable version of the federated recommender (FR) does not handle duplicates in the result list.
* There is no state of the partner recommenders (PM) returned in the result. (e.g. if a partner timed out or had an error)
* A detail call is needed for the documents, therefore some fields have to be grouped.
* There are several fields that are not used or needed anymore.

Therefore several changes will be implemented on the returned result list.


##New result format proposal

The new proposal includes:

* the query identifier
* results with grouping information, only the first element of the group is in the result list the others are saved in the document in the “resultGroup” field which would be NULL if there are no groups
* the document has now it’s own “documentBadge”, sorry for the naming, which can be collected and send back in a list to get the Details of the document.
* partner response state with information if and why the partner did not respond

http://{SERVER}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/recommend
accepts: secure user profile
returns:
```javascript
{
  "result" : [
    {
      "documentBadge":{
          "provider": "Europeana",
          "uri" : "http://europeana.eu/resolve/.." ,
          "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3678"
        },
      "previewImage" : "http://europeanastatic.eu/api/image?uri=...&type=IMAGE",
      "mediaType":"image",
      "title" : "Kalkstein",
      "decription":"Lorem Ipsum",
      "date":"1970",
      "language" : "de",
      "licence":"Gnu....",
      "resultGroup":[{
                      "documentBadge":{
                              "provider": "Europeana",
                              "uri" : "http://europeana.eu/resolve/.." ,
                              "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3679"
                          },
                      "previewImage" : "http://europeanastatic.eu/api/image?uri=...&type=IMAGE",
                      "mediaType":"image",
                      "title" : "Kalkstein",
                      "decription":"Lorem Ipsum",
                      "date":"1971",
                      "language":"de",
                      "licence":"Gnu....",
                       }]
    },
       {
      "documentBadge":{
          "provider": "Europeana",
          "uri" : "http://europeana.eu/resolve/.." ,
          "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3961"
        },
      "previewImage" : "http://europeanastatic.eu/api/image?uri=...&type=IMAGE",
      "mediaType":"image",
      "title" : "Schöckelkalk",
      "decription":"Lorem Ipsum",
      "date":"1970",
      "language" : "de",
      "licence":"Gnu....",
      "resultGroup":[{
                      "documentBadge":{
                              "provider": "Europeana",
                              "uri" : "http://europeana.eu/resolve/.." ,
                              "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3963"
                          },
                      "previewImage" : "http://europeanastatic.eu/api/image?uri=...&type=IMAGE",
                      "mediaType":"image",
                      "title" : "Korallenkalk",
                      "decription":"Lorem Ipsum",
                      "date":"1971",
                      "language":"de",
                      "licence":"Gnu....",
                       }]
    }    
  ],
  "partnerResponseState":[{
    "systemID" : "Europeana",
    "success" : true
    },
    {
    "systemID" : "Mendeley",
    "success" : false,
    "errorMessage":"timeout"
    }
  ],
  "provider" : "federated",
  "totalResults" : 2,
  "queryID":"queryIDXY001"
}
```
##Details Result:
http://{SERVER}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/getDetails
accepts: List of DocumentBadges
returns:
```javascript
{
  "documentBadge" : [
    {
          "provider": "Europeana",
          "uri" : "http://europeana.eu/resolve/.." ,
          "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3678",
          "details" : "........."
        },
        {
          "provider": "Europeana",
          "uri" : "http://europeana.eu/resolve/.." ,
          "id" : "/11601/_OPENUP_MINERALOGY_NHMV_AUSTRIA_3961",
          "details" : "........."
        }
}
```


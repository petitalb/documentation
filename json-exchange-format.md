# Request and Response format for call to federated recommender

Notes:
* In principle all fields are optional, and can be either not sent or left blank.

## query request format
POST: http://{SERVER}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/recommend
application/json
```javascript
{
   /*List of selected partners for this query. */
   /*If the list is empty all registered partners, except if source selection is switched on, are queried. May be left empty.*/
   /*Considered is only the SystemID of the given partnerbadge which has to be unique.*/
   /*Datatype: PartnerBadge*/
   "partnerList":[
      {
         /*System ID of the partner. Has to be unique in the system.*/
         /*Datatype: String*/
         "systemId":"Europeana"
      }
   ],
   /*List of Partners that are "protected" by a partnerKey to query them. May be left empty.*/
   /*Datatype: PartnerBadge.*/
   "protectedPartnerList":[
         /*System ID of the partner. Has to be unique in the system.*/
         /*Datatype: String*/
         "systemId":"Europeana"
         /*Partner Key of the partner.*/
         /*Datatype: String*/
         "partnerKey":"ycz!djklasnbm2ia"
   ],
   /*ID for the query. Is returned in the results to map queries to results. May be left empty.*/
   /*Datatype: String*/
   "queryID":"1234COFFEE",
   /*First name of the User.  May be left empty.*/
   /*Datatype: String*/
   "firstName":"Max",
   /*Last name of the User.  May be left empty.*/
   /*Datatype: String*/
   "lastName":"Musterman",
   /*Date of birth of the user. May be left empty.*/
   /*Datatype: Integer*/
   "birthDate":1433924619545,
   /*Amount of items the result should return. Default is 10*/
   /*Datatype: Integer*/
   "numResults":10,
   /*Gender of the User. May be left empty.*/
   /*Datatype: String*/
   "gender":"female",
   /*Address of the User. May be left empty.*/
   /*Datatype: Address*/ 
   "address":{
      /*Country of the user. May be left empty.*/
      /*Datatype: String*/
      "country":"testcountry",
      /*Zip code of the user. May be left empty.*/
      /*Datatype: Integer*/
      "zipCode":1213345,
      /*City of the user. May be left empty.*/
      /*Datatype: String*/
      "city":"testcity",
      /*Additional information. May be left empty.*/
      /*Datatype: String*/
      "line1":"nothing",
      /*Additional information. May be left empty.*/
      /*Datatype: String*/
      "line2":"to add"
   },
   /*Time range of the query if supported by the partners search engine. May be left empty.*/
   /*Datatype: TimeRange*/
   "timeRange":{
      /*Start date of the query*/
      /*Datatype: String*/
      "start":"1980",
      /*End date of the query*/
      /*Datatype: String*/
      "end":"2000"
   },
   /*Spoken language of the user. Partners that don't support the language will be left out. May be left empty.*/
   /*Datatype: Language*/
   "languages":[
      {
         /*Language in iso format.*/
         /*Datatype: String*/
         "iso2":"de",
         /*Level of competence for weighting.*/
         /*Datatype: Double*/
         "competenceLevel":0.1
      },
      {
         "iso2":"en",
         "competenceLevel":0.1
      }
   ],
   /*Locations of the user. Results might be filtered depending on the locations. May be left empty.*/
   /*Datatype: UserLocation*/
   "userLocations":[
      {
         /*Longitude of the location.*/
         /*Datatype: Double*/
         "longitude":33.123123,
         /*Latitude of the location.*/
         /*Datatype: Double*/
         "latitude":-127.123123,
         /*Accuracy level of the location.*/
         /*Datatype: Double*/
         "accuracy":4.5,
         /*Timestamp of the location.*/
         /*Datatype: Integer*/
         "timestamp":1433924619548
      },
      {
         "longitude":20.123123,
         "latitude":-130.123123,
         "accuracy":4.5,
         "timestamp":1433924619548
      }
   ],
   /*List of Partners that are "protected" by a partnerKey to query them. May be left empty.*/
   /*Datatype: PartnerBadge*/
   "userCredentials":[
      {
         /*System ID of the partner. Has to be unique in the system.*/
         /*Datatype: String*/
         "systemId":"Wissenmedia",
         /*Login name*/
         /*Datatype: String*/
         "login":"me@partner.x",
         /*Security Token or password*/
         /*Datatype: String*/
         "securityToken":"sdjalkej21!#"
      }
   ],
   /*History of the user's visited pages. May be left empty.*/
   /*Datatype: History*/
   "history":[
      {
         /*Last visited time of the given page*/
         /*Datatype: Integer*/
         "lastVisitTime":1433924619545,
         /*Title of the given page*/
         /*Datatype: String*/
         "title":"history title",
         /*How often the user has typed the URL*/
         /*Datatype: Integer*/
         "typedCount":4,
         /*Datatype: Integer*/
         /*How often the user has visited the URL*/
         /*Datatype: Integer*/
         "visitCount":4,
         /*The actuall URL*/
         /*Datatype: String*/
         "url":"http://1234.com"
      }
   ],
   /*The actual query terms. At least one has to be there*/
   /*Datatype: Contextkeyword*/
   "contextKeywords":[
      {
         /*Keyword or phrase, phrases might be handled differently depending on the partner (as conjunctive query).*/
         /*Datatype: String*/
         "text":"women",
         /*Weight of the query term or phrase.*/
         /*Datatype: Double*/
         "weight":0.5
      },
      {
         "text":"labour",
         "weight":0.5
      }
   ],
   /*The context of the given contextkeywords. May be left empty.*/
   /*Datatype: Context*/
   "context":{
      /*Reason for the query generation. Might be automaticly extraced or manualy entered.*/
      /*Datatype: String*/
      "reason":"manual",
      /*Additional value. E.g. the Page from which the query was generated*/
      /*Datatype: String*/
      "value":"www.wikipedia.at"
   },
   /*Named entities found in the users context.  May be left empty.*/
   /*Datatype: ContextNamedEntity*/
   "contextNamedEntities":{
      /*Locations found in the context*/
      /*Datatype: ContextNamedEntitiesElement*/
      "locations":[
         {  
            /*Actuall description of the named entity*/
            /*Datatype: String*/
            "text":"graz",
            /*Weight of the named entity*/
            /*Datatype: Double*/
            "weight":0.1,
            /*Confidence level of the named entity*/
            /*Datatype: Double*/
            "confidence":0.1,
            /*DBPedia URI of the named entity*/
            /*Datatype: String*/
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"graz",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ],
      /*See Locations*/
      /*Datatype: ContextNamedEntitiesElement*/
      "persons":[
         {
            "text":"Michael Jackson",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"Bill Clinton",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ],
      /*See Locations*/
      "organizations":[
         {
            "text":"know-center",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"mendeley",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ],
      /*See Locations*/
      "misc":[
         {
            "text":"something",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"something",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ],
      /*See Locations*/
      "topics":[
         {
            "text":"Trees",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"Animal",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ]
   },
   /*Interests of the user. Might be added to the query depending on the used query formulation algorithms. May be left empty.*/
   /*Datatype: Interest*/
   "interests":[
      {
         /*Entered interest text*/
         /*Datatype: String*/
         "text":"text",
         /*User might give a weight to the interest. May be left empty.*/
         /*Datatype: String*/
         "weight":0.1,
         /*User might give a confidence of the competence level. May be left empty.*/
          /*Datatype: String*/
         "confidence":0.1,
         /*User might give a competence level. May be left empty.*/
         /*Datatype: Double*/
         "competenceLevel":0.1
         /*Possible source of the interest. May be left empty.*/
         /*Datatype: String*/,
         "source":"source",
         /*Possible URI to the interest*/
         /*Datatype: String*/
         "uri":"http://dsjkdjas.de"
      },
      {
         "text":"text2",
         "weight":0.2,
         "confidence":0.2,
         "competenceLevel":0.2,
         "source":"source2",
         "uri":"http://google.de"
      }
   ]
}
```
## query response format
```javascript
{
   "provider":"federated",
   "totalResults":10,
   "partnerResponseState":[
      {
         "systemID":"Europeana",
         "success":true
      },
      {
         "systemID":"Deutsche Digitale Bibliothek",
         "success":false,
         "errorMessage":"Waited too long for partner system 'Deutsche Digitale Bibliothek' to respond 2972 ms "
      },
      {
         "systemID":"Wikipedia-Local",
         "success":false,
         "errorMessage":"Waited too long for partner system 'Wikipedia-Local' to respond 2972 ms "
      },
      {
         "systemID":"Wissenmedia",
         "success":true
      },
      {
         "systemID":"Mendeley",
         "success":true
      },
      {
         "systemID":"ZBW",
         "success":false,
         "errorMessage":"Timeout"
      },
      {
         "systemID":"KIMPortal",
         "success":true
      }
   ],
   "result":[
      {
         "resultGroup":[
            {
               "documentBadge":{
                  "id":"sl23394330",
                  "uri":"http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23394330&s=BEP&v=eexcess&w=EEXCESS",
                  "provider":"Wissenmedia"
               },
               "mediaType":"unknown",
               "previewImage":"http://service.wissens-server.com/wissensserver/media/?a=v&c=file-system&v=ws-mediensuche&reswidth=98&resheight=98&width=100&height=100&origin=center&border=1x1&background=FAFAFA&bordercolor=ddd&u=jadis/incoming/1569868.jpg",
               "title":"Computer",
               "description":"ComputerComputer [kɔmˈpjuːtər; englisch, zu to compute »(be)rechnen«, von lateinisch computare] der, -s/-, Rechner, Datenverarbeitungsanlage, Abkürzung DVA, elektronisch arbeitende Einrichtung, die Probleme dadurch löst, dass sie...",
               "date":"2014-04-28T07:55:00Z",
               "language":"de",
               "licence":"restricted"
            }
         ],
         "documentBadge":{
            "id":"sl23394330",
            "uri":"http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23394330&s=BEP&v=eexcess&w=EEXCESS",
            "provider":"Wissenmedia"
         },
         "mediaType":"unknown",
         "previewImage":"http://service.wissens-server.com/wissensserver/media/?a=v&c=file-system&v=ws-mediensuche&reswidth=98&resheight=98&width=100&height=100&origin=center&border=1x1&background=FAFAFA&bordercolor=ddd&u=jadis/incoming/1569868.jpg",
         "title":"Computer",
         "description":"ComputerComputer [kɔmˈpjuːtər; englisch, zu to compute »(be)rechnen«, von lateinisch computare] der, -s/-, Rechner, ...",
         "date":"2014-04-28T07:55:00Z",
         "language":"de",
         "licence":"restricted"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"/9200386/BibliographicResource_3000095846216",
            "uri":"http://europeana.eu/resolve/record/9200386/BibliographicResource_3000095846216",
            "provider":"Europeana"
         },
         "mediaType":"unknown",
         "previewImage":"http://europeanastatic.eu/api/image?uri=http%3A%2F%2Fbsb0mdz-upload.bsb.lrz.de%2F%7Eeuropeana%2Fbsb11072436%2Fdownload%2Fthumbs%2Fbsb11072436_00023.jpg&size=LARGE&type=TEXT",
         "title":"The works of Lord Byron complete in one volumeThe works",
         "date":"unknown",
         "language":"de",
         "licence":"http://www.europeana.eu/rights/out-of-copyright-non-commercial/"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"DIST_000004550",
            "uri":"http://www.kim.bl.openinteractive.ch/sammlungen#6a06900a-68fa-4d5f-82d5-6290264cafaa",
            "provider":"KIMPortal"
         },
         "mediaType":"unknown",
         "previewImage":"https://kgapi.bl.ch/media/kim-collect/resources/images/thumbs/6a06900a-68fa-4d5f-82d5-6290264cafaa_0001.jpg",
         "title":"Fotografie, Zeichnung von Georg Herwegh (Foto)",
         "description":"Burg (oder Stadteingang) über Mauer und Fels. Davor freies Feld mit Bauer, Kuh und Ziege. Im Hintergrund ein rosses Kreuz. Auf der Rückseite handschriftlicher Eintrag .....",
         "date":"unknown",
         "language":"de",
         "licence":"\n\t\t\t\t\t\t\t    http://creativecommons.org/licenses/by-nc-sa/4.0/\n\t\t\t\t\t\t\t"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"/9200386/BibliographicResource_3000044999678",
            "uri":"http://europeana.eu/resolve/record/9200386/BibliographicResource_3000044999678",
            "provider":"Europeana"
         },
         "mediaType":"unknown",
         "previewImage":"http://europeanastatic.eu/api/image?uri=http%3A%2F%2Fbsb0mdz-upload.bsb.lrz.de%2F%7Eeuropeana%2Fbsb10745363%2Fdownload%2Fthumbs%2Fbsb10745363_00027.jpg&size=LARGE&type=TEXT",
         "title":"The Works of Lord Byron complete in one volumeThe works",
         "date":"unknown",
         "language":"de",
         "licence":"http://www.europeana.eu/rights/out-of-copyright-non-commercial/"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"10001571124",
            "uri":"http://www.econbiz.de/Record/10001571124",
            "provider":"ZBW"
         },
         "mediaType":"unknown",
         "title":"Frauen - Technik - Evaluation : Frauenförderung als Qualitätskriterium in technisch-naturwissenschaftlichen Studiengängen; Bonn, 6./7. Juli 2000 ; [diese Publikation ist im Rahmen des Projektes Qualitätssicherung entstanden]",
         "date":"2001",
         "language":"de",
         "licence":"restricted"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"34a40c2f-7850-365a-af5b-1253dfc0e028",
            "uri":"http://www.mendeley.com/research/critique-lovelace-metaanalysis",
            "provider":"mendeley"
         },
         "mediaType":"unknown",
         "title":"Critique of Lovelace Meta-Analysis",
         "date":"2007",
         "language":"unknown",
         "licence":"https://creativecommons.org/licenses/by/3.0/legalcode"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"DIST_000003457",
            "uri":"http://www.kim.bl.openinteractive.ch/sammlungen#9ef343c7-aa70-487f-bcbe-64a5bdf1affa",
            "provider":"KIMPortal"
         },
         "mediaType":"unknown",
         "title":"Notizbuch",
         "description":"Notizbuch (kleinformatig), brauner Ledereinband und goldener Verschluss. Text auf 52 Seiten.",
         "date":"unknown",
         "language":"de",
         "licence":"\n\t\t\t\t\t\t\t    http://creativecommons.org/licenses/by-nc-sa/4.0/\n\t\t\t\t\t\t\t"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"1ec04663-27ad-3292-aff5-163b9bea9fab",
            "uri":"http://www.mendeley.com/research/byrons-voice",
            "provider":"mendeley"
         },
         "mediaType":"unknown",
         "title":"Byron's Voice",
         "date":"2010",
         "language":"unknown",
         "licence":"https://creativecommons.org/licenses/by/3.0/legalcode"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"10010480859",
            "uri":"http://www.econbiz.de/Record/10010480859",
            "provider":"ZBW"
         },
         "mediaType":"unknown",
         "title":"Taking the Lord's Name in Vain: The Impact of Connected Directors on 19th Century British Banks",
         "description":"This paper utilizes data on the presence of prominent individualsthat is, those with political (e.g., Members of Parliament) and aristocratic titles (e.g., lords)--...",
         "date":"2014",
         "language":"de",
         "licence":"restricted"
      },
      {
         "resultGroup":[

         ],
         "documentBadge":{
            "id":"/9200386/BibliographicResource_3000045256289",
            "uri":"http://europeana.eu/resolve/record/9200386/BibliographicResource_3000045256289",
            "provider":"Europeana"
         },
         "mediaType":"unknown",
         "previewImage":"http://europeanastatic.eu/api/image?uri=http%3A%2F%2Fbsb0mdz-upload.bsb.lrz.de%2F%7Eeuropeana%2Fbsb10701385%2Fdownload%2Fthumbs%2Fbsb10701385_00025.jpg&size=LARGE&type=TEXT",
         "title":"The poetical works of Lord Byron With Life. 6 engravings on steel",
         "date":"unknown",
         "language":"de",
         "licence":"http://www.europeana.eu/rights/out-of-copyright-non-commercial/"
      }
   ]
}
```


### Interactively inspection of the response
In order to interactively inspect the service's response you can use this command pipeline:
```bash
curl -v -H "Accept: application/json" -H "Content-Type: application/json" -d @<JSON FILE> \
<SERVER URL> 2>/dev/null | python -m json.tool | less
```
Where <JSON FILE> is a file corresponding to the request format and <SERVER URL> is a URL pointing to a federated recommender service.
This assumes you are using a Unix-like system and have `curl`, `python` and `less` installed.

## details request format
The request has to be a list of given documentBadges:
POST: http://{SERVER}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/getDetails
application/json
```javascript
{
   "documentBadge":[
      {
         "id":"/9200134/BibliographicResource_2000000012526",
         "uri":"http://europeana.eu/resolve/record/9200134/BibliographicResource_2000000012526",
         "provider":"Europeana"
      },
      {
         "id":"sl23428166",
         "uri":"http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23428166&s=BEP&v=eexcess&w=EEXCESS",
         "provider":"wissenmedia"
      },
      {
         "id":"/9200134/BibliographicResource_2000000012526",
         "uri":"http://europeana.eu/resolve/record/9200134/BibliographicResource_2000000012526",
         "provider":"Europeana"
      },
      {
         "id":"995eb36f-151d-356c-b00c-4ef419bc2124",
         "uri":"http://www.mendeley.com/research/hellenism-homoeroticism-shelley-circle",
         "provider":"Mendeley"
      },
      {
         "id":"DIST_000003457",
         "uri":"http://www.kim.bl.openinteractive.ch/sammlungen#9ef343c7-aa70-487f-bcbe-64a5bdf1affa",
         "provider":"KIM.Portal"
      }
   ]
}
```

## details response format

```javascript
{
   "documentBadge":[
      {
         "id":"/9200134/BibliographicResource_2000000012526",
         "uri":"http://europeana.eu/resolve/record/9200134/BibliographicResource_2000000012526",
         "provider":"Europeana",
         "detail":"..."
      },
      {
         "id":"/9200134/BibliographicResource_2000000012526",
         "uri":"http://europeana.eu/resolve/record/9200134/BibliographicResource_2000000012526",
         "provider":"Europeana",
         "detail":"..."
      },
      {
         "id":"995eb36f-151d-356c-b00c-4ef419bc2124",
         "uri":"http://www.mendeley.com/research/hellenism-homoeroticism-shelley-circle",
         "provider":"Mendeley",
         "detail":"..."
      }
   ]
}
```

# Request and Response formats to interact with the Privacy Proxy

## Request formats

There are two formats to query the privacy proxy: QF1 and QF2. The only difference between the two comes from `contextKeywords` attribute. QF1 is similar to the query request format defined in the Federated Recommender section: 
```javascript
{
   ...
   "contextKeywords":[
      {"text":"women", "weight":0.5}, 
      {"text":"labour","weight":0.5}
   ],
   ...
}
```
QF2 allow defining obfuscated queries by considering bags of keywords: 
```javascript
{
   ...
   "contextKeywords":[
      [{"text":"women", "weight":0.5}, {"text":"labour","weight":0.5}],
      [{"text":"paris", "weight":0.5}, {"text":"history","weight":0.5}],
      [{"text":"sport", "weight":0.5}, {"text":"soccer","weight":0.5}]
   ],
   ...
}
```

## Response formats

There are two formats for the responses: RF1 and RF2. They respectively correspond to the request formats QF1 and QF2. The only difference comes from the `result` attribute. RF1 is similar to the response format defined in the Federated Recommender section: 
```javascript
{
   ...
   "result":[
      { ... },
      { ... }
   ]
}
```
RF2 embeds several result sets. Each result set correspond to a bag of keyword defined in the obfuscated query (i.e., the number of set of keywords in the query is equal to the number of result sets in the response). RF2 is defined as: 
```javascript
{
   ...
   "result":[
      [{ ... }, { ... }, { ... }],
      [{ ... }, { ... }, { ... }],
      [{ ... }, { ... }, { ... }]
   ]
}
```

## Details request and response formats

These formats are similar to those defined in the Federated Recommender section. 

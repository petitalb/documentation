# Request and Response format for call to federated recommender

Notes:
* In principle all fields are optional, and can be either not sent or left blank.

## query request format
POST: http://{SERVER}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/recommend
application/json
```javascript
{
   "partnerList":[
      {
         "systemId":"Europeana"
      }
   ],
   "protectedPartnerList":[

   ],
   "queryID":"1234COFFEE",
   "firstName":"Max",
   "lastName":"Musterman",
   "birthDate":1433924619545,
   "numResults":null,
   "gender":"male",
   "address":{
      "country":"testcountry",
      "zipCode":1213345,
      "city":"testcity",
      "line1":"nothing",
      "line2":"to add"
   },
   "timeRange":{
      "start":"1980",
      "end":"2000"
   },
   "languages":[
      {
         "iso2":"de",
         "competenceLevel":0.1
      },
      {
         "iso2":"en",
         "competenceLevel":0.1
      }
   ],
   "userLocations":[
      {
         "longitude":33.123123,
         "latitude":-127.123123,
         "accuracy":4.5,
         "timestamp":1433924619548
      },
      {
         "longitude":20.123123,
         "latitude":-130.123123,
         "accuracy":4.5,
         "timestamp":1433924619548
      }
   ],
   "userCredentials":[
      {
         "systemId":"Wissenmedia",
         "login":"me@partner.x",
         "securityToken":"sdjalkej21!#"
      }
   ],
   "history":[
      {
         "lastVisitTime":1433924619545,
         "title":"history title",
         "typedCount":4,
         "visitCount":4,
         "url":"http://1234.com"
      }
   ],
   "contextKeywords":[
      {
         "text":"women",
         "weight":0.5
      },
      {
         "text":"labour",
         "weight":0.5
      }
   ],
   "context":{
      "reason":"manual",
      "value":"www.wikipedia.at"
   },
   "contextNamedEntities":{
      "locations":[
         {
            "text":"graz",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         },
         {
            "text":"graz",
            "weight":0.1,
            "confidence":0.1,
            "uri":"http://dbpedia.url.org"
         }
      ],
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
   "interests":[
      {
         "text":"text",
         "weight":0.1,
         "confidence":0.1,
         "competenceLevel":0.1,
         "source":"source",
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
The following interactions are currently logged on the privacy proxy (all including a timestamp, origin and ip):
* query (+ whole user profile as shown below)
* activated query (when the user decides to display results of an automatic query executed in the background)
* results (+ weighted query keywords and federated response)
* show/hide extension (+ current url)
* open/close result (+ result url, corresponding query, duration)
* rating (+ resource url, rating value [1|2])
* FacetScape {mode:<"selection" | "deselection" | "include" | "exclude" | "move">,facetName,facetValue,uuid} in separate logfile


The user profile logged along with a query is basically identical to the [request format of the federated recommender](https://github.com/EEXCESS/documentation/wiki/json-exchange-format#request-format). Depending on the privacy policy, some attributes may not be given.
In addition, the following adaptations are made if the query is sent by the extension:
* the attribute **reason** in the entries of **contextKeywords** is omitted
* an additional attribute **uuid** is added
* an additional attribute **context** is added, which covers the following scenarios:
	1. A query is triggered automatically by visiting a web page
	```javascript
"context" : {
	"reason" : "page", // "page" indicates that the search was triggered automatically by visiting a web page
	"context" : "http://en.wikipedia.org/wiki/Loom" // the url of the visited page
}
```
	2. A query is triggered automatically by selecting a piece of text
	```javascript
"context" : {
	"reason" : "selection", // "selection" indicates that the search was triggered automatically by a text selection
	"context" : "A loom is a device used to weave cloth" // the selected text
}
```
	3. A query is triggered manually
	```javascript
"context" : {
	"reason" : "manual", // "manual" indicates the query is given explicitly by the user
	"context" : "A loom is a device used to weave cloth", // contains a text selection (if any)
	"text" : "weaving" // the actual query
}
```


User Profile example logged along with a query (not all possible attributes present):
```javascript
{
	"history" : [{
			"lastVisitTime" : "1405586857413",
			"title" : "Loom - Wikipedia, the free encyclopedia",
			"typedCount" : 0,
			"url" : "http://en.wikipedia.org/wiki/Loom",
			"visitCount" : 7
		}, {
			"lastVisitTime" : "1405586696229",
			"title" : "Options - EEXCESS",
			"typedCount" : 0,
			"url" : "chrome-extension://hciiebglncblkihpbfmohaihobfhlgpp/options/options.html",
			"visitCount" : 13
		}
	],
	"firstName" : "hilde",
	"lastName" : "maier",
	"gender" : "female",
	"birthDate" : "2013-05-07",
	"address" : {
		"country" : "im nirgendwo",
		"city" : "irgendwo",
		"line1" : "hinterm",
		"line2" : "berg"
	},
	"interests" : [],
	"contextKeywords" : [{
			"weight" : 1,
			"text" : "loom",
		}, {
			"weight" : 0.4673913043478261,
			"text" : "looms",
		}, {
			"weight" : 0.34782608695652173,
			"text" : "shuttle",
		}, {
			"weight" : 0.33695652173913043,
			"text" : "weaving",
		}, {
			"weight" : 0.32608695652173914,
			"text" : "warp",
		}, {
			"weight" : 0.21739130434782608,
			"text" : "shed",
		}, {
			"weight" : 0.20652173913043478,
			"text" : "weft",
		}, {
			"weight" : 0.17391304347826086,
			"text" : "threads",
		}, {
			"weight" : 0.16304347826086957,
			"text" : "heddles",
		}, {
			"weight" : 0.15217391304347827,
			"text" : "weaver",
		}
	],
	"uuid" : "52BD5C8C-C7FA-4BB5-9908-ED382C44AF6A",
	"context" : {
		"reason" : "page",
		"context" : "http://en.wikipedia.org/wiki/Loom" 
	}
}
```

# logging endpoints
The logs for query and result do not require a specific endpoint (samples can be found at the bottom). Other logging endpoints:
* **/log/rating** rating of a resource
* **/log/rview** detail view of a resource opened
* **/log/rclose** detail view of a resource closed
* **/log/show_hide** visibility of the sidebar toggled
* **/log/facetScape** facetScape interaction
* **/log/query_activated** user decided to view results of a query executed in the background

## /log/rating
input:
```javascript
{
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7",
	"rating" : {
		"resource" : "http://europeana.eu/resolve/record/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680",
		"timestamp" : 1404209532893,
		"context" : {
			"query" : "loom"
		},
		"beenRecommended" : true,
		"type" : "rating",
		"annotation" : {
			"@context" : "http://www.w3.org/ns/oa-context-20130208.json",
			"@type" : "oa:Annotation",
			"hasTarget" : {
				"@id" : "http://europeana.eu/resolve/record/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680"
			},
			"hasBody" : {
				"http://purl.org/stuff/rev#rating" : 2,
				"http://purl.org/stuff/rev#minRating" : 1,
				"http://purl.org/stuff/rev#maxRating" : 2
			}
		}
	}
}
```
log entry:  
```
2014-07-01 12:12:12,899 [RATING] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7",
	"rating" : {
		"resource" : "http://europeana.eu/resolve/record/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680",
		"timestamp" : 1404209532893,
		"context" : {
			"query" : "loom"
		},
		"beenRecommended" : true,
		"type" : "rating",
		"annotation" : {
			"@context" : "http://www.w3.org/ns/oa-context-20130208.json",
			"@type" : "oa:Annotation",
			"hasTarget" : {
				"@id" : "http://europeana.eu/resolve/record/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680"
			},
			"hasBody" : {
				"http://purl.org/stuff/rev#rating" : 2,
				"http://purl.org/stuff/rev#minRating" : 1,
				"http://purl.org/stuff/rev#maxRating" : 2
			}
		}
	}
}
```

## /log/rview
input:
```javascript
{
	"resource" : "http://www.econbiz.de/Record/10009492734",
	"timestamp" : 1404209607918,
	"type" : "view",
	"context" : {
		"query" : "loom"
	},
	"beenRecommended" : true,
	"action" : "result-view",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
log entry:  
```
2014-07-01 12:13:27,958 [RESULT_VIEW] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"resource" : "http://www.econbiz.de/Record/10009492734",
	"timestamp" : 1404209607918,
	"type" : "view",
	"context" : {
		"query" : "loom"
	},
	"beenRecommended" : true,
	"action" : "result-view",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```

## /log/rclose
input:
```javascript
{
	"resource" : "http://www.econbiz.de/Record/10009492734",
	"timestamp" : 1404209607918,
	"type" : "view",
	"context" : {
		"query" : "loom"
	},
	"beenRecommended" : true,
	"id" : 9,
	"duration" : 3451,
	"action" : "result-close",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
log entry:  
```
2014-07-01 12:13:31,376 [RESULT_CLOSE] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"resource" : "http://www.econbiz.de/Record/10009492734",
	"timestamp" : 1404209607918,
	"type" : "view",
	"context" : {
		"query" : "loom"
	},
	"beenRecommended" : true,
	"id" : 9,
	"duration" : 3451,
	"action" : "result-close",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```

## /log/show_hide
input ("visible:false" means, the sidebar was turned off at the currentPage):
```javascript
{
	"visible" : false,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7",
	"currentPage" : "http://en.wikipedia.org/wiki/Loom"
}
```
log entry ("visible:false" means, the sidebar was turned off at the currentPage):  
```
2014-07-01 12:14:27,280 [SHOW_HIDE] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"visible" : false,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7",
	"currentPage" : "http://en.wikipedia.org/wiki/Loom"
}
```

## /log/facetScape
inputs:
```javascript
{
	"mode" : "move",
	"facetName" : "language",
	"facetValue" : null,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
```javascript
{
	"mode" : "selection",
	"facetName" : "year",
	"facetValue" : "2013",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
```javascript
{
	"mode" : "exclude",
	"facetName" : "provider",
	"facetValue" : null,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
```javascript
{
	"mode" : "include",
	"facetName" : "provider",
	"facetValue" : null,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
log entries:  
```
2014-07-01 12:15:54,608 [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
	{
		"mode" : "move",
		"facetName" : "language",
		"facetValue" : null,
		"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
	}
```
```
2014-07-01 12:15:57,092 [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"mode" : "selection",
	"facetName" : "year",
	"facetValue" : "2013",
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
```
2014-07-01 12:15:59,468 [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"mode" : "exclude",
	"facetName" : "provider",
	"facetValue" : null,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```
```
2014-07-01 12:16:55,760 [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"mode" : "include",
	"facetName" : "provider",
	"facetValue" : null,
	"uuid" : "E993A29B-A063-426D-896E-131F85193EB7"
}
```

## /log/query_activated
input:
```javascript
{
	"uuid" : "52BD5C8C-C7FA-4BB5-9908-ED382C44AF6A",
	"queryData" : {
		"query" : [{
				"weight" : 1,
				"text" : "loom",
				"reason" : "page"
			}, {
				"weight" : 0.4673913043478261,
				"text" : "looms",
				"reason" : "page"
			}, {
				"weight" : 0.34782608695652173,
				"text" : "shuttle",
				"reason" : "page"
			}, {
				"weight" : 0.33695652173913043,
				"text" : "weaving",
				"reason" : "page"
			}, {
				"weight" : 0.32608695652173914,
				"text" : "warp",
				"reason" : "page"
			}, {
				"weight" : 0.21739130434782608,
				"text" : "shed",
				"reason" : "page"
			}, {
				"weight" : 0.20652173913043478,
				"text" : "weft",
				"reason" : "page"
			}, {
				"weight" : 0.17391304347826086,
				"text" : "threads",
				"reason" : "page"
			}, {
				"weight" : 0.16304347826086957,
				"text" : "heddles",
				"reason" : "page"
			}, {
				"weight" : 0.15217391304347827,
				"text" : "weaver",
				"reason" : "page"
			}
		],
		"timestamp" : 1405587568264,
		"context" : {
			"selectedText" : "",
			"url" : "http://en.wikipedia.org/wiki/Loom"
		}
	}
}
```
log entry:
```
2014-07-17 10:59:28,305 [QUERY_ACTIVATED] [userID:52BD5C8C-C7FA-4BB5-9908-ED382C44AF6A] [origin:chrome-extension://hciiebglncblkihpbfmohaihobfhlgpp] [ip:0:0:0:0:0:0:0:1] 
{
	"uuid" : "52BD5C8C-C7FA-4BB5-9908-ED382C44AF6A",
	"queryData" : {
		"query" : [{
				"weight" : 1,
				"text" : "loom",
				"reason" : "page"
			}, {
				"weight" : 0.4673913043478261,
				"text" : "looms",
				"reason" : "page"
			}, {
				"weight" : 0.34782608695652173,
				"text" : "shuttle",
				"reason" : "page"
			}, {
				"weight" : 0.33695652173913043,
				"text" : "weaving",
				"reason" : "page"
			}, {
				"weight" : 0.32608695652173914,
				"text" : "warp",
				"reason" : "page"
			}, {
				"weight" : 0.21739130434782608,
				"text" : "shed",
				"reason" : "page"
			}, {
				"weight" : 0.20652173913043478,
				"text" : "weft",
				"reason" : "page"
			}, {
				"weight" : 0.17391304347826086,
				"text" : "threads",
				"reason" : "page"
			}, {
				"weight" : 0.16304347826086957,
				"text" : "heddles",
				"reason" : "page"
			}, {
				"weight" : 0.15217391304347827,
				"text" : "weaver",
				"reason" : "page"
			}
		],
		"timestamp" : 1405587568264,
		"context" : {
			"selectedText" : "",
			"url" : "http://en.wikipedia.org/wiki/Loom"
		}
	}
}
```

## query log entry
```
2014-07-01 09:47:56,002 [QUERY] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"history" : [{
			"lastVisitTime" : "1405586857413",
			"title" : "Loom - Wikipedia, the free encyclopedia",
			"typedCount" : 0,
			"url" : "http://en.wikipedia.org/wiki/Loom",
			"visitCount" : 7
		}, {
			"lastVisitTime" : "1405586696229",
			"title" : "Options - EEXCESS",
			"typedCount" : 0,
			"url" : "chrome-extension://hciiebglncblkihpbfmohaihobfhlgpp/options/options.html",
			"visitCount" : 13
		}
	],
	"firstName" : "hilde",
	"lastName" : "maier",
	"gender" : "female",
	"birthDate" : "2013-05-07",
	"address" : {
		"country" : "im nirgendwo",
		"city" : "irgendwo",
		"line1" : "hinterm",
		"line2" : "berg"
	},
	"interests" : [],
	"contextKeywords" : [{
			"weight" : 1,
			"text" : "loom",
			"reason" : "page"
		}, {
			"weight" : 0.4673913043478261,
			"text" : "looms",
			"reason" : "page"
		}, {
			"weight" : 0.34782608695652173,
			"text" : "shuttle",
			"reason" : "page"
		}, {
			"weight" : 0.33695652173913043,
			"text" : "weaving",
			"reason" : "page"
		}, {
			"weight" : 0.32608695652173914,
			"text" : "warp",
			"reason" : "page"
		}, {
			"weight" : 0.21739130434782608,
			"text" : "shed",
			"reason" : "page"
		}, {
			"weight" : 0.20652173913043478,
			"text" : "weft",
			"reason" : "page"
		}, {
			"weight" : 0.17391304347826086,
			"text" : "threads",
			"reason" : "page"
		}, {
			"weight" : 0.16304347826086957,
			"text" : "heddles",
			"reason" : "page"
		}, {
			"weight" : 0.15217391304347827,
			"text" : "weaver",
			"reason" : "page"
		}
	],
	"uuid" : "52BD5C8C-C7FA-4BB5-9908-ED382C44AF6A"
}
```

## result log entry
```
2014-07-01 09:47:57,706 [RESULT] [userID:E993A29B-A063-426D-896E-131F85193EB7] [origin:chrome-extension://lpelppibhjnlojepdlfpcdolbflghcfe] [ip:132.231.111.197]
{
	"results" : [{
			"provider" : "mendeley",
			"id" : "bafa34c5-b28f-33ca-8190-2304fe4d0f15"
		}, {
			"provider" : "mendeley",
			"id" : "0d42bc58-32e4-3cea-869d-cf6d23339673"
		}, {
			"provider" : "mendeley",
			"id" : "db619daf-2080-3b10-9ef1-8ae1eafe6b19"
		}, {
			"provider" : "mendeley",
			"id" : "3a50dd56-c5d6-34a4-bbed-c0711dc76da8"
		}, {
			"provider" : "mendeley",
			"id" : "c73f8232-d58f-396f-a29a-6b2f3ed665ff"
		}, {
			"provider" : "mendeley",
			"id" : "4abfd690-897b-3a3e-b7fb-ba645cd09428"
		}, {
			"provider" : "mendeley",
			"id" : "1e34c4f1-0d7b-31a9-bd05-aa427da1913b"
		}, {
			"provider" : "mendeley",
			"id" : "a2cd10c7-a885-3a15-9542-4087a3a9b022"
		}, {
			"provider" : "mendeley",
			"id" : "f92abe09-74e2-3832-82cd-09d4c035c60d"
		}, {
			"provider" : "mendeley",
			"id" : "53c12934-68c2-33ba-b43c-e9c50b95831c"
		}
	],
	"query" : [{
			"weight" : 1,
			"text" : "loom",
			"reason" : "page"
		}, {
			"weight" : 0.4673913043478261,
			"text" : "looms",
			"reason" : "page"
		}, {
			"weight" : 0.34782608695652173,
			"text" : "shuttle",
			"reason" : "page"
		}, {
			"weight" : 0.33695652173913043,
			"text" : "weaving",
			"reason" : "page"
		}, {
			"weight" : 0.32608695652173914,
			"text" : "warp",
			"reason" : "page"
		}, {
			"weight" : 0.21739130434782608,
			"text" : "shed",
			"reason" : "page"
		}, {
			"weight" : 0.20652173913043478,
			"text" : "weft",
			"reason" : "page"
		}, {
			"weight" : 0.17391304347826086,
			"text" : "threads",
			"reason" : "page"
		}, {
			"weight" : 0.16304347826086957,
			"text" : "heddles",
			"reason" : "page"
		}, {
			"weight" : 0.15217391304347827,
			"text" : "weaver",
			"reason" : "page"
		}
	]
}
``` 

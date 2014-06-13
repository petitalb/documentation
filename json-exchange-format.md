# request format:

_TODO include Source Selection (WP3 pls fill in the current status)

```javascript
{
	"eexcess-user-profile": {
		"history": [{
			"id": "8",
			"lastVisitTime": 1402472311035.249,
			"title": "Loom - Wikipedia, the free encyclopedia",
			"typedCount": 4,
			"url": "http://en.wikipedia.org/wiki/Loom",
			"visitCount": 8
		}],
		"firstname": "max",
		"lastname": "muster",
		"gender": "male",
		"birthdate": "2013-05-14",
		"address": {
			"country": "in the middle of nowhere",
			"zipcode": "12345",
			"city": "somewhere",
			"line1": "beyond",
			"line2": "the hill"
		},
		/* Should we have user credentials?, e.g."userCredentials": {
			"Mendeley": {
				"email": "user@example.com",
				"securityToken": "abcd"
			}
		},
		*/
		/*Please add a compentence level (or similar) to theinterest, e.g. expert on recommender systems, but novice to search algorithms.*/
		"interests": [{
			//concepts"text": "Recommender systems",
			"weight": "1.0",
			"source": "manual",
			"confidence": "1.0",
			"uri": "http://dbpedia.org/resource/Category:Recommender_systems"
		},
		{
			"text": "Search algorithms",
			"weight": "1.0",
			/*defines the source of the context information, either manually input by the user or automatically inferred from interactions For automatic inference we also have a confidence score ranging fromo 0 to 1.*/
			"source": "automatic",
			"confidence:"0.7,
			"uri": "http://dbpedia.org/resource/Category:Search_algorithms"
		},
		{
			"text": "bratwurst",
			"source": "manual",
			"weight": "1.0"/*uri may not necessarily be present*/
		}],
		"context-list": {
			"locations": [{
				"text": "Vienna",
				"uri": "http://dbpedia.org/page/Vienna",
				"weight": "1.0",
				"confidence:"0.7,
				
			}],
			"persons": [{
				"text": "Renate Brauner",
				"uri": "http://dbpedia.org/page/Renate_Brauner",
				"weight": "1.0",
				"confidence:"0.7,
				
			}],
			"topics": [{
				"text": "Computer science",
				"weight": "1.0",
				"confidence:"0.7,
				"uri": "http://dbpedia.org/resource/Category:Computer_science"
			}],
			"context": [{
				"weight": "1.0",
				"text": "women"
			},
			{
				"weight": "1.0",
				"text": "workforce"
			}],
			"reason": {
				"reason": "manual",
				"text": "women workforce"
			}
		}
		/*Please make the user location an array, including a timestamp.*/
		"user-location": {
			"longitude": /* TODO define coordinate system */
			"latitude": ,
			"accuracy": "100" /* in meters, optional */
    }
}
```


# response format:
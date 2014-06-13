# request format:

_TODO include Source Selection (WP3 pls fill in the current status)_

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

example of what we currently get (federated recommender on development server) for query "loom":


```javascript
{
	"provider": "federated",
	"totalResults": "45",
	"results": [{
		"id": "e0f5ba6e-c6e9-3f3a-b123-b07d46415996",
		"title": "The butterfly and the loom",
		"uri": "http://www.mendeley.com/research/butterfly-loom/",
		"creator": "Rodney J. Douglas, Kevan A C Martin",
		"facets": {
			"provider": "mendeley",
			"year": "2007"
		}
	},
	{
		"id": "/2022343/8A1A98A25C53A5BD5F285C5B026ACF83BB3D2E38",
		"title": "Northrop single-shuttle 'S' loom with automatic bobbin inser",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F3014003%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022343/8A1A98A25C53A5BD5F285C5B026ACF83BB3D2E38",
		"facets": {
			"provider": "Europeana",
			"language": "en",
			"year": "1939"
		}
	},
	{
		"id": "sl23322297",
		"title": "Waugh, Alec",
		"uri": "http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23322297&s=BEP&v=eexcess&w=EEXCESS",
		"facets": {
			"provider": "wissenmedia",
			"language": "de",
			"year": "2013-12-11T10:42:02Z"
		}
	},
	{
		"id": "10008547915",
		"title": "Crisis Is Over, but Problems Loom Ahead",
		"uri": "http://www.econbiz.de/Record/10008547915",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2010-02"
		}
	},
	{
		"id": "7c55f59b-797f-360d-89ad-37c1b4aae80f",
		"title": "Loom-sensitive neurons link computation to action in the Drosophila visual system",
		"uri": "http://www.mendeley.com/catalog/loomsensitive-neurons-link-computation-action-drosophila-visual-system/",
		"creator": "Saskia E J De Vries, Thomas R. Clandinin",
		"facets": {
			"provider": "mendeley",
			"year": "2012"
		}
	},
	{
		"id": "/92022/1E9687A97769CA6B1A4514B71E17B8958160F3DE",
		"title": "Loom, Giant's Causeway, Co.Antrim",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.nli.ie%252Fglassplates%252Fthumbs%252FL_ROY%252FL_ROY_03344.jpg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/92022/1E9687A97769CA6B1A4514B71E17B8958160F3DE",
		"facets": {
			"provider": "Europeana",
			"language": "mul"
		}
	},
	{
		"id": "sl23516249",
		"title": "Berkshire Hathaway Inc.",
		"uri": "http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23516249&s=BEP&v=eexcess&w=EEXCESS",
		"facets": {
			"provider": "wissenmedia",
			"language": "de",
			"year": "2013-09-01T05:20:53Z"
		}
	},
	{
		"id": "10009414705",
		"title": "The decison loom : a design for interactive decision-making in organizations",
		"uri": "http://www.econbiz.de/Record/10009414705",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2011"
		}
	},
	{
		"id": "e30e84f2-0971-3db5-ae59-7e9d33552af8",
		"title": "Monetary losses do not loom large in later life: Age differences in the framing effect",
		"uri": "http://www.mendeley.com/catalog/monetary-losses-not-loom-large-later-life-age-differences-framing-effect/",
		"creator": "Joseph A. Mikels, Andrew E. Reed",
		"description": "Studies of the framing effect indicate that individuals are risk averse for decisions framed as gains but risk seeking for decisions framed as losses. However, findings regarding age-related changes in susceptibility to framing are mixed. Recent work demonstrating age-related decreases in reactivity to anticipated monetary losses, but not gains, suggests that older and younger adults might show equivalent risk aversion for gains but discrepant risk seeking for losses. In the current study, older and younger adults completed a monetary gambling task in which they chose between sure options and risky gambles (the expected outcomes of which were equated). Although both groups demonstrated risk aversion in the gain frame, only younger adults showed risk seeking in the loss frame.",
		"facets": {
			"provider": "mendeley",
			"year": "2009"
		}
	},
	{
		"id": "/2022320/DBB5F44C28DCB63A2E117DF8B884986B9D2AEF58",
		"title": "Loom",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F3490376%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022320/DBB5F44C28DCB63A2E117DF8B884986B9D2AEF58",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "sl23411688",
		"title": "Toyota Motor Corp.",
		"uri": "http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23411688&s=BEP&v=eexcess&w=EEXCESS",
		"facets": {
			"provider": "wissenmedia",
			"language": "de",
			"year": "2013-09-01T05:20:43Z"
		}
	},
	{
		"id": "10009568848",
		"title": "Losses loom more likely than gains : propensity to imagine losses increases their subjective probability",
		"uri": "http://www.econbiz.de/Record/10009568848",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2012"
		}
	},
	{
		"id": "9227ac1b-2c0c-370f-8021-3d078a8cc384",
		"title": "Vision system for on-loom fabric inspection",
		"uri": "http://www.mendeley.com/research/vision-system-onloom-fabric-inspection/",
		"creator": "Hamed Sari-Sarraf, James S. Goddard",
		"description": "This paper describes a vision-based fabric inspection system thataccomplishes on-loom inspection of the fabric under construction with100% coverage. The inspection system, which offers a scalable openarchitecture, can be manufactured at relatively low cost usingoff-the-shelf components. While synchronized to the motion of the loom,the developed system first acquires very high-quality vibration-freeimages of the fabric using either front or backlighting. Then, theacquired images are subjected to a novel defect segmentation algorithm,which is based on the concepts of wavelet transform, image fusion andthe correlation dimension. The essence of this segmentation algorithm isthe localization of those events (i.e., defects) in the input imagesthat disrupt the global homogeneity of the background texture. Theefficacy of this algorithm, as well as the overall inspection system,has been tested thoroughly under realistic conditions. The system wasused to acquire and to analyze more than 3700 images of fabrics thatwere constructed with two different types of yarn. In each case, theperformance of the system was evaluated as an operator introduceddefects from 26 categories into the weaving process. The overalldetection rate of the presented approach was found to be 89% with alocalization accuracy of 0.2 in (i.e., the minimum defect size) and afalse alarm rate of 2.5%",
		"facets": {
			"provider": "mendeley",
			"year": "1999"
		}
	},
	{
		"id": "/2022320/FF8D044999E1EAF995FF9D102BF71C25B2580347",
		"title": "Hand Loom",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F2076905%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022320/FF8D044999E1EAF995FF9D102BF71C25B2580347",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "sl23317833",
		"title": "Lloyd Loom",
		"uri": "http://service.wissens-server.com/wissensserver/view.html?a=t&r=CURRENT&i=sl23317833&s=BEP&v=eexcess&w=EEXCESS",
		"facets": {
			"provider": "wissenmedia",
			"language": "de",
			"year": "2010-02-05T03:39:50Z"
		}
	},
	{
		"id": "10010219753",
		"title": "Drivers of health care expenditure : does Baumol's cost disease loom large?",
		"uri": "http://www.econbiz.de/Record/10010219753",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2012"
		}
	},
	{
		"id": "426ee598-2665-3fbb-8c50-590ae52bfbd2",
		"title": "Small RNAs loom large during reprogramming",
		"uri": "http://www.mendeley.com/catalog/small-rnas-loom-large-during-reprogramming/",
		"creator": "Rupa Sridharan, Kathrin Plath",
		"facets": {
			"provider": "mendeley",
			"year": "2011"
		}
	},
	{
		"id": "/2022320/6EDA61624C26F34C02B790FB31B3FA8B1B12224C",
		"title": "Benjamin Armitages, Shepley - Sulzer loom, the weft feeding end of the loom.",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F2105681%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022320/6EDA61624C26F34C02B790FB31B3FA8B1B12224C",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "10010310985",
		"title": "Drivers of health care expenditure: Does Baumol's cost disease loom large?",
		"uri": "http://www.econbiz.de/Record/10010310985",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2012"
		}
	},
	{
		"id": "de0869f7-0334-366b-9693-19e042669b71",
		"title": "On-loom warping for the Navajo loom",
		"uri": "http://www.mendeley.com/research/onloom-warping-navajo-loom/",
		"creator": "I M Freilinger",
		"description": "Materials are listed and warping instructions are given for the Navajo hand loom.",
		"facets": {
			"provider": "mendeley",
			"year": "1980"
		}
	},
	{
		"id": "/92022/871327702DD732FD8DE72988738D77E07159B766",
		"title": "Loom, Giant's Causeway, Antrim",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.nli.ie%252Fglassplates%252Fthumbs%252FL_CAB%252FL_CAB_00323.jpg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/92022/871327702DD732FD8DE72988738D77E07159B766",
		"facets": {
			"provider": "Europeana",
			"language": "mul"
		}
	},
	{
		"id": "10003942723",
		"title": "Crisis is over, but problems loom ahead",
		"uri": "http://www.econbiz.de/Record/10003942723",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2010"
		}
	},
	{
		"id": "11112d47-58bb-3f07-a345-af9657ae7bc8",
		"title": "Shape of things: Understanding a loom weight",
		"uri": "http://www.mendeley.com/research/shape-things-understanding-loom-weight/",
		"creator": "Linda M??rtensson, Marie Louise Nosch, Eva Andersson Strand",
		"description": "Loom weights are common finds in archaeological excavations in Europe and the Near East. They represent the only remains of warp-weighted looms. The function of the warp-weighted loom is well known from ethnographic studies. The function of loom weights, however, has not been investigated and cannot be deduced directly from ethnographical data, since loom weights in antiquity were very different from those used in the twentieth century AD. This paper reviews the functional elements of a loom weight. The weight and thickness of loom weights are established as the defining functional parameters for the operation of the warp-weighted loom. A series of systematic tests demonstrated that the weight of a loom weight defines what yarn (thickness) to use and the thread density. The thickness of a loom weight, and thus the width of the row of loom weights hanging closely together, defines the width of a fabric and – together with the weight of the loom weight – the thread count and density of the fabric. This new knowledge provides the methodological framework for archaeologists to calculate textile production possibilities from any given loom weight, as long as the weight and thickness are preserved. Furthermore, it allows scholars to assess textile production on sites where no textiles are preserved. But only for a given thickness and quality of woolen yarn. And this is not defined in any given site! The article provides some principles, and optimal and less optimal options.",
		"facets": {
			"provider": "mendeley",
			"year": "2009"
		}
	},
	{
		"id": "/2022343/C3494560951539055420DDC9CE3B760E2B63D4E0",
		"title": "Power loom, 1924",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F3165344%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022343/C3494560951539055420DDC9CE3B760E2B63D4E0",
		"facets": {
			"provider": "Europeana",
			"language": "en",
			"year": "1926"
		}
	},
	{
		"id": "10009740462",
		"title": "Dissecting home regionalization : how large does the region loom?",
		"uri": "http://www.econbiz.de/Record/10009740462",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2013"
		}
	},
	{
		"id": "593d22b4-344b-3395-a91b-f7a2206ddd34",
		"title": "MicroRNAs loom large in the heart.",
		"uri": "http://www.mendeley.com/research/micrornas-loom-large-heart/",
		"creator": "Michael Basson",
		"description": "How microRNAs (miRNAs) influence heart development and disease is a topic of growing interest. miRNAs regulate gene expression post-transcriptionally, typically by binding to mRNAs and inhibiting their translation. Three recent papers show that miRNAs are essential for heart development and function, regulating the expression of genes involved in electrical conductance, hypertrophy and contractility.",
		"facets": {
			"provider": "mendeley",
			"year": "2007"
		}
	},
	{
		"id": "/92022/42AD37EE1B18E06C9EB2AD46469D848F837CF3FB",
		"title": "Loom, Giant's Causeway, Co.Antrim",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.nli.ie%252Fglassplates%252Fthumbs%252FL_ROY%252FL_ROY_02242.jpg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/92022/42AD37EE1B18E06C9EB2AD46469D848F837CF3FB",
		"facets": {
			"provider": "Europeana",
			"language": "mul"
		}
	},
	{
		"id": "10008577283",
		"title": "Monetary Losses Do Not Loom Large in Later Life: Age Differences in the Framing Effect",
		"uri": "http://www.econbiz.de/Record/10008577283",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2009"
		}
	},
	{
		"id": "703e426d-b742-32c9-9a3a-ea52172e2a97",
		"title": "When gains loom larger than losses: Reversed loss aversion for small amounts of money",
		"uri": "http://www.mendeley.com/catalog/gains-loom-larger-losses-reversed-loss-aversion-small-amounts-money/",
		"creator": "Fieke Harinck, Eric Van Dijk, Ilja Van Beest, Paul Mersmann",
		"description": "Previous research has generally shown that people are loss averse; that is, they weigh losses more heavily than gains. In a series of three experiments, we found that for small outcomes, this pattern is reversed, and gains loom larger than losses. We explain this reversal on the basis of (a) the hedonic principle, which states that individuals are motivated to maximize pleasure and to minimize pain, and (b) the assumption that small losses are more easily discounted cognitively than large losses are.",
		"facets": {
			"provider": "mendeley",
			"year": "2007"
		}
	},
	{
		"id": "/2022350/90CFC376B420D8E9C93FB036C6F9019E1CFA637E",
		"title": "loom",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F4958279%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022350/90CFC376B420D8E9C93FB036C6F9019E1CFA637E",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "10009492734",
		"title": "Crisis Is Over, but Problems Loom Ahead",
		"uri": "http://www.econbiz.de/Record/10009492734",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2010-02"
		}
	},
	{
		"id": "c5e2db08-3774-36d3-958e-f4fa18489569",
		"title": "Spanish colonial loom",
		"uri": "http://www.mendeley.com/research/spanish-colonial-loom/",
		"creator": "J Edwards",
		"description": "A replica of a seventeenth century Spanish colonial loom for the Albuquerque Museum has just been completed. Period tools were used to make the loom. Tie up graft drafts are included.",
		"facets": {
			"provider": "mendeley",
			"year": "1986"
		}
	},
	{
		"id": "/2022350/20C595FA93425DCC255437E865E8FD5218CB533E",
		"title": "loom",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F4957872%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022350/20C595FA93425DCC255437E865E8FD5218CB533E",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "10009144347",
		"title": "While America Aged: How Pension Debts Ruined General Motors, Stopped the NYC Subways, Bankrupted San Diego, and Loom as the Next Financial Crisis. Roger Lowenstein. Penguin Press, 2008, ISBN 978-1-59420-167-7, 275 pages.",
		"uri": "http://www.econbiz.de/Record/10009144347",
		"facets": {
			"provider": "ZBW",
			"language": "de",
			"year": "2011"
		}
	},
	{
		"id": "237f3a0f-47c4-3edf-89de-f9b2d7d85e8b",
		"title": "Losses loom more likely than gains: Propensity to imagine losses increases their subjective probability",
		"uri": "http://www.mendeley.com/catalog/losses-loom-more-likely-gains-propensity-imagine-losses-increases-subjective-probability/",
		"creator": "Baler Bilgin",
		"facets": {
			"provider": "mendeley",
			"year": "2012"
		}
	},
	{
		"id": "/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680",
		"title": "loom",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F4957873%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022350/542DF28412FF874428B9FAB96756B2AE88B3A680",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "9b76a6f2-6ac2-3319-8269-862fffe11626",
		"title": "Revisiting the jacquard loom: threads of history and current patterns in HCI",
		"uri": "http://www.mendeley.com/catalog/revisiting-jacquard-loom-threads-history-current-patterns-hci/",
		"creator": "Ylva Fernaeus, Martin Jonsson, Jakob Tholander",
		"description": "In the recent developments of human computer interaction, one central challenge has been to find and to explore alternatives to the legacy of the desktop computer paradigm for interaction design. To investigate this issue further we have conducted an analysis on a fascinating piece of machinery often referred to as one of the predecessors of the modern day computer, the Jacquard loom. In analysing the Jacquard loom we look at qualities in design and interaction from some different perspectives: how historical tools, crafts, and practices can inform interaction design, the role of physicality, materiality, and whole-body interaction in order to rethink some current conceptions of interaction and design of computational devices.",
		"facets": {
			"provider": "mendeley",
			"year": "2012"
		}
	},
	{
		"id": "/2022343/33B5639C9E85303EA1DB04E130E6A3A81B841EF2",
		"title": "Wooden loom bobbin winder.",
		"previewImage": "http://europeanastatic.eu/api/image?uri=http%253A%252F%252Fwww.culturegrid.org.uk%252Fdpp%252Fresource%252F3013593%252Fstream%252Fthumbnail_image_jpeg&size=LARGE&type=IMAGE",
		"uri": "http://europeana.eu/resolve/record/2022343/33B5639C9E85303EA1DB04E130E6A3A81B841EF2",
		"facets": {
			"provider": "Europeana",
			"language": "en"
		}
	},
	{
		"id": "cdd0cf8d-0378-30af-bed4-d70cdaca1cdc",
		"title": "Chronic Mental Health Issues in Children Now Loom Larger Than Physical Problems",
		"uri": "http://www.mendeley.com/catalog/chronic-mental-health-issues-children-now-loom-larger-physical-problems/",
		"creator": "Anita Slomski",
		"description": "Slomski, A. (2012). Chronic mental health issues in children now loom larger than physical problems. JAMA, 308, 223-225. doi:10.1001/jama.2012.6951",
		"facets": {
			"provider": "mendeley",
			"year": "2012"
		}
	},
	{
		"id": "89a9d18f-b50a-3ab4-94a5-7715dcf5335a",
		"title": "Loom of Life: Unravelling Ecosystems",
		"uri": "http://www.mendeley.com/research/loom-life-unravelling-ecosystems/",
		"creator": "M Schilthuizen",
		"description": "This 161-page book consists of 9 extensive chapters written in English. Topics focused include wildcard ecology, unravelling ecosystem and the ecosystem ripper. This book helps students and the general readers to bridge the gap between the niche and the staggering global biodiversity.",
		"facets": {
			"provider": "mendeley",
			"year": "2008"
		}
	},
	{
		"id": "8d019179-0e84-3836-a30b-90db12be8a61",
		"title": "Shelburne's jacquard loom: is it a computer?",
		"uri": "http://www.mendeley.com/research/shelburnes-jacquard-loom-it-computer/",
		"creator": "T V Noorda",
		"description": "A jacquard loom donated to the Shelburne Museum in Shelburne, Vermont, by Franco Scalamandre is highlighted. How the loom works, along with an analysis of how complicated patterns are programmed and the relationship between the loom and a digital computer, are all discussed.",
		"facets": {
			"provider": "mendeley",
			"year": "1986"
		}
	},
	{
		"id": "704f1ac0-1e15-3036-8c07-457eef056772",
		"title": "Cloned animals deemed safe to eat, but labeling issues loom.",
		"uri": "http://www.mendeley.com/research/cloned-animals-deemed-safe-eat-labeling-issues-loom/",
		"creator": "Jeffrey L Fox",
		"description": "Cloning is a tool that allows genetic modifications and is the efficient means for doing so. US Food and Drug Administration (FDA) and European Food Safety Authority issued a draft that clone-derived foods are safe for human consumption. Cloned animals are different from transgenic animals according to Biotechnology Industry Organization.",
		"facets": {
			"provider": "mendeley",
			"year": "2008"
		}
	},
	{
		"id": "f92ae8ec-281a-3db5-92f2-1a742010709a",
		"title": "Inside the LOOM description classifier",
		"uri": "http://www.mendeley.com/research/inside-loom-description-classifier/",
		"creator": "Robert M. MacGregor",
		"description": "This paper presents a symbol level account of some of the representation and reasoning structures within the LOOM knowledge representation system. Reasoning in LOOM centers around a classifier whose primary function is to construct a taxonomy of all descriptions that have been entered into the system. The LOOM classifier is unique in that it constructs a separate taxonomy for each of seven kinds of non-composite descriptions, and uses a marker passing algorithm to replace the quadratic time subsumption test found in most classifiers with a linear time test. We briefly illustrate how the selection of data structures within LOOM impacts the completeness of the classification algorithm, and we describe the LOOM option that allows concepts to be reasoned with in either a forward-chaining or a backward-chaining mode.",
		"facets": {
			"provider": "mendeley",
			"year": "1991"
		}
	},
	{
		"id": "f7b1a07b-fe97-3211-a45d-869c0d7f750f",
		"title": "LOOJ: Weaving LOOM into Java",
		"uri": "http://www.mendeley.com/catalog/looj-weaving-loom-java/",
		"creator": "Martin Odersky, Kim B Bruce, J Nathan Foster",
		"description": "{LOOJ} is an extension of Java obtained by adding bounded parametric polymorphism and new type expressions {ThisClass} and {ThisType,} which are similar to {MyType} in {LOOM.} Through examples we demonstrate the utility of this language even over very expressive extensions such as {GJ.} The {LOOJ} compiler generates standard {JVML} code and supports instanceof and casts for all types including type variables and the other new type expressions. The core of the {LOOJ} type system is sound, as demonstrated by a soundness proof for an extension of Featherweight {GJ.} This paper also highlights difficulties that arise from the use of both classes and interfaces as types in Java. Keywords: Object-oriented language design, static type systems, {MyType,} {ThisClass,} {ThisType,} formal semantics.",
		"facets": {
			"provider": "mendeley",
			"year": "2004"
		}
	},
	{
		"id": "127fe9c8-ff7f-3f4f-b726-7dba6849c93d",
		"title": "The Loom of Latin",
		"uri": "http://www.mendeley.com/research/loom-latin/",
		"creator": "Michael C. J. Putnam",
		"description": "Page 1. Transactions of the American Philological Association 131 (2001) 329-339 Michael CJ Putnam Brown University",
		"facets": {
			"provider": "mendeley",
			"year": "2001"
		}
	}]
}
```
# Proposal for implementing the visualisation detail call

### Actual state
Here a very simplified description of the actual implementation:
The UI e.g Chrome plugin calls the recommend method of the PrivacyProxy(PP), which calls the FederatedRecommender(FR). The FR knows all registered PartnerRecommender(PR) and forwards the recommender call to each PR. Each PR calls the configured Partner API with a search-command. If necessary the PR make additional calls to the Partner API to get more detailed data. This data is merged in one response XML and this is transformed to the EEXCESS Data format. After this, the enrichment of the results will be done, if the enrichment is activated. The results are returned to the FR. The FR takes the results from each responding  PR and creates one list of records. It’s possible that the FR removes single records from the resulting list. The FR returns the data via PP to the Chrome plugin.

### Whats the Problem:
* The additional details-service calls from the PR costs a lot of processing time and adds latency from additional network traffic.
* We need to reduce the data transferred during the recommender call to increase performance.

## Proposal of a solution
Remove the detail calls in the PR in the recommend method. Remove the enrichment of the results in the recommend method. Return only a few data to the FR. Therefor create a simplified mapping with the ConfigTool and use this transformation.

The format of the results can be found here: https://github.com/EEXCESS/documentation/blob/master/result-format-proposal.md

If one of the fields are not in the service response from the partner API the value of the field will be left empty.

In this first resultList there will also no RDF included, only the XML will returned. If the UI(ChromePlugin) needs more data for single records, the new detail call can used to get this information.

### new Detail call 
This new Detail call will be called from the UI(ChromePlugin) to get more detailed data to records.

*Method name:*
fetchDetails

*input data:*
List of DocumentBadge (see https://github.com/EEXCESS/documentation/blob/master/result-format-proposal.md)

*returns:*
List of documentBadge extendet wiht a field for the RDF.

This method must added to the PP. In a first implementation in the PP can be simply forward to the FR. Later the PP will add fake documentBadges to obfuscate the request and the user interest are protected.

This method must be added to the FR. The implementation takes the list and cuts it down for every registered PR and calls the new method of the PR. The results are pasted together and returned to the PP.

This method must be added to all PR. The PR takes the URI or identifier, build a detail call for the record. The API response will be transformed via a detailed mapping from the ConfigTool into the EEXCESS data format(RDF). After collecting the data, the list will returned from the PR to the FR. 

## Detail Metadata in RDF

The visualization needs the following meta data fields:

* Time metadata: timestamp or time interval
 Preferably also:
  * semantic descriptors (e.g. publication date, birth/death date, found date, etc.)
  * period name (e.g. antiquity, renaissance)
  * "fuzzy" flag (uncertainty)
* Geo references: Lat/Long coordinates
Preferably also:
  * semantic descriptors (publication place, birth/death place, exhibition place etc.)
  * place type (city, region, country...)
  * place name
  * "fuzzy" flag (uncertainty)
* mime type
* source (data provider)
* language
* subjects/keywords
* link (URL)
* title
* snippet/abstract
* thumbnail
* trust enabling metadata


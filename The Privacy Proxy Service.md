# The Privacy Proxy Service

You can reach 3 types of service on the Privacy Proxy :
* Recommender Service
* Log Service
* Category suggestion Service

## Recommender service

You can reach this service by calling `{host}:{port}/eexcess-privacy-proxy/api/v1/recommend`. This service forwards the query to the Federated Recommender and return the recommendations. 
It takes as input a POST request with JSON file (the format is describe in the documentation: [json exchange format](https://github.com/EEXCESS/documentation/wiki/json-exchange-format)) and return the answer as a JSON format.

## Log service

This service is used to log on the Privacy Proxy the interaction with the user. You can reach this service by calling `{host}:{port}/eexcess-privacy-proxy/api/v1/log/{InteractionType}`. Everything is described in the documentation: [logging on privacy proxy](https://github.com/EEXCESS/documentation/wiki/logging-on-privacy-proxy).

## Category suggestion Service

You can reach this service by calling `{host}:{port}/eexcess-privacy-proxy/api/v1/disambiguate`. The service is used to suggest DBpedia categories when the user specifies interests on the profile page. It forwards the query to another REST API (hosted by Passau) that does the job and return suggestions of DBpedia-categories. 

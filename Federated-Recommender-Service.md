# The Federated Recommender Service

##  Reaching the Service
You can reach the Service, based on the location where the service is running,by calling 
`{host}:{port}/eexcess-federated-recommender-web-service-1.0-SNAPSHOT/recommender/{call}`.

## The Service Calls

All services consume and/or produce xml and json aswell depending on which type is defined as content type. 


###  Register
`/register` (POST)
This is the service to register a new partner to be queried by the system.
Consumes a partnerBadge (example partner badge can be produced by calling /testBadge with the correct format (json/xml)), with all the information needed to connect to the partner.




###  Get Registered Partners
 `/getRegisteredPartners` (GET)
Produces the list of partners registered in the System and some rudimentary statistics about the partners.

* requestCount: count of requests done by the server on the partner
* failedRequestCount: failed requests of any kind (including timeouts)
* shortTimeResponseTimes: average of the last ten responses
* shortTimeResponsDeviation: deviation of the last ten responses
* longTimeResponseTimes: overall average since the server was restarted


###  Recommend
`/recommend` (POST)
This is the actuall recommendation call and consumes a SecureUserProfile (example can be generated with the /testSUP call).
In this SecureUserProfile a list of servers can be integrated which will be used to query these specific partners. (The partnerBadge which you get from /getRegisteredPartners call has to be in this list)

###  Test Recommend
`/testRecommend` (GET)
This is a test recommendation call.

###  Test Badge
`/testBadge` (GET)
This call produces a example partner Badge.

###  Test Secure User Profile
`/testSUP` (GET)
This call produces a example secure user profile.


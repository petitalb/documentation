This page provides a guide how to integrate a new data provider into the EEXCESS Framework. 

# Define a Mapping

As a first step we create a mapping from the service response to the EEXCESS format. Therefore it’s helpful to have an example response of the data providers-service. The ConfigTool is available at: http://eexcess.joanneum.at/configtool/. To get a user and password please get in contact with feedback@eexcess.eu.
The ConfigTool is a tool that allows the creation of a mapping from a local data structure to the EEXCESS data format without implementation skills. It offers user interfaces for all steps of mapping creation right from opening a mapping project to the creation of the XSL transformation file.
Here we give a brief introduction to the ConfigTool: 

1. Create a new project with the ConfigTool, while entering a name for the project and select a Source Schema and a Target Schema. 
A “project” here is a very special mapping from one local data format (Source Schema) to an output data format (Target Schema, here: EEXCESS data format).
2. Create a concept in the Source Schema for every field which needs to be mapped. 
3. Define mappings from the new Concepts in the Source Schema to the MEON-Concepts. The MEON-Concepts already contain the definition of the EEXCESS data format in which the local data should be mapped. 
4. When all mappings are defined Transformation-Files can be created directly with the ConfigTool (Menu Transformation -> Create XSL). This Transformation-File is used in the PartnerRecommender later on.

# Create a new PartnerRecommender
The PartnerRecommender and the FederatedRecommender are written in JAVA. The source code is published on github:https://github.com/EEXCESS/recommender.
This is the folder-structure:

* Code
  * Partners
    * EUROPEANA
    * KIM.collect
    * Mendeley
    * wissenmedia
    * ZBW
  * Recommender
  * Reference
    * Partner-data-layer
    * PartnerRecommender
    * Partner-web-service

These structure and folders are used to build PartnerRecommender. In the folder “partners” implementations and configurations for the existing data providers are all already available. In the folder “reference” the API’s from WP3 und WP4 and der REST-Service of the PartnerRecommender can be found. 

# Configure the PartnerRecommender – ConfigFile

`
{
  "partnerConnectorClass": "eu.eexcess.zbw.recommender.PartnerConnector",
  "queryGeneratorClass": "eu.eexcess.zbw.recommender.ZBWQueryGenerator",
  "searchEndpoint": "https://api.econbiz.de/v1/search?q=${query}&xml=true",
  "transformerClass": "eu.eexcess.zbw.datalayer.ZBWTransformer",
  "mappingListTransformationFile":"mapperResultList.xsl",
  "mappingObjectTransformationFile":"mapperObject.xsl"
}
`

The parameter partnerConnectorClass defines the JAVA-Class which will be used to call the service of the partner data store. To get data out of the partner data store it’s necessary to call the API of the partner data store. For this it’s necessary to configure an already existing PartnerConnector or implement a new one with creating a new class which implements the Interface ParnterConnectorApi.

The parameter queryGeneratorClass defines the JAVA-Class which creates the query for the service. The query generator is responsible for translating the EEXCESS user profile into a query string. The user profile contains special user information as for instance special themes the user is interested in, often used keywords in queries. Details to the user profile are specified in work package 5 and therefore not part of the present deliverable. 
For example: If a user is interested in a special theme and the user puts this into his own user profile – this is under his own responsibility in order to stick to privacy guidelines – these user profile information is added to the query request sent to the PartnerRecommender. This is a first enrichment of the result list depending on user profile information.

The parameter searchEndpoint defines the URL where the service is available. The parameter transformerClass defines the JAVA-Class which transforms the results from the format of the service of the data provider to the EEXCESS format. The parameters mappingListTransformationFile and mappingObjectTransformationFile defines the transformations into the EEXCESS format for result-lists or single objects. The transformation files from the ConfigTool must be put in the sub-folder \src\main\resources\. The filenames must be the same as for the parameters mappingListTransformationFile and mappingObjectTransformationFile as configured in the PartnerRecommender-ConfigFile.

# Extend the FederatedRecommender
In the next step the FederatedRecommender must be changed to call the new PartnerRecommender. Therefore open the project modules\recommender\federated-recommender-web-service and extend the method “initialize” in the Class FederatedRecommenderService. Add the new PartnerRecommender via a PartnerBadge like the already existing PartnerRecommenders are added.

# Creation and Deployment of the war-File
Build the new PartnerRecommender and the modified FederatedRecommender with maven and deploy the new war-files to the Tomcat. After deploying both web-apps, the client should also show results from the newly added data provider, if some objects matches to the information need which the client detects.

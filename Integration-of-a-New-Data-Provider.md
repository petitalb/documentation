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
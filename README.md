# CosmosDB-Gremlin-Synapse

This repo contains example notebook using Cosmos Gremlin API to explore/illustrate Graph Analytical use-cases using Synapse Spark GraphFrames library.


## Prep-step to create Synapse Link for your Cosmos Gremlin API account
Since Synapse link currently does not support (yet) CosmosDB Gremlin API directly – to make this connection work we need to use CORE SQL API endpoint URI for Cosmos Gremlin API account (thanks to a multi-model support of Cosmos Gremlin API).
![Cosmos .NET URI](/images/CosmosURI_LI.jpg?raw=true "Cosmos .NET URI")

And when creating Cosmos Synapse Linked service - instead of using option “from Azure subscription” , use  “Enter manually” (alternatively URI/key can be used via KeyVault) .
Copy/paste that URI and the key for your Gremlin API account – and enter DatabaseName (which is the same as your Graph name) from that account manually and test connection.
![Cosmos Synapse Link](/images/SynapseLink_LI.jpg?raw=true "Cosmos Synapse Link")
 
This is essentially replicating the way of connecting from Databricks Spark to Cosmos Gremlin API account (using SQL API endpoint URI/key and database in Cosmos spark config options) described here:
"https://github.com/Azure/azure-cosmosdb-spark/blob/master/samples/notebooks/On-Time%20Flight%20Performance%20with%20Spark%20and%20Cosmos%20DB%20-%20Seattle.ipynb" 

Once you complete creating linked service - you should be able to see it under CosmosDB branch in "Linked Serfvices".
![Cosmos Synapse](/images/Synapse_Cosmos.png?raw=true "Cosmos Synapse")
 
Note - that you will not be able to see automatic collections (actual Graphs discovery) when expanding it in the UI - but instead you would define container/graph as part of Cosmos DB options for spark.read.format when exploring it via notebook).

Now you are ready to import the sample notebook from this repo, load the data sample from the initial cell into Cosmos Gremlin API and experiment with GraphFrame analytical library examples.

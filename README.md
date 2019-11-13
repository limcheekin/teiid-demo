# teiid-demo
The demo created with the following tools:
 * [Teiid Designer 11.1.2](http://teiid.io/teiid_runtimes/teiid_wildfly/downloads/#teiid-designer) ([User Guide](http://docs.jboss.org/teiid/designer/11.1.2/user-guide/html_single/), [Examples](https://developer.jboss.org/wiki/TeiidDesignerExamples)) 
 * [Teiid Runtime 9.0.6](http://teiid.io/legacy/downloads_900/)

## Setup and Running 
Start the server with the following command:
```
standalone.sh -c standalone-teiid.xml
```

Before you can connect to Teiid Connection and OData endpoint, you need to create a user with `user,odata` group with the following command
```
add-user.sh
```
Please see the following URL for more information: https://developer.jboss.org/thread/277216

If you would like to create source model from MongoDB collection ([Importer Properties](https://teiid.gitbooks.io/documents/content/reference/MongoDB_Translator.html#_importer_properties)), first you need to install the mongodb JCA module with the following command:
```
jboss-cli.sh -c --file=setup/mongodb.cli
```
Modify the value of `jndi-name`, `RemoteServerList`, `Database` specific to your MongoDB instance.
You can find out more information from https://github.com/teiid/teiid-wildfly-quickstarts/tree/master/mongodb-as-a-datasource

## OData Endpoint
Access the metadata of the VDB with the following URL:
```
http://localhost:8080/odata/TeiidVDB/$metadata
```

Access the data of product view model in JSON format with the following URL:
```
http://localhost:8080/odata/TeiidVDB/Teiid_Demo.product?$format=json
```
__Note:__ View model need to have primary key defined in order to expose it as OData entity, please goto the URL for more information https://developer.jboss.org/thread/243737
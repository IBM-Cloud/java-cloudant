# Java Cloudant Web Starter Overview

The Java Cloudant Web Starter demonstrates how to use the Bluemix Cloudant NoSQL DB service. This application helps users organize their favorite files. The UI talks to a RESTful JAX-RS CRUD backend API.

### Running the application locally in Liberty

1. Download all the [ektorp dependency jars](https://maven-repository.com/artifact/org.ektorp/org.ektorp/1.4.2) and copy them to `${server.config.dir}/lib`  (`wlp/usr/servers/defaultServer/lib`). Use the commands below for reference, replacing the value for `outputDirectory`:

    ```
    # Download all the jars
    mvn dependency:get -Dartifact=org.ektorp:org.ektorp:1.4.2
    
    # Copy to liberty lib directory
    mvn dependency:copy-dependencies -f $HOME/.m2/repository/org/ektorp/org.ektorp/1.4.2/org.ektorp-1.4.2.pom -DoutputDirectory=$HOME/wlp/usr/servers/defaultServer/lib
    ```
    
2. In your server.xml, create a shared `library` definition for all the jars and add a classloader element to the `webApplication` element as shown below
    ```
    	<library id='cloudantNoSQLDB-library'>
    		<fileset dir='${server.config.dir}/lib'
    			id='cloudantNoSQLDB-fileset'
    			includes='commons-codec-1.6.jar
    			commons-io-2.0.1.jar
    			commons-logging-1.1.1.jar
    			httpclient-4.2.5.jar
    			httpclient-cache-4.2.5.jar
    			httpcore-4.2.5.jar
    			jackson-annotations-2.2.2.jar
    			jackson-core-2.2.2.jar
    			jackson-databind-2.2.2.jar
    			jcl-over-slf4j-1.6.6.jar
    			org.ektorp-1.4.1.jar
    			slf4j-api-1.6.6.jar
    			slf4j-jdk14-1.6.6.jar'/>
    	</library>

    	<webApplication contextRoot="JavaCloudantDBApp" id="JavaCloudantApp"
    		location="JavaCloudantDBApp.war" name="JavaCloudantApp">
    		<classloader commonLibraryRef="cloudantNoSQLDB-library" />
    	</webApplication>
    ```
3. Add your Cloudant credentials to `src/example/nosql/CloudantClientMgr.java`
    ```
    	user = "REPLACE_WITH_CLOUDANT_USERNAME";
    	password = "REPLACE_WITH_CLOUDANT_PASSWORD";
    ```
## Decomposition

* See src/example/nosql/CloudantClientMgr.java for how to obtain and use the Cloudant credentials
* See src/example/nosql/AttachServlet.java for the file upload API
* See src/example/noqsl/ResourceServlet.java for the file CRUD API
* See WebContent/index.js and WebContent/util.js for how the front-end calls the back-end API

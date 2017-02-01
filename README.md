# Java Cloudant Sample

This application demonstrates how to use the Bluemix Cloudant NoSQL Database service. It helps users organize their favorite files. The UI talks to a RESTful JAX-RS CRUD backend API.

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/IBM-Bluemix/java-cloudant)

## Building and running the application using the command-line

1. Open the [Bluemix dashboard](https://bluemix.net), create/select your Cloudant service -> Service Credentials  -> View Credentials
  - Copy the credentials to src/main/java/example/nosql/CloudantClientMgr.java
  
    ```
      user = "REPLACE_WITH_CLOUDANT_USERNAME";
      password = "REPLACE_WITH_CLOUDANT_PASSWORD";
    ```  

2. Execute full Maven build to create the `target/JavaCloudantApp.war` file:
    ```bash
    $ mvn clean install
    ```

3. Download and start a local Liberty server with the application:
    ```bash
    $ mvn liberty:run-server
    ```

    Once the server is running, the application will be available under [http://localhost:9080/JavaCloudantApp](http://localhost:9080/JavaCloudantApp).

4. Update the application details in the `manfest.yml` file. Change the `name` field to your Bluemix Application Name. Use the following command to push the application to Bluemix:
    ```bash
    $ cf push
    ```

## Developing and Deploying using Eclipse

IBM® Eclipse Tools for Bluemix® provides plug-ins that can be installed into an existing Eclipse environment to assist in integrating the developer's integrated development environment (IDE) with Bluemix.

1. Download and install  [IBM Eclipse Tools for Bluemix](https://developer.ibm.com/wasdev/downloads/#asset/tools-IBM_Eclipse_Tools_for_Bluemix).

2. Import this sample into Eclipse using `File` -> `Import` -> `Maven` -> `Existing Maven Projects` option.

3. Create a Liberty server definition:
  - In the `Servers` view right-click -> `New` -> `Server`
  - Select `IBM` -> `WebSphere Application Server Liberty`
  - Choose `Install from an archive or a repository`
  - Enter a destination path (/Users/username/liberty)
  - Choose `WAS Liberty with Java EE 7 Web Profile`
  - Continue the wizard with default options to Finish

4. Open the [Bluemix dashbaord](bluemix.net) create/select your Cloudant service -> Service Credentials  -> View Credentials
  - Copy the credentials to src/example/nosql/CloudantClientMgr.java
  
    ```
      user = "REPLACE_WITH_CLOUDANT_USERNAME";
      password = "REPLACE_WITH_CLOUDANT_PASSWORD";
    ```  

4. Run your application locally on Liberty:
  - Right click on the `JavaCloudantApp` sample and select `Run As` -> `Run on Server` option
  - Find and select the localhost Liberty server and press `Finish`
  - In a few seconds, your application should be running at http://localhost:9080/JavaHelloWorldApp/

5. Create a Bluemix server definition:
  - In the `Servers` view, right-click -> `New` -> `Server`
  - Select `IBM` -> `IBM Bluemix` and follow the steps in the wizard.
  - Enter your credentials and click `Next`
  - Select your `org` and `space` and click `Finish`

6. Run your application on Bluemix:
  - Right click on the `JavaCloudantApp` sample and select `Run As` -> `Run on Server` option
  - Find and select the `IBM Bluemix` and press `Finish`
  - A wizard will guide you with the deployment options.
  - Select your Cloudant service on the Services step
  - In a few minutes, your application should be running at the URL you chose.

Now you have your code running locally and on the cloud!

[Liberty Maven Plug-in]: https://github.com/WASdev/ci.maven

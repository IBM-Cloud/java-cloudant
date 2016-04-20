# Java Cloudant Web Starter Overview

The Java Cloudant Web Starter demonstrates how to use the Bluemix Cloudant NoSQL DB service. The app displays persisted files and lets the user upload new files or delete old files.

## Decomposition Instructions

* See src/example/nosql/CloudantClientMgr.java for how to obtain and use the Cloudant credentials
* See src/example/nosql/AttachServlet.java for the file upload API
* See src/example/noqsl/ResourceServlet.java for the file CRUD API
* See WebContent/index.js and WebContent/util.js for how the front-end calls the back-end API

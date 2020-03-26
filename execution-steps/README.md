# Ephesoft Execution Steps

Step 1 : The document to be OCR-ed should be available at the folder mentioned in the ![CMIS Import Path](https://github.com/sherrymax/ephesoft/tree/master/configuration-steps#2-cmis-import).
Step 2 : The Ephesoft will pull in the document (mentioned at Step 1) at the ![interval which CMIS server is configured to be monitored](https://github.com/sherrymax/ephesoft/tree/master/configuration-steps#5-cron-job-expression).
Step 3 : Login to ![Batch Instance Management](http://<host-name>:8080/dcma/BatchInstanceManagement.html), for any validations or error monitoring.
Step 4 : The document will be exported to the Folder mentioned in ![CMIS Export](https://github.com/sherrymax/ephesoft/tree/master/configuration-steps#3-cmis-export).
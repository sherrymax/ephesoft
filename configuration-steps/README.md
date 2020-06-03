# Ephesoft Configuration Steps

## 1. Prepare and manage batch classes
Please follow these steps for batch class management.
1. Login to [Batch Class Management](http://<host-name>:8080/dcma/BatchClassManagement.html)![](resources/1.png)
2. Credentials -  `ephesoft/demo`![](resources/3.png)
3. Successful login will route to this Batch Class Management screen. Double click the last row, which is the Batch Class created for this tutorial. ![](resources/4.png)
4. Ephesoft has to be trained on the files that are to be OCR-ed. To do this, please upload a sample of the document as shown here.![](resources/4a.png)
A sample contract document is available [here](resources/Sample-ContractDocument.pdf).
5. The view is updated with more details of the batch. Now the document types configured in this batch to be OCR-ed are available.![](resources/5.png)
6. Double click on a Document Type to open it.![](resources/7.png)
7. Select an Index Type related to a Document Type![](resources/7a.png)
   P.S: Keep the `OCR Confidence Level` of each Document Type to its lowest to skip validation steps.
8. Create Key-Value pairs to mention the keys and values to be extracted.![](resources/8.png)![](resources/9.png)
![](resources/10.png)
9. Make sure all the changes are saved and deployed by clicking the `Apply` and `Deploy` buttons.
   
## 2. CMIS Import
   Make sure the values are entered correctly for importing documents from ACS to Ephesoft.![](resources/11.png)

| Property       | Value                                                     |
| -------------- | --------------------------------------------------------- |
| Server URL     | http://\<host-name\>/alfresco/api/cmis/versions/1.1/atom/ |
| Username       | demo                                                      |
| Password       | demo                                                      |
| Repository Id  | -default-                                                 |
| File Extension | pdf;tif                                                   |
| Folder         | site/hr-department/documentlibrary/Contracts/Drafts       |
| Property       | ephesoft:OCR-ready                                        |
| Value          | ready                                                     |
| New Value      | OCR In Progress                                           |
| CMIS Version   | 1.1                                                       |
| Enabled        | checked                                                   |

More details are available at [Ephesoft Documentation](https://ephesoft.com/docs/install-and-upgrade/4-1-0-0/cmis-import/)

## 3. CMIS Export
   Make sure the values are entered correctly here for exporting documents from Ephesoft to ACS.![](resources/12.png)
   | Property                   | Value                                                                       |
   | -------------------------- | --------------------------------------------------------------------------- |
   | Cmis Root Folder Name      | site/hr-department/documentlibrary/Contracts/GeneratedContracts             |
   | Cmis Upload File Extension | pdf                                                                         |
   | Cmis Server URL            | http://\<host-name\>/alfresco/api/-default-/public/cmis/versions/1.1/atom   |
   | Cmis Server User Name      | demo                                                                        |
   | Cmis Server User Password  | demo                                                                        |
   | Cmis Server Repository Id  | -default-                                                                   |
   | Cmis Server Switch ON/OFF  | ON                                                                          |
   | Aspect Switch              | ON                                                                          |
   | CMIS Export File Name      | ```$BATCH_IDENTIFIER & _ & $DOCUMENT_ID & _ & $DOCUMENT_TYPE & _ & $TIME``` |
   
   More details are available at [Ephesoft Documentation](https://ephesoft.com/docs/cmis-export-plugin-documentation/)

## 4. Updating Document Metadata before exporting.
A mapping document is required to update the metadata of a scan-captured document with the captured values. Ephesoft uses `aspects-mapping.properties` file as the mapping document. 

P.S: Ensure to update the correct `aspect-mapping.properties` located at your Batch Class's location eg: `C:\Ephesoft\SharedFolders\BCB\cmis-plugin-mapping\aspect-mapping.properties`

A sample `aspects-mapping.properties` file is available [here](resources/aspects-mapping.properties).

P.S: Restarting `Ephesoft Transact` service is NOT necessary to pickup these aspect configuration changes.

More information on syntax of this file is available at  [Ephesoft Documentation](https://ephesoft.com/docs/features-and-functions/administrator/moduleplugin-configuration/export-module/cmis-export-plugin-3/)

## 5. Cron job expression
For cron job expression which specify the interval at which CMIS server need to be monitored, user needs to update property `cmisImport.cronxpression` available in `Ephesoft_Home/WEB-INF/classes/META-INF/dcma-cmis-import/cmis-import.properties` file.

```
cmisImport.cronxpression=0 0/15 * ? * *
```

P.S: Even though the default value for this property is 15 mins, it is ok to set the value to 1 min.

## 6. Disabling/Enabling CMIS import functionality
For enabling/disabling CMIS import functionality user can uncomment/comment the following line in `Ephesoft_Home\applicationContext.xml`

```
<import resource=”classpath:/META-INF/applicationContext-dcma-cmis-import.xml” />
```

By default: CMIS import is disabled.

## 7. Troubleshooting

| Error message                              | Possible root cause                                                                                                                                           |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unable to connect to the server            | Invalid configuration being used for making connection to the cmis server.                                                                                    |
| Error while generating cmis properties xml | Either Ephesoft Application doesn’t have access to write the properties on the disk or Ephesoft was unable to connect to network path while writing the file. |
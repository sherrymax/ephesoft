# Ephesoft Configuration Steps

## 1. Prepare and manage batch classes
Please follow these steps for batch class management.
1. Login to [Batch Class Management](http://<host-name>:8080/dcma/BatchClassManagement.html)![](resources/1.png)
2. Credentials -  `ephesoft/demo`![](resources/3.png)
3. Successful login will route to this Batch Class Management screen. Double click the last row, which is the Batch Class created for this tutorial. ![](resources/4.png)
4. Ephesoft has to be trained on the files that are to be OCR-ed. To do this, please upload a sample of the document as shown here.![](resources/4a.png)
5. The view is updated with more details of the batch. Now the document types configured in this batch to be OCR-ed are available.![](resources/5.png)
6. Double click on a Document Type to open it.![](resources/7.png)
7. Select an Index Type related to a Document Type![](resources/7a.png)
8. Create Key-Value pairs to mention the keys and values to be extracted.![](resources/8.png)![](resources/9.png)
![](resources/10.png)
8. Make sure all the changes are saved and deployed by clicking the `Apply` and `Deploy` buttons.
## 2. CMIS Import
   Make sure the values are entered correctly for importing documents from ACS to Ephesoft.![](resources/11.png)

| Property       | Value                                                     |
| -------------- | --------------------------------------------------------- |
| Server URL     | http://\<host-name\>/alfresco/api/cmis/versions/1.1/atom/ |
| Username       | demo                                                      |
| Password       | demo                                                      |
| Repository Id  | -default-                                                 |
| File Extension | pdf;tif                                                   |
| Folder         | sites/hr-department/documentlibrary/Contracts/Drafts      |
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
   | Cmis Root Folder Name      | sites/hr-department/documentlibrary/Contracts/GeneratedContracts            |
   | Cmis Upload File Extension | demo                                                                        |
   | Cmis Server URL            | http://\<host-name\>/alfresco/api/-default-/public/cmis/versions/1.1/atom   |
   | Cmis Server User Name      | demo                                                                        |
   | Cmis Server User Password  | demo                                                                        |
   | Cmis Server Repository Id  | -default-                                                                   |
   | Cmis Server Switch ON/OFF  | ON                                                                          |
   | Aspect Switch              | ON                                                                          |
   | CMIS Export File Name      | ```$BATCH_IDENTIFIER & _ & $DOCUMENT_ID & _ & $DOCUMENT_TYPE & _ & $TIME``` |
   
   More details are available at [Ephesoft Documentation](https://ephesoft.com/docs/cmis-export-plugin-documentation/)

## 4. Updating Document Metadata before exporting

XML Schema Reference
========================


==========================      ==================================
Element                         Description
==========================      ==================================
TotalPages                      Total pages
PageSize                        Number of items on a page
CurrentPage                     The current page number
TotalResults                    The total items through all the pages
TotalResultsOnPage              The total items on the current page
--------------------------      ----------------------------------
docSeq                          Document Unique ID
docNumber                       Document Number
dateReceivedFromVendor          Date Received From Vendor
docType                         Document Type
title                           Title
revision                        Revision
version                         Aconex Internal Version
modified                        Creation Date
fileName                        Document Attachment Name
fileType                        Document Attachment Type
trackingId                      Aconex Internal Tracking Number
createdBy                       Created By
poTitle                         PO Title
poNo                            PO Number
VDIssuePurpose                  VD Issue Purpose
PMCReviewCategory               PMC/KNPC Review Category
HSSJVConsolidator               HSSJV Consolidator
dueDate                         Due Date
packageNumber                   Package No (TR No. Vendor to JV)
transmittalNoJVToVendor         TR No. JV to Vendor
CPYDelayReturn                  CPY Delay Return
CPYAnswerDueDate                CPY Answer Due Date
documentForPIM                  Document for PIM
handOver                        Hand Over
keyDocument                     Key Document
shopPhaseClose                  Shop Phase Close
nativeFileType                  Native File Type
subContractorDocumentNo         Subcontractor Doc. No
discipline                      Discipline
status                          Document Status
dateReceivedFromVendor          Date Created (Date Received from Vendor)
dateCreated                     Date Created
VDRDelay                        VDR Delay
JVReturnCode                    JV Return Code (Status)
JVAnswerDueDate                 JV Answer Due Date
JVDelayForReturn                JV Delay for Return
current                         Current
reportDate                      Reporting Date
referenceNo                     TR No. JV to Vendor
==========================      ==================================




Sample Output:

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <Response>
        <TotalPages>1</TotalPages>
        <PageSize>200</PageSize>
        <CurrentPage>1</CurrentPage>
        <TotalResults>178</TotalResults>
        <TotalResultsOnPage>178</TotalResultsOnPage>
        <List>
            <DocDetail>
                <docSeq>940126422304322391</docSeq>
                <docNumber>V-P4045ZOR-PO-CS-CM-711-000-MA-H005-001</docNumber>
                <docType>Procedure</docType>
                <title><![CDATA[Manufacturing Procedure Specification]]></title>
                <revision>B</revision>
                <version>19</version>
                <modified>2016-10-25</modified>
                <fileName>V-P4045ZOR-PO-CS-CM-711-000-MA-H005-001_B.pdf</fileName>
                <fileType>pdf</fileType>
                <trackingId>940126422226957342</trackingId>
                <createdBy>SUMITOMO</createdBy>
                <poTitle>Sheet Pile for quay wall</poTitle>
                <poNo>P4045ZOR-PO-CS-CM-711</poNo>
                <VDIssuePurpose>Issued for Approval</VDIssuePurpose>
                <PMCReviewCategory />
                <HSSJVConsolidator>Hwan-Wook Ji</HSSJVConsolidator>
                <dueDate>2016-10-25</dueDate>
                <packageNumber>SCKR-TRANSMIT-000020</packageNumber>
                <transmittalNoJVToVendor>HSSJ-SCKR-EPC45-T-0013</transmittalNoJVToVendor>
                <CPYDelayReturn>0</CPYDelayReturn>
                <CPYAnswerDueDate>2016-11-08</CPYAnswerDueDate>
                <documentForPIM>Documents for Pre-Inspection Meeting</documentForPIM>
                <handOver>Yes</handOver>
                <keyDocument>Key Document</keyDocument>
                <shopPhaseClose>No</shopPhaseClose>
                <nativeFileType>PDF</nativeFileType>
                <subContractorDocumentNo>3668-MPS-01</subContractorDocumentNo>
                <discipline>Material</discipline>
                <status>Issued for Review</status>
                <dateReceivedFromVendor>2016-10-11</dateReceivedFromVendor>
                <dateCreated>2016-10-11</dateCreated>
                <VDRDelay>0</VDRDelay>
                <JVReturnCode>Approved</JVReturnCode>
                <JVAnswerDueDate>2016-11-01</JVAnswerDueDate>
                <JVDelayForReturn>0</JVDelayForReturn>
                <current>Yes</current>
                <reportDate>2016-10-10</reportDate>
                <referenceNo>HSSJ-SCKR-EPC45-T-0013</referenceNo>
            </DocDetail>
        </List>
    </Response>